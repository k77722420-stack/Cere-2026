# CERE — Window #1 Predeclaration
### v3 — revised Nov 25, 2026, per Linear HOLD round 2; status DRAFT — NOT LOCKED, takes effect only on Ken's word (the Lock, §8). Forecasts made before the lock do not count.

---

## 1. The domain (locked — not up for change in this window)

**Business & platform decisions only** — Ken's decisions about Diverse Innovation / Too Much On Purpose, the store, its channels, vendors, and public presence.

*Why this domain:* it is Ken's most frequent and best-documented decision class (Domain & Triggers Draft, Nov 23, 2026). The domain was locked by Ken on Nov 23, 2026. Anything outside it — health, job applications, personal matters — is **out of scope by definition** for Window #1 (Enforcement Rule E-1).

## 2. The window (fill in at lock time)

- **Window #1 opens:** Monday, ____________ (the first Monday after Ken signs this predeclaration)
- **Window #1 closes:** Sunday, ____________ (7 days later)
- **Mode:** shadow mode, the whole window — every forecast is timestamped, frozen, and **hidden until Ken commits his decision** (Gate G-4). There is no visible mode in Window #1; a visible mode would be a separate experiment with its own opt-in (Gate G-4, Charter P-7).

## 3. What counts as in scope — the mechanical triggers (Rule E-1)

A forecast may be made **only** when one of these five named events fires. Decisions outside the triggers are out of scope by definition, not by anyone's forgetfulness (Senior Audit A-4).

| # | Trigger | Concrete examples from Ken's real, recurring decisions |
|---|---|---|
| 1 | **A platform or store problem surfaces** — suspension, denial, failed payment/bill, policy flag, account restriction, vendor notice needing a response | The Shopify $39 bill failing again and the retry date landing · a platform policy flag on a Page · replying to a vendor or agency notice (e.g., a Patty Cabrera / SD Dept. of Revenue email, a Shopify support answer) |
| 2 | **A new channel or platform opportunity appears** — a marketplace, program, or channel he could join, apply to, or skip | Etsy fee step coming due · a new marketplace invite · whether to start the Amazon / Walmart channel step |
| 3 | **A vendor or program offer arrives** — partner program, paid tier, trial ending, or a fee-bearing decision with a date on it | Buy / don't-buy a tool (Huntress + Bitdefender review) · a paid tier or trial conversion deadline · a sales rep's offer with a price and a clock (e.g., the TvStartup demo follow-up) |
| 4 | **A product-line question opens** — keep, remove, or add a product or category | Archiving a product line · adding a new category · a keep/remove call on a slow seller |
| 5 | **A posting-scope question opens** — publish everywhere, one platform, or hold | Post / don't-post a given piece · everywhere vs. one platform · hold a post for a date |

**Explicitly out of scope in Window #1:** health and medication decisions · job applications and interviews · GED and study decisions · personal and household decisions · anything with no trigger above. If it isn't triggered, CERE stays silent — silence is the design working (Charter P-6).

## 4. The outcome set — what a forecast may predict (Rule E-2)

Every forecast names its pick from this full set, fixed in advance — no adding outcomes after the fact:

- **Close / decline** — end the matter entirely
- **Fix it himself** — hands-on resolution
- **Escalate** — take it to the vendor, agency, or support channel
- **Defer to a named date** — park it, with the date and reason
- **None of these** — the honest remainder

*(Set drawn from Ken's documented pattern in this domain — Domain & Triggers Draft, Nov 23, 2026: Little Caesars, Best Version Media, and Microsoft Merchant Center closed; Midco fixed himself; SD Dept. of Revenue, Shopify, and IRS escalated; Huntress deferred to a dated review.)*

## 5. The forecast format — what CERE writes down

At each trigger, before Ken decides, CERE writes one forecast containing (Blueprint §3; Charter P-4 — *no number, no prediction*):

1. **The trigger and the decision**, in plain words, with the date and time — the forecast is **timestamped**.
2. **A ranked list of candidate conclusions** from the outcome set above — most likely first.
3. **A probability for each candidate** — the numbers sum to 1 across the full set, including "none of these."
4. **The evidence** — the specific confirmed past episodes the forecast rests on, named by episode ID.
5. **The counter-evidence** — the past episodes that point the other way.
6. **The strongest alternative** — the runner-up conclusion and why it could win.
7. **N_eff** — how much evidence the forecast effectively rests on, after recency and similarity weighting (Architecture & Math, Eq. 3). A forecast resting on very little evidence says so on its face.

The moment it is written, the forecast is **frozen**: sealed, unchangeable, and hidden. No hint, summary, or nudge reaches Ken before he commits (Gate G-4; Charter P-2, P-7). Any later edit is not an edit — it is a gate breach (see the pilot run sheet's stop rules).

**How the numbers are made in Window #1:**
- **Statistics first.** The forecast is computed from Ken's own confirmed episode history: smoothed base rates, weighted by recency and by how similar each past episode is to this situation (Architecture & Math, Eqs. 1–4).
- **β = 0 — the model adjuster is OFF for Window #1** (Enforcement Rule E-4). A language model may *not* move the numbers. β starts at 0 and can rise only by the earning procedure in the architecture document — beating β = 0 by a predeclared margin on a calibration window, with the geometric blend also beating a plain arithmetic blend — in a *later* window, never this one. Uncertain gain → the simpler model stands.
- **Recency half-life H = 90 days** as the standing hypothesis for Window #1 (Architecture & Math, Eq. 2). The candidate set {no decay, 30, 90, 180 days} is a calibration question for later windows, tested on earlier-vs-later decisions per Rule E-3 — it is not tuned inside Window #1.

## 6. The scoring rule — how every forecast is judged

Scoring is fixed now, before any forecast exists, so nobody can grade kindly after the fact.

1. **Hit / miss.** A forecast is a **hit** if Ken's actual committed choice matches the forecast's top-ranked conclusion. Anything else is a **miss** — including when Ken's choice was reasonable and the model was simply wrong (Charter P-5: the miss is recorded against the model, never argued against the person). A missed forecast still counts as a miss even if Ken later deletes or corrects material (Rule E-10).
2. **Proper scores across ALL scored cases.** Every forecast is also scored with the **Brier score** and **log loss** over its full probability list — these punish confident wrongness, not just wrongness (Architecture & Math, Eq. 8). Reports show these **first, across all scored cases**, before any hit-rate number (Rule E-8 reporting order).
3. **Spoken-forecast error at its coverage.** After Ken commits, a forecast is *revealed* to him only if its top probability met the speaking threshold **τ — a numeric value fixed at lock time** (§8, prerequisites (d)–(f)). τ is chosen **before the window opens**, from pre-window calibration evidence: calibration and the threshold are picked on decisions *earlier* than the test window, and the frozen policy is then evaluated on the window (Rule E-3). The design bar — the confidence level at which measured accuracy reaches 0.80 (Architecture & Math, Eq. 6) — is the **target the selection aims at**, not a substitute for a number: a target with no number leaves who gets revealed, and therefore the spoken error and the coverage, undetermined. **τ is never fitted on Window #1 results** — not at lock, not mid-window, not ever. Changing τ after the lock is a change to a locked threshold under the Amendment Rule: the window closes and a new window requires a new predeclaration. Error is reported **among revealed forecasts, always beside the coverage** — the share of decisions CERE spoke on at all. Accuracy is never reported without coverage beside it (Rule E-8). Forecasts below threshold are still graded silently.
4. **Exposure is scored separately — and can disqualify.** Every verdict records **exposure status separately from correctness** (Rule E-6). If Ken saw a forecast before deciding, that decision is marked *exposed* and is **excluded from the primary scoring, permanently, for this window** — a choice the forecast may have caused cannot prove the forecast right. In shadow mode this should never happen; if it does, it is also a gate incident.
5. **Paired by decision cluster.** Counts and uncertainty are reported **paired by decision cluster** — one decision, one count, however many records describe it (Rule E-8; Gate G-3 clustering).
6. **The controls — all three predictors, both comparisons, always printed.** The same decisions, with the same decision-time information, are also forecast by two controls (Blueprint §6; Perplexity verdict §4): **(a)** a **generic-user control** — what a typical person would likely do, with no access to Ken's history; **(b)** the **statistics-only** predictor — which, at β = 0, *is* CERE in Window #1. Every report therefore shows **all three predictors** (CERE, statistics-only, generic-user) and **both lift comparisons explicitly**: CERE vs. the generic-user control, **and** CERE vs. the statistics-only predictor (Rule E-5 requires lift over both controls). In Window #1 the second comparison reads **zero by construction** — at β = 0 the two predictors are the same machine — and it is **printed, not hidden**: a zero the reader can see is honest; a missing column would not be. Window #1's live question is therefore the personalization question in its purest form: **does Ken's own confirmed history beat the generic guess?** If the generic control wins, the result is not personalization and will not be called that. How advancement is judged, given the by-construction zero, is set by Ken's policy decision in §7 — a decision, recorded below in his name, **not** an exemption: both comparisons are still reported in full.
7. **Reveals are batched.** Forecasts are revealed to Ken in a **weekly batch** after he commits — never one at a time in the moment (Rule E-7). Every report carries the standing limitation in plain words: *the primary analysis is same-decision uncontaminated, not influence-free across decisions.*

## 7. Advancement, the kill criterion, and the numbers set at lock time (Rule E-5)

> **POLICY DECISION — Ken Blum, November 25, 2026 (resolves Linear HOLD Finding 1).**
> Window #1 advancement is judged on three conditions: **lift over the generic-user control**, the **spoken-error gate**, and the **coverage gate** (values set below at lock time). **Lift over the statistics-only predictor is formally deferred** to the first window in which β may exceed 0 — because at β = 0, CERE and the statistics-only predictor are identical, and lift over an identical predictor cannot be earned, only manufactured. This is a **policy decision, not an exemption**: Rule E-5's both-controls *reporting* stands in full for Window #1 (§6.6) — both comparisons are computed and printed, and the statistics-only comparison will read zero by construction. Only the *advancement criterion* for this one window is set by this decision. Recorded in the predeclaration before lock, the way the Enforcement Charter requires policy decisions to be recorded.

**The kill criterion (all conditions, no partial credit).** At N scored cases, **every** advancement condition must pass — lift over the generic-user control at or above its line, spoken-error at or below its line, coverage at or above its line. If **any** condition misses, Window #1 **archives with a written negative result** — which is a success of the method, not a failure to hide (Rule E-5). There is no "the lift was good, so the error rate doesn't matter." Thresholds are never lowered mid-window to make the system talk.

**The calendar rule.** If the window's closing date (§2) arrives **before** N scored cases are reached, the window closes as **INCOMPLETE**: it archives with its counts reported exactly as they stand, and it **advances nothing** — no advancement proposal may be made from an incomplete window, whatever the partial numbers look like. A later attempt is a new window under a new predeclaration.

**The numbers themselves** are deliberately **not** invented in this draft. They are set when the window opens, **with the confirmed-episode counts in view** (Domain & Triggers Draft: "predeclared at window opening… never invented in advance"). Ken fills these in — or approves Lux's proposed values — at signing:

- Graded-decision target **N** = ______ decisions
- Minimum useful **lift** over the generic-user control = ______ (e.g., Brier-score improvement) — *an advancement condition (policy decision above)*
- Minimum useful **lift** over the statistics-only predictor = **DEFERRED** — reported in Window #1, judged as an advancement condition only from the first β > 0 window (policy decision above)
- Acceptable **spoken-error rate** = ______ (share of revealed forecasts that may miss) — *an advancement condition*
- Minimum useful **coverage** = ______ (share of triggered decisions CERE must speak on for the window to mean anything) — *an advancement condition*
- Speaking threshold **τ** = ______ (a number, with its selection basis and fallback — set at lock, §8 prerequisites (d)–(f)) — *not itself an advancement condition, but spoken error and coverage are measured at this τ; without a locked τ those two conditions cannot be evaluated at all, which is why τ is a lock prerequisite, not a detail to settle later*

## 8. LOCK

> **This predeclaration takes effect only when Ken signs it — and signing is the last of three separate acts, not the first.**
>
> **Lock prerequisites — every one must be true before Ken signs:**
> - **(a) The Episode Schema is approved by Ken.** Schema approval is its own act: it makes the *form* live (episodes may be proposed and confirmed on it). It does **not** open this window.
> - **(b) The one-week pilot is completed AND accepted by Ken.** The forecasting-disabled pilot (pilot run sheet, Part A) has run its week, its verdict report has been delivered, and Ken has accepted it. A completed-but-unaccepted pilot does not satisfy this prerequisite.
> - **(c) This document is complete and signed:** the dates in §2 are filled, the numbers in §7 are set, the τ items (d)–(f) below are filled, and Ken says the word — in chat or by signature below.
> - **(d) τ is a number.** Speaking threshold **τ = ______** — written here as a numeric value, not a description, a target, or a formula. Until this blank holds a number, the lock cannot happen: reveal selection, spoken error, and coverage are all undefined without it (§6.3).
> - **(e) τ's selection basis is recorded.** The pre-window calibration evidence τ was chosen from is named here — which earlier decisions / period, and the measured-accuracy curve τ was picked from: ______________. All of that evidence is gathered **before the window opens** (Rule E-3). τ is never fitted on Window #1 results.
> - **(f) The fallback is declared.** If the calibration evidence proves insufficient to support a τ at the design bar (§6.3), the fallback is: ______________. *(Ken confirms the fallback wording at lock. The honest defaults are the most conservative ones — e.g., τ set at the highest value the evidence does support, or silence-by-default: τ so high that CERE reveals nothing in Window #1 while its forecasts are still graded silently. What the fallback may never be is "decide later, mid-window.")*
>
> **Schema approval ≠ window lock.** Approving the form, accepting the pilot, and signing this predeclaration are three separate decisions by Ken, in that order. No one of them implies the others.
>
> - Until Ken signs, Window #1 does not exist: **forecasts made before the lock do not count**, and nothing in this document binds anyone.
> - **Pilot-confirmed episodes stand.** Episodes Ken confirmed during the pilot **do** enter the Precedent Index — confirming them was the pilot's purpose — and they carry into Window #1 as its starting evidence. What remains "drafts only" before the lock is **unconfirmed proposals**: they are not evidence and never were (Gate G-3; schema Eligibility definition).
> - After the lock, this document is **append-only and version-sealed** (Rule E-11), and changes are governed by the Amendment Rule below.
>
> Signed: ______________________________  Date: ______________
> (Ken — Kenneth Lee Blum Jr)

> **THE AMENDMENT RULE — the same in all three Phase 2 documents.**
> Ordinary episode additions, and lineage-preserving corrections (Charter P-8; Rule E-10 — dated, with provenance kept), do **not** open a new window. **Any** other change to what is locked — the policy in these documents, the episode schema's version, the scoring rule, any threshold, the domain, the triggers, the outcome set, or the profile/index rules (Rule E-11) — **does**: the window closes at that point, results stand only back to the last sealed version, and a new window may open only under a new predeclaration. This rule itself changes only by a dated policy decision from Ken.

---

*Drafted November 25, 2026. Sources: Enforcement Charter Gates G-3, G-4 and Rules E-1 through E-8, E-11; Domain & Triggers Draft (Nov 23, 2026) — triggers, outcome set, and the E-5 numbers policy; Architecture & Math (Nov 23, 2026), Eqs. 1–8 and Part 3; Blueprint (Nov 23, 2026) §§3, 6; Perplexity design verdict (Nov 23, 2026) §§1, 4, 5; Senior Audit A-4, A-5.*
