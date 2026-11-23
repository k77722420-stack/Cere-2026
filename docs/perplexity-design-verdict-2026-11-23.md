# Perplexity — Design Verdict on Predictive Pattern Memory
### Returned Nov 23, 2026, in response to the design-review packet Ken carried to her. Verbatim below. Design verdict only — separate from her snapshot and salvage reviews. **ADOPTED by Ken Nov 23, 2026** — the blueprint and architecture/math documents were amended the same day to carry her corrections, and a senior-level audit of the adopted design followed (`~/workspace/your_files/duality-predictive-audit-2026-11-23.md`).

---

For Ken and Lux — design verdict

I support building this as a standalone, private shadow-mode study: make predictions before Ken decides, hide them until he records his decision, and measure whether they add anything. I would not start with visible drafts or integrate it into Duality yet. This is a design verdict, separate from the snapshot and salvage reviews.

The strongest version of the claim is also the most testable: "Given what was knowable at a specified decision point, can governed personal history improve a forecast of the person's later confirmed choice?" That is narrower than predicting a thought process. It leaves room for the person to change their mind and gives the project a result it can honestly prove or fail to prove.

1. The math is sound as a starting model, not as a calibration guarantee

Smoothed base rates first, then recency and similarity, is a sensible order. Start with an explicit set of outcomes, including "defer" or "none of these" where meaningful. Treat the 90-day half-life as a hypothesis: an episode 180 days old gets one-quarter the recency weight of a fresh one before similarity is applied. Compare that default to no decay and a small, predeclared set of alternatives. Track how many distinct decisions support a forecast; several episodes from one decision should not count as independent evidence.

The geometric blend is a valid logarithmic pool. Put both distributions on the same outcome set, smooth or floor probabilities before taking logs, and normalize the result:

The important correction: β=0 should be the fallback rule, not something you expect the optimizer to discover reliably. With sparse verdicts, a fitted nonzero weight can be noise. Both components may also depend on the same episodes, so agreement is not independent corroboration. Fit with a proper probability score such as log loss or Brier, favor the simpler model when the gain is uncertain, and compare against an arithmetic blend before declaring the geometric one necessary. Research on learning logarithmic-pool weights supports fitting them from data but also notes that they can be hard to identify.

Fit the predictor and blend on earlier decisions, choose the calibration and speaking threshold on later decisions, and evaluate the frozen policy on a still-later test window. Group related episodes by decision and reconstruct the index, profile, and served recall as they existed at prediction time. Report Brier and log loss across all scored cases, then report error among spoken forecasts at their coverage, with counts and uncertainty. A calibration-set threshold is an operating choice, not a guarantee under drift. If the evidence is too thin to support a useful risk–coverage point, the right result is silence.

2. The derived-content rule holds, and it needs to cover the profile too

A prediction is never evidence that the person thinks or acts that way. A profile statement is also derived content: it can help compute a forecast, but it is not a second, independent vote alongside the episodes that produced it. Use confirmed, eligible human decisions as evidence; use forecasts and verdicts to evaluate the predictor. A correct forecast does not turn into precedent.

Read-only access to served recall is necessary but not sufficient once the wrap keeps an index, a profile, or cached features. Those are new stores of derived information. When a source becomes ineligible or the owner corrects it, invalidate affected profile claims, cached features, and pending drafts; recompute from currently eligible inputs or suppress the result. Keep lineage at the granularity at which a profile claim can be reused. Otherwise the wrap can preserve a pattern that Duality's recall layer has stopped serving.

One distinction for "correction is law": the owner controls what the profile may assert or reuse. An ordinary missed forecast must still count as a miss. If an owner exercises deletion rights, honor the deletion and report the resulting change in evaluation coverage rather than quietly rewriting the score.

3. P-7 needs an enforceable boundary: draft-only is not non-steering

A draft that says "you'll probably choose A" can anchor a choice without taking any external action. A confidence number and a selective evidence list can strengthen that effect. A morality prompt belongs in the design, but it cannot enforce a rule about when someone sees something or where an output can go.

I would give P-7 three concrete rules:

No pre-decision disclosure by default. The person commits their decision independently before seeing the forecast. Any future pre-decision mode is a separate, explicit opt-in experiment, not a setting change to the validated mode.

Constrain the output and its destination. Use a user-invoked display for a forecast about a named choice, with eligible evidence and uncertainty. No unsolicited nudges, auto-filled choices, tool calls, ranking of available actions, or injection into Duality's acting pipeline. "Show your work" should mean showing checkable evidence, not generating a persuasive explanation of why the person ought to agree.

Make ownership operational. The person can inspect, correct, pause, export, and delete the profile and its derivatives. Don't send profile data to an external model by default. Microsoft's UserRepGen model card explicitly warns that behavior representations can make conversations easier to link to the same person. Metadata-only verdicts are not automatically anonymous either; timestamps, categories, and lookup identifiers can still be revealing.

4. Generic-user lift is necessary, but it is not the only gate

Compare every variant on the same future decisions, with the same decision-time information and at matched coverage where abstention is involved. I would use three comparisons:

Predeclare a minimum useful lift, an acceptable error rate among spoken forecasts, and minimum useful coverage. Report paired uncertainty by decision or decision cluster. A system that beats generic only on a handful of easy cases has not earned the right to speak broadly. If the statistical predictor wins and the adjuster doesn't, keep the statistical predictor. If the context-matched generic control wins, don't call the result personalization.

I'd also narrow the novelty claim. UserLM-2.0 is described as a conversation simulator. The distinction worth defending here is the combination of owner-controlled eligible memory, independent human verdicts, and enforceable limits on how a forecast can be used—not a claim that no other research combines personal history and prediction.

5. The failure I'd put first: the forecast creates its own ground truth

Suppose the wrap predicts A, Ken sees it, and then chooses A. The log shows a hit, but it cannot distinguish "the system foresaw the choice" from "the system helped cause the choice." If that choice then enters precedent without recording the exposure, the next profile can learn from behavior the system helped produce. Apparent accuracy can improve while independent predictive value disappears. "No self-evidence" does not catch this on its own, because the contaminated evidence is now a real human choice.

The first acceptance study should therefore timestamp and freeze each forecast before the decision, keep its contents hidden until the owner commits, and record exposure status separately from correctness. Keep exposed decisions out of the primary independent-lift analysis. If the owner later wants a visible mode, evaluate it separately for influence as well as usefulness; shadow accuracy cannot establish that displaying predictions is non-steering.

My recommendation is to build the smallest version that can fail honestly: one owner, one well-defined decision domain, local data, versioned evidence, and hidden prospective forecasts. Advance only if personal history beats strong controls at useful coverage, corrections and revocations reach the derived state, and the forecast has no operational path into action. That would establish a capability worth discussing for Duality without confusing prediction with authorship.
