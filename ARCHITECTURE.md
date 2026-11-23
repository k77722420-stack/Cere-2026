# Predictive Pattern Memory — Full Architecture and the Math Under It
### Companion to the conceptual blueprint (Nov 23, 2026). Design only — nothing is built. PARKED behind the current Duality stack. **Binding enforcement: the Study Charter & Enforcement Rules (`~/workspace/your_files/duality-predictive-enforcement-charter-2026-11-23.md`) govern any build of this architecture (Ken's direction, Nov 23, 2026).**

This document describes the wraparound the way it would actually be built: the components, the data flow, and the statistical machinery that produces a prediction — plus how its performance is measured honestly. Every number given as a performance figure is a **design target to be measured**, not a promise. The worked example uses round, invented counts to show the arithmetic — it is not Ken's real record.

---

## Part 1 — The architecture

### Components

1. **Served-Recall Boundary (the only door in).** The wrap never touches Duality's store directly. It consumes the same recall snapshots the core already serves (one snapshot per run, per the snapshot refactor). Read-only. If recall wouldn't serve it to the person, the wrap never sees it.
2. **Precedent Index.** Every confirmed decision episode in the record, indexed by: domain (money, people, platforms, health, build-vs-buy…), situation features (stakes, reversibility, who is affected, time pressure), the options the person faced, the choice they made, and its timestamp. Built only from **confirmed** records — never from predictions (Charter P-3).
3. **Pattern Profile Store.** A small, versioned, human-readable document (JSON + a plain-language rendering) holding, per domain: the choice distribution, the value weights the choices imply, known exceptions, and a freshness date. Every version carries provenance: which episodes it was synthesized from. The person can inspect, correct, pause, export, delete, and roll it back (P-1, P-8). As a **derived store**, it obeys P-9: when a source episode becomes ineligible or is corrected, every claim, cached feature, and pending forecast built from it is invalidated and recomputed from currently eligible inputs — or suppressed. Lineage is kept at the granularity at which a claim can be reused.
4. **Statistical Core.** The math of Part 2. Pure computation over the Precedent Index and the Profile: base rates, recency- and similarity-weighted evidence, the blend with the model's read, and the confidence threshold. No language model in this box — it is arithmetic, so it can be audited line by line.
5. **Model Adjuster.** A language model (local, Ollama-class, like the sandbox work) that reads the live situation and proposes how the specifics should move the statistical prior. It outputs a probability distribution and its reasons. It never sees the person, never writes anything, and its influence is capped by the blend weight β (Part 2), which is itself calibrated.
6. **Seal & Draft Gate (the only door out).** In shadow mode (the default), a forecast is timestamped, frozen, and **sealed** — the gate's job is that nothing leaks: no hint, summary, or nudge reaches the person before they commit. After the person commits and invokes the reveal, the gate applies the Charter mechanically: confidence below threshold → the forecast stays unshown and is graded silently (P-6). No evidence attached → suppressed (P-4). Anything that reads as pressure rather than checkable evidence → suppressed (P-7). What survives renders as: the forecast, the probability, the eligible evidence, the counter-evidence, and the strongest alternative.
7. **Verdict Recorder.** When the person commits, the verdict — predicted X at p, person chose Y, hit or miss, **exposure status** (sealed/unseen vs. seen before deciding) — is written as a **metadata-only record** in the stop-record style, through Duality's normal door. The prediction's text is not stored as fact. Metadata-only is **not** automatically anonymous: timestamps, categories, and lookup identifiers can still be revealing, so the ledger is held at the same protection class as the profile. This ledger is the system's memory of its own performance, and nothing else.
8. **Calibration Ledger / Scorecard.** Aggregates the verdicts into the published measures of Part 3, per domain. The person can ask "how good are you, lately, at money calls?" and get a number with its sample size.

### Data flow, one prediction end to end

```
situation arrives
  → recall snapshot (governed, read-only)
  → precedent retrieval: similar past episodes, weighted (Part 2, eq. 2–3)
  → statistical prior over the person's likely conclusions (eq. 1, 4)
  → model adjuster proposes a distribution from the live specifics
  → blend (eq. 5) → calibrated confidence (eq. 7)
  → Seal: forecast frozen + hidden (shadow mode)
  → person commits their decision independently
  → reveal only on the person's invocation: threshold + Charter checks (or continued silence)
  → person decides → verdict recorded (metadata only)
  → counts, calibration, and drift updated (eq. 8)
```

### Where each Charter clause is enforced

| Clause | Enforced at |
|---|---|
| P-1 Ownership | Profile Store — local, exportable, deletable; no other reader exists in the design |
| P-2 Draft-only | Draft Gate — the wrap has no write path to the outside world at all |
| P-3 No self-evidence | Precedent Index — predictions are structurally ineligible as episodes |
| P-4 Show your work | Draft Gate — a draft without evidence and a number cannot render |
| P-5 Person is author | Verdict Recorder — misses score against the model, always |
| P-6 Silence over noise | Statistical Core — the threshold τ (eq. 6), set from measured calibration |
| P-7 No steering | Draft Gate — drafts present the fork (top prediction + strongest alternative + counter-evidence), never a push |
| P-8 Correction is law | Profile Store — corrections are versioned inputs with provenance, applied before any new prediction |

---

## Part 2 — The math

**Setup.** For a domain *d*, let the person's possible conclusions be c₁…c_K. The record holds episodes i = 1…N in that domain; episode i has choice y_i, age Δt_i (days since it happened), and — for a live situation — a similarity s_i ∈ [0,1] to the current situation.

**Eq. 1 — Smoothed base rate (the prior).** Raw counts lie when data is thin, so counts are smoothed (Laplace / add-α):

> P₀(c) = (n_c + α) / (N + αK), with α = 1.

A choice never made still gets a small probability instead of zero — the person is allowed to surprise the model.

**Eq. 2 — Recency weighting.** People change, so old episodes count less. Each episode's weight decays with its age, in true half-life form *(formula corrected on adoption of Perplexity's verdict, Nov 23, 2026 — the first draft wrote an e-folding curve while calling the constant a half-life; her arithmetic was right, the label was wrong)*:

> w_i = 2^(−Δt_i / H), with half-life H. Default hypothesis: H = 90 days — an episode 180 days old carries one-quarter the weight of a fresh one, before similarity is applied.

H is a **hypothesis, not a constant of nature**: it is tested against a small predeclared set (no decay; H = 30; H = 90; H = 180) on the calibration window, and the winner is frozen for the test window. Weighted counts ñ_c = Σ_{i: y_i=c} w_i replace raw counts in Eq. 1. Episodes are **clustered by decision**: several records from one decision never count as independent evidence.

**Eq. 3 — Similarity weighting.** For a live prediction, precedents also weigh by how much they resemble the current situation:

> n̂_c = Σ_{i: y_i=c} w_i · s_i, and the effective sample size is N_eff = Σ_i w_i · s_i.

N_eff is reported with every prediction. A prediction resting on N_eff = 2.3 is a whisper, whatever its probability says — the Draft Gate can require a minimum N_eff as well as a minimum probability.

**Eq. 4 — The statistical prediction.** P_stat(c) is Eq. 1 computed from the weighted counts n̂_c. This is the "statistical predictive processing" Ken specified: the person's own history, speaking first, in numbers.

**Eq. 5 — The blend.** The model adjuster contributes P_model(c). The final distribution is a geometric blend:

> P(c) ∝ P_stat(c)^(1−β) · P_model(c)^β, normalized to sum to 1.

β ∈ [0,1] is **not** a taste setting — but the fallback is a rule, not a hope (Perplexity's correction, adopted): **β = 0 is the default**, because with sparse verdicts a fitted nonzero β can be noise, and the two components rest on the same episodes, so their agreement is not independent corroboration. β may rise above 0 only when a fit on the training window (by log-loss or Brier; probabilities floored before logs; both distributions on the same outcome set — including "defer / none of these" where meaningful) beats β = 0 by a predeclared margin on the calibration window — and the geometric pool must also beat an **arithmetic blend** before it is declared necessary. When the gain is uncertain, the simpler model wins. The machine has to earn its influence, in public, with numbers.

**Eq. 6 — The speak/silence threshold.** The wrap speaks only when max_c P(c) ≥ τ_d, per domain. τ_d is set from the calibration curve (Eq. 7): the lowest stated-confidence level at which the domain's measured accuracy reaches the charter bar (design bar: 0.80). Accuracy and **coverage** (the fraction of situations spoken on) are always reported together — a model that speaks rarely and is usually right is the design goal; a model that speaks constantly is a nuisance with a chart.

**Eq. 7 — Calibration.** Predictions are binned by stated confidence (0.5–0.6, 0.6–0.7, …). In each bin, measured accuracy should match stated confidence. The gap is the Expected Calibration Error:

> ECE = Σ_bins (n_b / N) · |accuracy_b − confidence_b|.

Design target: ECE ≤ 0.05 per active domain. A model that says 0.8 and is right half the time is not "sometimes wrong" — it is miscalibrated, and its τ rises until it tells the truth or goes quiet.

**Eq. 8 — Scoring and the verdict update.** Every graded prediction is scored with the Brier score:

> BS = Σ_c (P(c) − o_c)², where o_c = 1 for the person's actual choice, else 0.

BS = 0 is perfect; an always-hedging forecaster scores poorly and visibly. Each verdict also updates the domain's counts (the person's actual choice enters the Precedent Index as a new confirmed episode — their decisions are data; the model's guesses are not), and repeated misses in a domain raise its entropy, which raises its effective τ. **Failure makes the system quieter, automatically.**

**Evaluation protocol (adopted from Perplexity's verdict).** Time is the wall: fit the predictor and blend on **earlier** decisions, choose calibration and the speaking threshold on **later** decisions, and evaluate the **frozen** policy on a **still-later** test window. At each forecast, the index, profile, and served recall are reconstructed **as they existed at that decision point** — no future information leaks backward. Report Brier score and log loss across **all** scored cases first; then error among spoken forecasts at their coverage, with counts and uncertainty. The threshold is an operating choice, not a guarantee under drift — and if the evidence is too thin to support a useful risk–coverage point, the correct result is silence.

**Sequences.** For multi-step matters, transition counts T(a→b) over the person's decision sequences get the same smoothing and decay; a rollout (model-simulated, UserLM-style) is scored by the fraction of its steps the statistical core endorses. Sequence predictions carry lower confidence by construction — errors compound, and the math says so out loud.

### A worked illustration (invented round numbers — not Ken's record)

Domain: *platform problems*. Record: 9 episodes — closed the list 6 times, fixed it himself 2, escalated to support 1. α=1, K=3:
P₀(close) = (6+1)/(9+3) = **0.58**; P₀(fix) = 3/12 = **0.25**; P₀(escalate) = 2/12 = **0.17**.
A new platform problem arrives, resembling the "close" episodes most (similarity lifts their weight), and the model adjuster reads the specifics and leans close as well. Blend at β=0.3 → P(close) ≈ **0.71**. If τ for this domain is 0.65, the wrap speaks: *"Likely call: close it (about 7 in 10). Evidence: 6 of your last 9 like this. Strongest alternative: fix it yourself — you did that when the fix was one setting."* The person decides. The verdict — not the draft — goes in the ledger.

---

## Part 3 — Performance: what "working" means, in numbers

Measured on **held-out** episodes (the system is graded only on decisions it did not train on), reported per domain, always with sample sizes:

| Measure | What it proves | Design target |
|---|---|---|
| Top-1 hit rate (spoken predictions only) | When it speaks, is it right? | ≥ 0.80 in narrow, habitual domains; no target promised for open domains — measured, then published |
| Coverage | How often it speaks at all | Whatever accuracy buys; expected low at first (silence is the default) |
| ECE | Does its confidence mean what it says? | ≤ 0.05 per active domain |
| Brier score vs. base-rate-only | Does the model adjuster add anything over raw statistics? | Must beat the statistics-only score, or β → 0 |
| **Personalization lift (three-way gate)** | Does knowing *this* person beat both the statistics-only predictor and a generic-user control, on the same decisions, same information, matched coverage? | Must beat both by the **predeclared** margin, with paired uncertainty by decision cluster — or the wrap has earned nothing |
| Override rate trend | Is the person pushing back more over time? | Rising overrides = steering or rot alarm; triggers profile re-verification |

**Honest expectations.** People are habitual in narrow domains (tools, vendors, routines), so base rates alone will carry real weight there — that is the system working as designed, not a trick. Open-ended conclusions (new territory, values calls, anything the person is still forming) will predict far worse, and the threshold exists to keep the wrap silent there. The claim, stated the Duality way: *a governed predictor that knows its own score, speaks only where its record is strong, and treats every miss as evidence against itself.* Anything stronger would be inflation.

**Cost shape.** The profile is kilobytes. A prediction is one recall snapshot + arithmetic + one local model call — the same weight class as a Duality run. It fits the stack Ken already runs (his own cloud, local models), which matters: the most sensitive artifact in the system never has to leave the person's own machine.

---

## Sequencing (unchanged from the blueprint)

Snapshot + salvage verdicts → merges → real-model sandbox session → this project as its own repo (profile extraction first, predictor second, calibration always) → the wraparound integration last. **Status: architecture description only, Nov 23, 2026.**
