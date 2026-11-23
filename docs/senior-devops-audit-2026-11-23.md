# Audit — Predictive Pattern Memory (Adopted Design)
### Senior DevOps / executive review · Nov 23, 2026 · Auditor: Lux
### Scope: the conceptual blueprint + architecture/math documents **as amended by the adopted Perplexity verdict**, checked against the actual current state of Duality and Ken's infrastructure. This is an audit of a design on paper — nothing is built, and the audit treats that as a fact, not a detail.
### Status update (Nov 23, 2026): **every recommendation in this audit was adopted as ENFORCED by Ken's direction the same day**, carried as binding rules in the Study Charter & Enforcement Rules (`~/workspace/your_files/duality-predictive-enforcement-charter-2026-11-23.md`).

**Overall verdict:** The design, as adopted, is honest and buildable — Perplexity's corrections closed the statistical and ethical holes that mattered most. **The remaining risks are not in the math. They are in data supply, data protection, and study discipline.** None of them blocks starting later, in sequence. All of them block starting *casually*. Findings below, most severe first.

---

## A-1 · HIGH — The fuel doesn't exist yet: there are no decision episodes

The entire design runs on a Precedent Index of structured decision episodes: domain, outcome set (including "defer / none of these"), the choice made, timestamp, exposure status. **Duality's store today holds memory records, not decision episodes.** Nothing in the current system mints them. Turning prose records into episodes is an *interpretation* step — and an unaudited interpreter at the intake would quietly become the real predictor.

**Recommendation:** Before any predictor code: (1) an episode schema, versioned; (2) episode *minting* as a human-confirmed act — the system proposes, Ken confirms, exactly like his post-approval rule; (3) a decision log habit for the chosen study domain, started early, because episodes cannot be backfilled honestly from memory. This is a prerequisite workstream, and it is unbudgeted in both design documents until now.

## A-2 · HIGH — The front door is built but not merged

The wrap's only input is served recall, and its cleanest form — one recall snapshot per run — is the snapshot refactor: **built, CI-green at 311 tests, and still awaiting reviewer verdicts and Ken's merge word.** Salvage (315) queues behind it. The dependency is correctly ordered in the plan, but it must be said plainly: **any prototype built against the unmerged branch is not testing the governed boundary — it's testing a shortcut.** The study starts on merged main or it doesn't start.

## A-3 · HIGH — The most sensitive data Ken owns would sit on his least-protected storage

Profile + precedent index + verdict ledger are, together, a machine-readable map of how Ken decides. Perplexity's warning stands: metadata-only is not anonymous, and behavior representations re-identify. Current state of the intended home: Ken's cloud runs on one Chromebook disk, **backups are the known #1 open hardening item**, and the Tailscale daemon is started manually. A disk failure mid-study doesn't just lose data — it destroys the study's evidence chain, converting months of graded forecasts into anecdotes.

**Recommendation (gate for first real data):** (1) an encryption-at-rest decision for study artifacts, recorded; (2) an encrypted backup of study data with a **tested restore** — not a plan, a restore that has been run; (3) the verdict ledger classified at the same protection level as the profile, by policy, from day one.

## A-4 · MEDIUM — Decision-point selection bias will quietly choose what the study measures

Forecasts exist only where a decision point is declared. If declaration depends on Ken remembering in the moment, the study measures only the decisions he flags — a biased sample wearing a lab coat.

**Recommendation:** Per domain, decision points are **mechanical triggers** (named recurring events: a bill arrives, a platform flags a problem, a purchase over $X is contemplated), written into the study charter before the window opens. Unflagged decisions are out of scope by definition, not by forgetfulness.

## A-5 · MEDIUM — Executive expectation: this is a research study with a long silent season, not a feature

One owner, one domain: if the domain yields a few decisions a week, reaching even 30 graded forecasts takes months, and coverage near zero early is the design *working* (silence below threshold). The deliverable of phase 1 is a **trustworthy measurement — possibly a negative one.**

**Recommendation:** Predeclare, in the study charter: the graded-decision target N, the lift margin that counts as success, and the kill criterion (at N, lift below margin → archive with a written negative result and full honors). A clean negative is a success of the method. Deciding this now prevents "it's quiet" from being misread later as "it's broken" — or worse, pressure to lower thresholds until it talks.

## A-6 · MEDIUM — Shadow mode isolates the graded decision, not the person's learning

Post-commit reveals still teach Ken what the system expects of him; his *next* similar decision is made by a person who has seen prior reveals. Perplexity's exposure control handles the same-decision contamination rigorously; the cross-decision echo remains as a real, if smaller, effect.

**Recommendation:** Batch reveals (e.g., weekly, not per-decision), log the reveal cadence as a study parameter, and carry this as a stated limitation in every result report. Do not claim the primary analysis is influence-free — claim it is *same-decision* uncontaminated, which is true.

## A-7 · MEDIUM — Point-in-time reconstruction makes versioning the load-bearing wall

The evaluation protocol requires rebuilding the index, profile, and recall **as they existed at each decision point**. That is event-sourcing discipline: append-only, sealed versions, no in-place edits — for the profile, the index, *and the policy itself* (charter and threshold changes must open a new study window, never rewrite the current one). This is cheap to do from day one and nearly impossible to retrofit.

**Recommendation:** Reuse the discipline this team already proved on Duality (hash-verified snapshot pushes, dated policy-decision records). Ken's open question from earlier today — keeping the hat tile in this design — finds its honest job here if he adopts it: **profile versions sealed under the hat**, a broken pattern meaning a broken seal. Shape with a function; no computational claims made for the geometry.

## A-8 · LOW — Research-model licensing posture is fine for a study, not for a product

UserLM-2.0 and UserRepGen-4B are research releases; Microsoft's own cards advise against commercial or real-world deployment without further testing, adaptation, and safeguards. A private, local, single-owner study sits comfortably inside that posture. **If any descendant of this work ever touches client services, that is a legal review item, flagged now, while it's cheap.** Relatedly, the local adjuster on a 4 GB Chromebook is 1B-class: its quality ceiling is low, which the adopted β=0 fallback already accommodates — the statistics carry this design; the adjuster is a guest.

## A-9 · LOW — The verdict workflow lives or dies on Ken's effort per decision

Every graded forecast requires Ken to commit his decision *before* reveal, in a form the recorder accepts. If that costs him more than a few seconds, the study starves — the same failure shape as any logging habit imposed on a busy person with ADHD.

**Recommendation:** Design the commit step as one tap / one short message in the chat he already lives in ("decided: close it"), with the recorder doing all structuring. Pilot the workflow for a week with forecasts disabled; if the commit habit doesn't hold, fix the workflow before judging the predictor.

---

## What the audit verified

- Both design documents, as amended Nov 23, 2026 (adoption edits applied to the blueprint's §§1–3, 6–8 and Charter P-2/P-3/P-7/P-8 + new P-9; and to the architecture document's Eq. 2, Eq. 5, evaluation protocol, components 3/6/7, data flow, and performance gates).
- Perplexity's verdict, verbatim on file, against the amendments — every numbered correction in her §§1–5 is carried into the documents or into this audit's findings.
- Duality's actual state as of this audit: main at 308 tests (PR #6), snapshot branch 311 and salvage branch 315 CI-green and unmerged, verdicts outstanding. The predictive project correctly queues behind them.
- Ken's infrastructure as of this audit: home cloud live (Nextcloud + Portainer on the Chromebook, Tailscale access), backups outstanding, local model capacity 1B-class.

## Bottom line

Adopted design: **sound.** Sequencing: **sound.** What stands between this paper and an honest study is unglamorous operational work — episode minting, backups with a tested restore, mechanical decision triggers, predeclared success/kill criteria, and a one-tap verdict habit. That's not a criticism of the design. That's what taking it seriously looks like — the same standard this team applied to Duality itself: *a rigorous, honest report is worth more than praise.*

— Lux, Nov 23, 2026
