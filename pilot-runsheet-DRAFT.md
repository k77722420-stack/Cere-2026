# CERE — One-Week Verdict Pilot Run Sheet
### Status: DRAFT · Date: November 25, 2026 · **Takes effect only on Ken's word.**
### Read this first — what the pilot week is, and what it is not

The charter is specific about this week (Enforcement Rule **E-12**):

> *"The workflow is piloted for one week with **forecasting disabled** before any study window opens; if the commit habit doesn't hold, the workflow is fixed before the predictor is judged."*

So the pilot week tests **the habit, not the predictor**:

- Ken's decisions get **noticed** when a trigger fires.
- Ken **commits** each decision in one tap or one short message — *before* anything is shown to him.
- Each committed decision becomes a **proposed episode** (Episode Schema v1), which Ken **confirms or rejects** in one tap each.
- **No forecasts are made, frozen, revealed, or scored during the pilot week.** There is nothing to be right or wrong about yet — on purpose. A week of clean commits and confirmed episodes is the fuel Window #1 will run on, and proof the routine costs Ken seconds, not effort (Senior Audit A-9: if the commit step costs more than a few seconds, the study starves).

The forecast procedure — freeze, hide, reveal, score — is written out in **Part B** so it is ready and agreed in advance. It switches on only when Window #1 is locked (Window #1 Predeclaration, Lock section). It is **not active** during the pilot week.

---

## Part A — The pilot week, day by day

**Before Day 1 (setup, Lux does all of it):**
- The five triggers (Window #1 Predeclaration §3) are pinned where Lux works from them.
- The commit phrase is agreed: Ken types or taps **"decided: ___"** (e.g., *"decided: close it"*, *"decided: defer to January"*) in the main chat — or just tells Lux the decision in his own words as he makes it. One short message is the whole step (Rule E-12).
- Episode Schema v1 is the form Lux drafts from. Nothing else needs building.

**Every day, Days 1–7 — the same loop:**

| Step | What happens | Who |
|---|---|---|
| 1. **Notice** | A trigger fires in the normal flow of work (a platform problem, an offer, a channel or posting question). Lux spots it while doing the day's ordinary work — inbox, store, pages — and logs a **decision-point notice**: time, which trigger, the situation in one line. Ken never has to flag decisions himself; unflagged-by-Lux is the only miss that counts against the workflow. | Lux |
| 2. **Wait for the commit** | Lux does **not** ask "what will you do?" and offers no prediction, hint, or lean. Ken decides the way he always decides. | Ken |
| 3. **Commit** | Ken records the decision with one tap / one short message ("decided: ___"). Lux timestamps it exactly as received. This timestamp is what later proves a forecast (in window time) was frozen *before* the commit. | Ken → Lux logs |
| 4. **Draft the episode** | Same day, Lux turns the notice + commit into a **proposed episode** on the schema form — every field from the record, nothing invented. Status: proposed. It is **not** evidence yet (Gate G-3). | Lux |
| 5. **Confirm / reject** | Once a day, in one batch, Lux shows Ken the day's proposed episodes. Ken confirms, rejects, or corrects each — one tap each. Confirmed episodes enter the Precedent Index; rejected ones are filed as rejected and never used. | Ken |
| 6. **Log the workflow numbers** | Lux records the day's counts: notices logged, commits received, commits that arrived *without* Lux having noticed first (workflow misses), episodes proposed / confirmed / rejected, and roughly how long Ken's steps took him. | Lux |

**Day 7 (closing the week):**
- Lux writes the **pilot verdict report** (format below) and brings it to Ken.
- The go / no-go question is only about the habit: *did noticing + committing + confirming hold for a week at a cost of seconds per decision?*
- If the habit held → the workflow is proven, and Window #1 may be predeclared and locked on Ken's word.
- If the habit didn't hold → the workflow gets fixed and the pilot re-runs. **The predictor is never judged on a broken workflow** (Rule E-12).

### Pilot verdict report format (end of pilot week)

1. **Coverage of the habit:** decision points noticed ___ / triggered decisions that actually happened ___ (and how Lux knows — any decision found afterward that nobody logged is listed by name).
2. **Commits:** received ___ / expected ___; every missed commit listed, with the reason if known.
3. **Episodes:** proposed ___ · confirmed ___ · rejected ___ · still pending ___.
4. **Ken's cost:** the commit + confirm steps, in plain terms (taps per day, roughly seconds each).
5. **Breaches:** any stop-rule event from Part C, or "none."
6. **Verdict line:** *habit held* / *habit needs fixing* — with the fix proposed if it's the second one.

---

## Part B — The forecast procedure (activates only when Window #1 opens — NOT during the pilot)

Written now so the mechanics are agreed before any forecast exists. Every step is mechanical; nobody improvises.

1. **Notice.** Same as Part A step 1 — a trigger fires, Lux logs the decision-point notice (time, trigger, situation).
2. **Forecast and freeze.** *Before* Ken decides, Lux computes the forecast from the confirmed Precedent Index **as it exists at that moment** (Rule E-3: index, profile, and recall reconstructed as of the decision point — no future information). The forecast is written in the Window #1 format (ranked conclusions, probabilities, evidence, counter-evidence, strongest alternative, N_eff), **timestamped, and frozen** — sealed exactly as written. β = 0: statistics only, no model adjuster (Rule E-4).
3. **Hide.** The frozen forecast is stored where Ken does not see it. No hint, summary, lean, or "the system has a view on this" reaches Ken — in any wording, in any chat (Gate G-4; Charter P-2, P-7). Lux's ordinary help on the decision continues exactly as if no forecast existed.
4. **Commit.** Ken decides and commits — one tap / one short message, timestamped (Rule E-12). The commit timestamp must be **after** the freeze timestamp; that ordering is the whole proof of shadow mode.
5. **Score the verdict.** After the commit, Lux scores the frozen forecast against the actual choice and writes the verdict to the **verdict ledger** — metadata only, in stop-record style: *predicted X at p = ___; Ken chose Y; hit / miss; Brier score; log loss; exposure status* (Architecture & Math, component 7; Blueprint §3 step 5). The forecast text is never stored as fact about Ken (Charter P-3). The ledger is held at the same protection level as the profile (Gate G-2).
6. **Reveal — batched, weekly.** Ken sees the week's forecasts in **one weekly batch**, after his commits — never in the moment (Rule E-7). A forecast is included in the reveal only if its top probability met the speaking threshold τ; below-threshold forecasts stay unshown and are graded silently (Charter P-6). Every reveal restates the standing limitation: *same-decision uncontaminated, not influence-free across decisions.*
7. **Ken's choice becomes data.** The committed decision is drafted as a proposed episode (schema v1) and goes through the same confirm / reject step as the pilot. Confirmed episodes join the index and may inform later forecasts. The forecast itself never does.

### Window verdict report format (end of Window #1 — Rule E-8 reporting order, no exceptions)

1. **Brier score and log loss across ALL scored cases** — CERE vs. the generic-user control, side by side.
2. **Spoken-forecast error at its coverage** — error among revealed forecasts, with the coverage figure beside it. Accuracy is never shown without coverage.
3. **Counts and uncertainty, paired by decision cluster** — forecasts made, graded, hits, misses, exposed (excluded from the primary numbers, listed separately with their count).
4. **Exposure line:** exposed decisions ___ (excluded from primary scoring per Rule E-6), or "none."
5. **Coverage-change line:** any deletion or correction that changed evaluation coverage during the window (Rule E-10), or "none."
6. **The E-5 check:** N reached ___ / target ___ · lift vs. control ___ / minimum ___ · spoken-error ___ / acceptable ___ · coverage ___ / minimum ___ → **advance** (propose to Ken) or **archive with a written negative result**. Both are honest endings; a negative result is a success of the method.

---

## Part C — Stop rules (both parts, no exceptions)

A stop rule firing **halts the pilot (or the window) on the spot**. It is never worked around, patched quietly, or re-tried the same day. Every stop is recorded as a **dated incident** in the project record — what rule, what happened, what was suppressed — and work resumes **only on Ken's word** (Enforcement Charter, Part 3: "Violations stop work").

1. **Gate G-3 breach** — an unconfirmed episode is treated as evidence, counted, or quoted anywhere. → Stop; the affected material is suppressed (Rule E-9).
2. **Gate G-4 / P-7 breach** — any forecast, hint, or lean reaches Ken before his commit, in any wording. → Stop; the decision is marked **exposed** and excluded from primary scoring permanently (Rule E-6), on top of the stop.
3. **Gate G-5 breach** — profile, episode, or verdict data goes to any external model or service without Ken's explicit, per-case, recorded decision. → Stop.
4. **Rule E-11 breach** — any in-place edit to a confirmed episode, a frozen forecast, the charter, or a threshold (no dated correction entry / new version). → Stop; results back to the last sealed version are invalid.
5. **Rule E-9 trigger** — a source record is corrected or pulled and derived material built from it is *not* invalidated. → Stop until the invalidation is done and verified.
6. **Protection breach** — study data found outside its encrypted backup / protection class (Gate G-2), or the backup found unreadable. → Stop; restore-verify before anything resumes.
7. **Workflow failure (pilot only)** — commits missed on 2 or more days, or Ken's step is costing more than a few seconds a decision. → Pause the pilot; fix the workflow first (Rule E-12, Audit A-9). This is a workflow verdict, never a predictor verdict.
8. **Ken says stop.** — No reason needed, no argument offered. The stop is recorded and everything waits for his word.

---

*Drafted November 25, 2026. Sources: Enforcement Charter Rules E-3, E-4, E-5, E-6, E-7, E-8, E-9, E-10, E-11, E-12 and Part 3 (violations stop work); Gates G-2, G-3, G-4, G-5; Blueprint (Nov 23, 2026) §3; Architecture & Math (Nov 23, 2026), components 6–8, Eq. 8; Senior Audit A-9; Perplexity design verdict (Nov 23, 2026) §5.*
