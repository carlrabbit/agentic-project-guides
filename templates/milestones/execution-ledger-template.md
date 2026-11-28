# Execution Obligation Ledger — <Milestone ID>

> Planner-seeded operational completeness inventory for a substantive milestone. The ready milestone is authoritative. Not an evidence registry or validation matrix. For a genuinely trivial indivisible task, the planner may explicitly omit this file.

**Milestone:** <repository-relative milestone path>
**Updated:** <date/commit or session>

## Planned obligations

| ID | Material outcome (same meaning as milestone) | Status | Brief result / blocker |
|---|---|---|---|
| AC-01 | <First independently deliverable requirement> | pending | |
| AC-02 | <Second independently deliverable requirement> | pending | |
| DOC-01 | <Required documentation or migration deliverable, if any> | pending | |

Planning seeds **all** material obligations before `ready`; IDs correspond to the milestone and cannot be compressed, deleted, or renumbered by implementation. Omit example rows that do not apply; do not invent rows for individual tests.

Status values:

- `pending`, `in progress`, `done`, `blocked` — normal execution states.
- `reopened` — a planning amendment found a `done` entry incomplete; work on it again.
- `superseded` — a planning amendment replaced this entry; the result column names the replacing ID(s) and the amendment revision.

## Amendments (only when a planning amendment changes obligations)

Only a planning amendment may change this inventory. Keep every original row. Add each new or refined obligation as its own row, using a traceable ID: a sub-ID for a refined obligation (for example `AC-03.1` under `AC-03`) or the next free ID for a new one. In the result column, name the amendment revision that introduced or changed the row. A defect repair inside an existing obligation needs no new row.

| Amendment revision | Change |
|---|---|
| <commit SHA or reconciled version> | <for example: refined AC-03 into AC-03.1/AC-03.2; reopened AC-05; added AC-07> |

## Implementation progress / resume context (when useful)

- <Next implementation step, significant discovery, or pointer to live code>

## Completion accounting

Before `COMPLETE`, check that the set of applicable milestone obligation IDs (original plus any added by amendment) equals the ledger IDs, and that every entry has a truthful disposition against the delivered result. No entry may stay `reopened`. A `superseded` entry is accounted for by its replacing IDs. Resolve scope changes with planning. This is **not** a requirement to attach a test, evidence case, validation gate, or fingerprint per obligation. Run proportionate focused checks separately.

Keep this ledger through implementation/review. Afterward retain or archive per project policy; place a short durable completion summary in the milestone.
