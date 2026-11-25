# CERE — Episode Schema v1 (the episode form)
### Status: DRAFT · Date: November 25, 2026 · **Takes effect only on Ken's word.**
### Nothing written with this form counts as evidence until Ken locks it — and no episode counts at all until Ken confirms it (Gate G-3).

---

## What an episode is, in plain words

An **episode** is one of Ken's decisions, written down in a fixed shape: what came up, what he knew at the time, what his choices were, what he picked, and what happened after.

Episodes are the **only fuel** CERE runs on. The list of confirmed episodes is called the **Precedent Index** — "the index" for short. A forecast, a guess, or a profile statement is **never** an episode and never enters the index (Charter P-3; Enforcement Charter E-9).

**The G-3 rule (Enforcement Charter, Gate G-3):** the system may *propose* an episode from the record. **Ken confirms or rejects it.** An unconfirmed proposal is not evidence — it cannot be counted, quoted, or built on. Episodes are **clustered by decision**: one decision = one cluster, no matter how many emails, chats, or records describe it. Several records about the same decision never count as several votes (Architecture & Math, Eq. 2; Perplexity verdict §1).

---

## The form — every field, in plain words

### Identity and status

| Field | What it means, plainly | Required? |
|---|---|---|
| `schema_version` | Which version of this form the episode was written on. This form is **1.0**. The version is never quietly changed — a new form gets a new number (Gate G-3: "episode schema is versioned"). | Yes |
| `episode_id` | A short unique name for this episode, e.g. `ep-2026-11-24-llc-date`. | Yes |
| `cluster_id` | The decision this episode belongs to. One decision = one cluster. If three records describe the same decision, all three carry the same `cluster_id` and count **once**. | Yes |
| `status` | Where the episode stands: **proposed** (written by the system, waiting), **confirmed** (Ken said yes — only now is it evidence), or **rejected** (Ken said no — kept on file as rejected, never used). | Yes |

### The decision itself

| Field | What it means, plainly | Required? |
|---|---|---|
| `domain` | What kind of decision this was. For now this is locked to one value: **business & platform decisions** (the locked study domain — see Window #1 predeclaration). | Yes |
| `trigger` | Which of the five mechanical triggers fired — the named event that made this a decision point (Enforcement Rule E-1; Domain & Triggers Draft, Nov 23, 2026). One of: **(1)** a platform or store problem surfaces · **(2)** a new channel or platform opportunity appears · **(3)** a vendor or program offer arrives · **(4)** a product-line question opens · **(5)** a posting-scope question opens. No trigger, no episode. | Yes |
| `decision_point_time` | The date and time the decision landed in front of Ken — when he had to call it, not when paperwork finished. | Yes |
| `situation` | What came up, in one or two plain sentences. | Yes |
| `known_at_the_time` | The facts Ken actually had when he decided. Nothing learned later may be written here — later knowledge would make old decisions look easier or dumber than they were (Enforcement Rule E-3: no future information leaks backward). | Yes |
| `options_faced` | The full list of choices that were really open to him at that moment — including **defer** (park it to a date) and **none of these** wherever they were real options (Enforcement Rule E-2). Written as they looked *then*, not tidied up afterward. | Yes |
| `choice_made` | What Ken actually picked, stated in the study's outcome words (Domain & Triggers Draft): **close / decline** · **fix it himself** · **escalate** · **defer to a named date** · **none of these**. If he deferred, the date and the reason go here too. | Yes |
| `committed_at` | When Ken committed to the choice (his message, tap, or filing time). | Yes |

### The shape of the situation (helps the math weigh how alike two decisions are)

| Field | What it means, plainly | Required? |
|---|---|---|
| `stakes` | What rides on it, in plain words — money at risk, a deadline, a reputation point. | If known |
| `reversibility` | Could the call be undone cheaply, or was it one-way? (`easy to undo` / `hard to undo` / `one-way`) | If known |
| `who_is_affected` | Who else the decision touches — just Ken, the business, a vendor, customers. | If known |
| `time_pressure` | Was there a clock on it? (`none` / `days` / `hours`) | If known |

*(These four come from the Architecture & Math document, Part 1, component 2 — the Precedent Index is indexed by exactly these situation features.)*

### What happened, and where the proof lives

| Field | What it means, plainly | Required? |
|---|---|---|
| `outcome` | What actually happened afterward — filled in later, when it's known. Left blank at first; an episode does not need its ending to be proposed. | Later |
| `source_records` | Where this episode comes from — the dated records, messages, or files that describe the decision. This is the episode's lineage: if a source is ever corrected or pulled, everything built from it is pulled and rebuilt (Enforcement Rule E-9). | Yes |
| `exposure_status` | Whether Ken had seen any CERE forecast about this decision **before** he decided: **no forecast existed** / **forecast sealed, unseen** / **forecast seen before deciding**. The last one permanently keeps the episode out of the primary scoring (Enforcement Rule E-6) — a choice a forecast may have caused can't prove the forecast was right. | Yes |

### The confirmation trail (Gate G-3)

| Field | What it means, plainly | Required? |
|---|---|---|
| `proposed_by` / `proposed_at` | Who wrote the proposal (the system / Lux) and when. | Yes |
| `ken_decision` | **confirmed** or **rejected**, exactly as Ken gave it. | At review |
| `ken_decision_at` | When Ken confirmed or rejected it. | At review |
| `corrections` | Anything Ken fixes in the episode, with the date. Corrections are law (Charter P-8): the corrected version is what the index uses, and the correction itself stays on the record. Ken may also delete an episode outright — the deletion is honored at once, and any change it makes to scoring coverage is reported, never quietly absorbed (Enforcement Rule E-10). | As they happen |

---

## The propose → confirm / reject flow (Gate G-3)

1. **A trigger fires** in the normal flow of work (a platform problem, an offer, a channel question…).
2. **The system drafts a proposed episode** from the record — every field above filled from sources, nothing invented. Status: **proposed**.
3. **Ken reviews it** — one tap or one short message per episode (Enforcement Rule E-12: Ken's step costs one tap; all the structuring is the system's work). He can **confirm**, **reject**, or **correct** any field.
4. **Confirmed** → the episode enters the Precedent Index and may be used as evidence. **Rejected** → it is filed as rejected and never used. **Still proposed** → it is *not* evidence, full stop.
5. Episodes are **append-only and version-sealed** once confirmed (Enforcement Rule E-11). A fix is a dated correction entry, never a silent edit — an in-place edit invalidates study results back to the last sealed version.

**What never happens:** a forecast never becomes an episode; a verdict never becomes an episode; a profile statement never counts as a vote beside the episodes it was built from (Charter P-3, Enforcement Rule E-9). Ken's *decisions* are data. The model's *guesses* are not.

---

## EXAMPLE — proposed, not confirmed

*Built from a real decision already on record (MEMORY.md, business sequence entries, Nov 24, 2026). Shown so Ken can see the form filled in. It is an example only — it enters nothing until Ken confirms it like any other proposal.*

| Field | Value |
|---|---|
| `schema_version` | 1.0 |
| `episode_id` | `ep-2026-11-24-llc-date` |
| `cluster_id` | `llc-filing-timing` |
| `status` | **proposed** (example) |
| `domain` | business & platform decisions |
| `trigger` | (3) a vendor or program offer arrives — a fee-bearing filing decision with a date on it (the LLC filing, ~$150 state fee, date set for Dec 1) |
| `decision_point_time` | November 24, 2026 |
| `situation` | The Diverse Innovation LLC filing was planned for December 1, 2026. Ken moved it to January 2027. |
| `known_at_the_time` | Dec 1 was the standing plan (set Nov 5). Filing in January puts it after McDonald's last paycheck of December — a fresh January start. Moving the LLC also moves what hangs off it: the business insurance decision, re-filing "Too Much On Purpose" under the LLC, first filing of "Tech Love Tech Services" under the LLC, the LLC's own EIN, and channel timing (Amazon + Walmart under the LLC). The sole-proprietor DBA, sales tax license, and store were already live and unaffected. |
| `options_faced` | File Dec 1, 2026 as planned · **defer to January 2027** · close / decline (don't form the LLC) |
| `choice_made` | **Defer to a named date** — January 2027, after the last December paycheck, for a fresh January start |
| `committed_at` | November 24, 2026 (Ken's direction, recorded same day) |
| `stakes` | The whole business structure sequence: insurance, both DBA filings, bank and channel steps all key off this date |
| `reversibility` | Easy to undo — a date can move again; nothing was filed or paid |
| `who_is_affected` | Ken and the business |
| `time_pressure` | Days — Dec 1 was a week out |
| `outcome` | Pending — the January filing hasn't happened yet. Downstream dates were re-set the same day (insurance decision → Jan 4, 2027; Huntress review → Jan 5, 2027). |
| `source_records` | MEMORY.md: LLC entry ("MOVED Nov 24, 2026: filing pushed from Dec 1, 2026 to January 2027"); business setup sequence entry (Nov 5, 2026, step 4 updated Nov 24); DBA filings entry (Nov 24, 2026) |
| `exposure_status` | No forecast existed — CERE has never made one |
| `proposed_by` / `proposed_at` | Lux, November 25, 2026 (as the worked example in this draft) |
| `ken_decision` | — not yet given (example) |

---

*Drafted November 25, 2026. Sources: Enforcement Charter Gate G-3 and Rules E-2, E-3, E-6, E-9, E-10, E-11, E-12; Architecture & Math (Nov 23, 2026), Part 1 components 2 and 7, Eq. 2; Blueprint (Nov 23, 2026) §§3, 5; Senior Audit A-1; Domain & Triggers Draft (Nov 23, 2026).*
