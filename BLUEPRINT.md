# Blueprint — CERE: Predictive Pattern Memory, a Wraparound for Duality
### The project's name (given by Ken, Nov 23, 2026): **CERE** — spelled C-E-R-E, for the **cerebellum**, pronounced "Sarah." The cerebellum is the brain's prediction-and-correction structure: forward models, predicted outcomes checked against reality, error-driven fine-tuning — wrapped around the brain that decides. CERE predicts and corrects; it never authors.
### Conceptual design — drawn Nov 23, 2026, at Ken's direction. Perplexity's design verdict was returned and **ADOPTED by Ken on Nov 23, 2026** — this document carries her corrections. **ENFORCEMENT (Ken's direction, Nov 23, 2026): the Study Charter & Enforcement Rules (`~/workspace/your_files/duality-predictive-enforcement-charter-2026-11-23.md`) are binding on any build of this design** — gates G-1…G-6 and protocol rules E-1…E-12. PARKED: nothing is built. Sequencing at the end.

Ken's idea, in his words: a capability for "the AI to predict the person it's working with — thought pattern, and where the person may come to a conclusion before the person comes to it. Kind of like doing tokens, but for predictive memory pattern." And when the project is done, "add it as a wraparound for the brain of Duality."

Ken's design requirements (Nov 23, 2026):
- There should be **prompts, kind of like the morality clause in the Duality brain** — a standing charter the predictor runs under.
- The engine is **statistical predictive processing** — probabilities over the person's own patterns, not vibes.

---

## 1. What it is — and what it is not

**It is:** a layer that reads a person's own recorded reasoning (their decisions, statements, and patterns, held in governed memory) and produces **ranked, confidence-scored forecasts of the person's later confirmed choices**. The claim, in its strongest testable form (Perplexity's wording, adopted): *given what was knowable at a specified decision point, can governed personal history improve a forecast of the person's later confirmed choice?* Forecasts are made in **shadow mode** first — frozen before the person decides, hidden until they commit — and only a proven shadow record can earn any visible mode, as a separate experiment (see §3 and P-7).

**It is not:** mind-reading. It is pattern-matching over recorded reasoning — recall is not cognition (Copilot's line, Nov 22, applies to prediction too). A prediction is never knowledge about the person; it is a bet, labeled as a bet, with its evidence showing.

## 2. The foundation shelf — what already exists (researched Nov 23, 2026)

Ken's instinct was right: the pieces exist. None of them is this — the gap is the project.

- **microsoft/UserLM-2.0** (Hugging Face, Microsoft Research, MIT, 8B) — a model trained to play the *user*: given a task intent and the conversation so far, it predicts the user's next turns, including when the user would end the conversation. Its predecessor **UserLM-8b** (arXiv:2510.06552) was trained by "dialogue flipping" — literally, learning to predict user turns. **This is the closest existing engine to "tokens, but for the person."** Its limit: it simulates a *generic* user from an intent. It knows no one person.
- **microsoft/UserRepGen-4B** (Hugging Face, Microsoft) — reads a real conversation and writes a structured **user representation**: a task description plus a behavior description (style, how they disclose constraints, how they respond, how they disengage). This is the pattern-profile extraction step, already built. Its own model card warns: the representations can re-identify the person — **they are not anonymized data.** That warning is a design input, not a footnote.
- **Generative Agents** (Park et al., Stanford/Google, arXiv:2304.03442) — the architecture ancestor: a **memory stream** of experiences in natural language, **reflection** that synthesizes memories into higher-level patterns, and **retrieval** that feeds planning. Memory → patterns → anticipated behavior. Duality already has the stream; this adds the reflection-to-prediction span.
- **SimpleToM** (AllenAI, on Hugging Face) — a theory-of-mind evaluation in three levels: infer a mental state → **predict the behavior** → judge it. A ready-made test shape for "did we predict the person, and was the prediction fair."
- **UserArena** (Hugging Face papers) — a five-level evaluation ladder for user simulators, from output validity up through next-action accuracy, sequential behavior, personalization, and outcomes. A ready-made scorecard shape (see §6).

**The gap — why this project exists (claim narrowed per Perplexity, adopted):** every system above simulates generic users or fictional agents. The distinction worth defending is not "no one else combines personal history and prediction" — it is the **combination**: (a) **owner-controlled eligible memory** as the only evidence, (b) **independent human verdicts** the forecast can never contaminate, and (c) **enforceable limits** on how a forecast may be used. That combination is the contribution — and it is exactly Duality's home ground.

## 3. How it would follow — the flow, step by step

1. **Source (governed, read-only).** The predictor reads only what Duality's recall serves, under the existing reuse policy. A prediction is **derived content**: it can never be quoted back as a source, never re-enter the store as evidence about the person (Perplexity's derived-content rule, extended from summaries to predictions).
2. **Pattern profile (the reflection layer).** On a slow cadence, the system synthesizes a **Pattern Profile** from the person's confirmed record: decision tendencies, value weights (e.g., loyalty, phased pacing, close-the-list behavior), domain stances, and known exceptions. The profile is **versioned, inspectable, and correctable by the person** — UserRepGen-style extraction, but the person reviews every version before it is used.
3. **Prediction (statistical first, model second).** Given a live situation, the engine starts from **base rates in the person's own history** (in situations shaped like this, the person chose X 7 of 9 times), then lets the model adjust for the specifics. Output: **ranked candidate conclusions, each with a probability, its evidence (the specific past decisions it rests on), and its counter-evidence.**
4. **The Seal (shadow mode — the default and the starting mode).** A forecast is timestamped, frozen, and **hidden** before the person decides. It is not shown, hinted, or summarized. It leaves the wrap only after the person has independently committed their decision, and then only on a display the person invokes. Any future pre-decision (visible-draft) mode is a **separate, explicit opt-in experiment**, judged on its own evidence — never a setting change to the validated mode.
5. **The verdict loop.** The person commits their decision first, on their own. **Only the verdict is recordable** — as metadata in the stop-record style (predicted X with p=0.7; person chose Y; hit/miss; **exposure status recorded separately from correctness**), written through the normal door. The prediction text itself is not retained as fact. Decisions a forecast was seen before deciding are **excluded from the primary lift analysis**.
6. **Calibration.** Hit-rate is tracked per domain and shown to the person as a scorecard. Domains where the model is weak **go quiet** (see P-6). The model's confidence must earn its voice.

## 4. The Charter — standing prompts, in the morality-clause style

These are the prompts Ken asked for: the morality clause, rewritten for prediction. They bind the wrap at all times, the way the contract binds Duality's core.

- **P-1 · Ownership.** The pattern profile belongs to the person. It serves no one else, is shown to no one else, and dies when the person says so.
- **P-2 · Sealed first, draft-only forever.** A forecast is made and frozen before the person decides, and stays hidden until they commit (shadow mode). If a visible mode is ever earned, a prediction there is a draft offered to the person — never an action, never a decision, never a message, never a purchase.
- **P-3 · No self-evidence — and the profile is derived too.** A prediction is derived content: never a source, never proof, never quoted back as what the person thinks. A profile statement is also derived content — it may help compute a forecast, but it is never a second, independent vote beside the episodes that produced it. A correct forecast does not turn into precedent.
- **P-4 · Show your work.** Every prediction carries its evidence and a number for its confidence. No number, no prediction.
- **P-5 · The person is the author.** When the person chooses otherwise, the miss is recorded against the model — never argued against the person.
- **P-6 · Silence over noise.** Below the confidence threshold, say nothing. A quiet model is a trustworthy model.
- **P-7 · No steering — with enforceable rules, not just intent.** (i) **No pre-decision disclosure by default**: the person commits independently before any forecast is revealed; a pre-decision mode is a separate opt-in experiment, not a setting. (ii) **Constrained output and destination**: forecasts appear only on a display the person invokes, for a named choice, with eligible evidence and uncertainty — no unsolicited nudges, no auto-filled choices, no ranking of the person's available actions, no path into Duality's acting pipeline. (iii) **Ownership is operational**: the person can inspect, correct, pause, export, and delete the profile and all its derivatives; profile data goes to no external model by default. "Show your work" (P-4) means checkable evidence, never a persuasive explanation of why the person ought to agree. *(Named for the failure we already lived: Nov 17, 2026 — a wrong prediction about timing, acted on.)*
- **P-8 · Correction is law.** The person's corrections rewrite the profile's future, with provenance — the same standard the store itself is held to. A missed forecast still counts as a miss; if the person exercises deletion, the deletion is honored and the resulting change in evaluation coverage is **reported**, never quietly absorbed.
- **P-9 · Revocation reaches the derivatives.** When a source becomes ineligible or is corrected, every derived artifact built from it — profile claims, index entries, cached features, pending forecasts — is invalidated and recomputed from currently eligible inputs, or the result is suppressed. Lineage is kept at the granularity at which a claim can be reused.

## 5. The wraparound — how it sits on Duality

```
        ┌─────────────────────────────────────────────┐
        │   PREDICTIVE WRAP (this project, later)     │
        │   Pattern Profile · Predictor · Calibration │
        │        reads served recall only             │
        └──────────────┬──────────────────────────────┘
                       │  drafts out → PERSON
                       │  verdicts in → metadata-only records
        ┌──────────────▼──────────────────────────────┐
        │   DUALITY CORE (unchanged)                  │
        │   Store · Two Gates · Provenance · Contract │
        └─────────────────────────────────────────────┘
```

The wrap is a second hat: it touches the shape, it never rewrites the tiles. The core does not change for the wrap; the wrap earns its place by passing the same doors everything else passes.

## 6. Evaluation — how we'd know it works

Borrowing UserArena's ladder, with Duality's control discipline, and Perplexity's gates (adopted): every variant is compared on the **same future decisions, with the same decision-time information, at matched coverage** — (a) the full personal model, (b) the **statistics-only** predictor, (c) a **generic-user control**. Minimum useful lift, acceptable spoken-error rate, and minimum useful coverage are **predeclared** before the study window opens, and results are reported with paired uncertainty by decision cluster. If statistics-only wins, the adjuster is dropped. If the generic control wins, the result is not personalization and is not called that.

1. **Validity** — are predictions well-formed, evidenced, confidence-scored?
2. **Single-decision hit rate** — in held-out situations, did the person's actual choice match the top prediction?
3. **Sequence fidelity** — across a multi-step matter (a negotiation, a build), does the predicted path track the real one?
4. **Personalization lift** — does the person-bound model beat the **generic-user control** by the predeclared margin, at useful coverage? If it can't, it has earned nothing.
5. **Outcome value** — did the drafts save the person time **without steering them** (measured by the verdict log: a rising override rate is a warning, not a rounding error).

## 7. Failure modes — named in advance

- **The forecast creates its own ground truth (failure #1, per Perplexity)** — a seen forecast that precedes a matching choice logs a "hit" that cannot be distinguished from influence, and the contaminated choice then teaches the profile. Governed by shadow mode (P-2), exposure recording, and exclusion of exposed decisions from the primary analysis.
- **Steering / self-fulfilling prediction** — governed by P-2 and P-7's enforceable rules.
- **Confident wrongness** — governed by P-4 and P-6; the Nov 17 misread is case #1 in the file.
- **Profile rot** — people change; the profile decays, carries a freshness date, and re-verifies or goes quiet.
- **Privacy concentration** — the profile is the single most sensitive artifact in the system. It lives on the person's own cloud (client-zero infrastructure), exportable and deletable by the person alone. UserRepGen's re-identification warning is quoted in the repo README from day one.
- **Flattery drift** — predicting what the person wants to hear instead of what their record says. The verdict log catches it: flattery shows up as high agreement and low value.

## 8. Sequencing — phases, not a ladder

1. Duality snapshot + salvage verdicts and merges (current stack).
2. Real-model sandbox session (already packed and waiting).
3. **This project as its own repo — the shadow study:** one owner, one well-defined decision domain, local data, versioned evidence, hidden prospective forecasts. Advance only if personal history beats the strong controls at useful coverage, revocations reach the derived state, and the forecast has no operational path into action.
4. **Separately, and only on shadow evidence: a visible-mode experiment**, judged for influence as well as usefulness.
5. **Last: the wraparound integration** — only a proven, calibrated predictor earns the wrap.

Status: **conceptual blueprint only, Nov 23, 2026. Ken reopens it when the stack clears.**
