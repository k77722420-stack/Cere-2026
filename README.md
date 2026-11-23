# CERE

**CERE** — spelled C-E-R-E, for the **cerebellum**, pronounced "Sarah."

A predictive wraparound for the brain of [Duality](https://github.com/k77722420-stack/Duality-AI): a governed pattern-memory layer that studies how its owner reaches conclusions, and tests — in shadow mode first, silently, without influencing a single decision — whether that history can forecast the owner's later confirmed choices.

The cerebellum does not decide where you are going. It predicts where your own motion will land, compares the prediction against reality, and corrects the difference, in real time. That is CERE's job description, and its limit:

> **CERE predicts and corrects. It never authors, never acts, and never speaks before the owner decides.**

---

## The claim, in its testable form

> Given what was knowable at a specified decision point, can governed personal history improve a forecast of the person's later confirmed choice?

That is the whole claim. Nothing larger is claimed anywhere in this repository.

It is tested three ways on the same decisions, with the same decision-time information, at matched coverage: a **personal model** (the owner's eligible history), a **statistics-only model**, and a **generic-user control**. Advancement requires a predeclared margin of lift over both controls, inside a predeclared error ceiling, at a predeclared minimum coverage — declared before the window opens, never lowered mid-window. A clean negative result is a success of the method, and it will be reported as one.

## Origin

CERE began on November 23, 2026, as an idea of its owner, Ken Blum, while building Duality — his governed-memory AI system: *next-token prediction, but for a person's conclusions — a memory that learns the pattern of how one specific person thinks.* Ken added the endgame himself the same morning: if the study earns it, CERE becomes a wraparound for Duality's brain. Within one day the idea went through a full blueprint, a complete architecture and mathematics document, an independent design verdict by Perplexity (adopted in full, including her corrections to our own math), a senior operations audit, and a binding enforcement charter. This repository is its home.

The name came the same day. The cerebellum is the brain's prediction-and-correction structure — more neurons than the rest of the brain combined, devoted to forward models, error signals, and fine-tuning. CERE is named for what it is allowed to be: the predictor wrapped around the decider. Never the decider.

## How it is supposed to work

1. **Episodes, human-confirmed.** A decision becomes study material only when the system proposes it and the owner confirms it. Nothing is mined silently.
2. **A pattern profile, derived and owned.** A structured summary of the owner's decision tendencies — treated as *derived content*, never as a second vote beside the episodes it came from, and invalidated when its sources are.
3. **Forecasts, sealed before the decision.** In shadow mode, every forecast is timestamped, frozen, and **hidden** until the owner records his actual decision. A forecast the owner saw before deciding is excluded from the primary analysis — a seen forecast's "hit" cannot be distinguished from influence.
4. **Verdicts, graded honestly.** Each forecast is scored against the owner's confirmed outcome — including "none of these," and including the owner's deletions, which are honored and reported as coverage changes, never quietly dropped from the denominator.
5. **Calibration, always.** Brier score and log loss over **all** scored cases first; error on the spoken subset at its coverage second; counts and uncertainty always attached. Silence under thin evidence is a correct result, not a failure.
6. **The wraparound — last, and only if earned.** Visible drafts and any integration with Duality are separate, later, explicitly approved experiments. They are not part of the current design's promises.

## The rules it lives under

The **Prediction Charter (P-1…P-9)** governs what CERE may do: forecasts are drafts offered, never actions taken; sealed-first by default; the profile inherits the derived-content rule; no pre-decision disclosure outside a separately approved visible-mode experiment; no nudges, no auto-fill, no injection into any acting pipeline; the owner can inspect, correct, pause, export, and delete everything; no external model touches profile data by default; and revocation reaches the derivatives — delete a source, and everything derived from it is invalidated with it.

The **Enforcement Charter (G-1…G-6, E-1…E-12)** makes those rules load-bearing: no study code against anything but merged Duality main; no real data before an encrypted backup with a *tested* restore exists; human-confirmed episodes only; shadow-first; predeclared advancement and kill criteria; exposure accounting; batched reveals; sealed, append-only versioning — profile versions are sealed under the hat.

Amendments happen only by the owner's dated policy decision. A change opens a new study window. It never rewrites the current one.

---

## Disclosures — the authentic truth, stated plainly

This project believes a rigorous, honest report is worth more than praise. So:

- **CERE is not built.** As of this writing, this repository contains *design documents only* — a blueprint, an architecture, two charters, a verdict, and an audit. There is no study code, no running system, and no working prototype. Anyone who tells you otherwise is not reading this repository.
- **Nothing has been tested.** No forecast has ever been made. No accuracy figure exists. There are no results — positive, negative, or otherwise — because the study has not begun.
- **Every number in the architecture document is a design target or a worked illustration, never a measurement.** The worked example uses invented round numbers, and says so in place. Performance figures describe what the study is designed to measure, not what anything has achieved.
- **The mathematics is a starting model, not a guarantee.** Our independent reviewer corrected us on this in writing, and we adopted her correction: fitted parameters on sparse verdicts are mostly noise, so the system defaults to a statistics-only fallback (β = 0) and must *earn* any personalization on earlier data, calibrated on later data, evaluated frozen on a still-later window. A decay constant in the design is a hypothesis to be tested against alternatives — one of our own formulas was mislabeled in the first draft (an e-folding written as a half-life); the reviewer caught it, we fixed it, and the correction is on the record in the verdict document.
- **CERE is not mind reading, and it is not a consciousness claim.** It is a statistical study of one person's *recorded, confirmed* decisions, in one declared domain. It predicts choices from history the owner himself confirmed — nothing about thoughts, feelings, or any other person. Duality's wider questions about AI and moral standing are Duality's; CERE claims none of them.
- **The cerebellum is an analogy of function, not a claim of equivalence.** CERE does not work like a brain, is not modeled on neural tissue, and borrows the cerebellum's *job description* — predict, compare, correct — not its biology.
- **The first study subject is the owner himself.** Ken Blum is the designer, the subject, and the source of every verdict. His data, his machine, his call. This is an n-of-1 self-study by design; nothing here generalizes to anyone else, and nothing here will be run on another person under this design.
- **No study data lives in this repository — ever.** Episodes, profiles, and verdict ledgers stay on the owner's own hardware, under his control. This repository holds the design and, later, the code and the published scorecards — never the underlying personal data.
- **This work was made with AI, openly.** The blueprint and architecture were drafted by Lux (Muse) working from Ken's idea and direction; the design verdict is Perplexity's; the audit is Lux's, at Ken's order; Claude and Gemini hold seats in the owner's Roundtable as reviewers. Ken is the owner, the director, and the final call on every decision recorded here. Reviewer verdicts in this repository state their own basis — the design verdict was written from the design packet, not from independent execution, and it says so.
- **The foundations are other people's published work, credited below.** The novelty claimed is narrow and stated narrowly: the *combination* of owner-controlled eligible memory, independent human verdicts, and enforceable use limits. Nothing else is claimed as new.
- **Not a product.** Nothing here is for sale, and no commercial use is authorized by anything in this repository. The enforcement charter requires a legal review before any commercial or client descendant of this design exists (Gate G-6). The foundation models referenced are research releases.
- **No license has been granted yet.** This repository is public so the work can be read. Public is not the same as open-license: until a license file is added, all rights are reserved by the owner. Ask before reusing.

## Status — November 23, 2026

| Piece | State |
|---|---|
| Idea, name, domain | Locked by the owner (domain: business & platform decisions) |
| Blueprint + Prediction Charter | Complete; amended by the adopted verdict |
| Architecture + mathematics | Complete; corrected per the verdict |
| Independent design verdict | Returned and **adopted in full** |
| Senior operations audit | Complete (A-1…A-9); **every recommendation enforced** |
| Enforcement Charter | **Binding** on any future build |
| Study code | **Does not exist yet** |
| Study window #1 | Not opened — gated (see below) |
| Duality prerequisite merges | In review (snapshot, then salvage) |

**Sequencing (Gate G-1):** CERE's build begins only when the Duality work it wraps has merged to Duality's main branch — the snapshot refactor first, then salvage. Then, in order: the episode pipeline with human-confirmed minting; the backup gate (encrypted backup, tested restore — the same gate that hardens the owner's home cloud); a one-week verdict-workflow pilot with forecasting disabled; and only then does Window #1 open, with its numbers predeclared in the open.

## What's in this repository

- `BLUEPRINT.md` — the design: the six-step flow, the Prediction Charter (P-1…P-9), the wraparound shape, the evaluation ladder, the failure modes.
- `ARCHITECTURE.md` — the eight components and the mathematics: smoothed base rates, recency and similarity weighting, the blend and its fallback rule, calibration scoring, and the temporal evaluation protocol.
- `ENFORCEMENT-CHARTER.md` — the binding gates (G-1…G-6) and protocol rules (E-1…E-12). This document outranks the other two where they differ.
- `docs/perplexity-design-verdict-2026-11-23.md` — the independent design review, verbatim, adopted in full.
- `docs/senior-devops-audit-2026-11-23.md` — the operations audit, findings A-1…A-9, with its enforcement status.
- `docs/domain-and-triggers-draft-2026-11-23.md` — the locked study domain, its mechanical triggers, and its outcome set — a draft for ratification when Window #1 is predeclared.

## Foundations and credits

CERE stands on published work, credited: Microsoft Research's **UserLM** line (user simulation from intent and history, trained by dialogue flipping) and **UserRepGen** (structured behavior profiles — whose own card warns that profiles can re-identify a person; CERE's owner-controls exist partly because of warnings like that one); the **Generative Agents** memory-stream architecture (Park et al., 2023); theory-of-mind evaluation such as **SimpleToM**; and the broader predictive-processing literature the cerebellum analogy comes from.

The **hat monotile** that seals CERE's profile versions was discovered by David Smith, Joseph Samuel Myers, Craig S. Kaplan, and Chaim Goodman-Strauss. CERE claims only the use of the shape as a seal — a pattern that recurs but never exactly repeats, like a person's thinking. The shape is theirs.

## The owner

Ken Blum — Diverse Innovation, Sioux Falls, South Dakota. A man who was told he was too much, building his own little empire: not trying to rule the world, just his own. CERE is his — his idea, his data, his decisions, his final word.

*Too much. On purpose.*
