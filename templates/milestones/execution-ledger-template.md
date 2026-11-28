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
- `reopened` — a `done` entry turned out not to be met (for example a later regression or a review finding); work on it again. The implementer sets this; no amendment is needed.
- `superseded` — a planning amendment replaced this entry; the result column names the replacing ID(s) and the amendment label.

Planning owns what an obligation is (identity, meaning, applicability); the implementer owns its status.

## Amendments (only when a planning amendment changes obligations)

Only a planning amendment may refine, add or supersede obligations. Keep every original row. Add each new or refined obligation as its own row, using a traceable ID: a sub-ID for a refined obligation (for example `AC-03.1` under `AC-03`) or the next free ID for a new one. A refined parent becomes `superseded` by its sub-IDs. In the result column, name the amendment label that introduced or changed the row. A defect repair inside an existing obligation needs no new row.

Identify amendments with a local label such as `A1 (2026-11-28)`, not a commit SHA: the amendment and its ledger changes are usually one commit, which cannot contain its own SHA. Report the exact amended revision in the handoff instruction instead.

| Amendment | Change |
|---|---|
| <A1 (date)> | <for example: superseded AC-03 by AC-03.1/AC-03.2; added AC-07> |

## Implementation progress / resume context (when useful)

- <Next implementation step, significant discovery, or pointer to live code>

## Completion accounting

The ledger is the history: it keeps every ID ever issued. The **effective** obligations are the entries that are not `superseded`.

Before `COMPLETE`, check that the effective obligation IDs equal the obligation IDs of the current (possibly amended) milestone, and that every entry has a truthful disposition against the delivered result. Every effective obligation must be `done`; none may stay `pending`, `in progress` or `reopened`, and a genuine blocker ends the run as `BLOCKED`, not `COMPLETE`. Each `superseded` entry must name replacements that are themselves effective (or superseded in turn), so it cannot hide unfinished work. Resolve scope changes with planning. This is **not** a requirement to attach a test, evidence case, validation gate, or fingerprint per obligation. Run proportionate focused checks separately.

Keep this ledger through implementation/review. Afterward retain or archive per project policy; place a short durable completion summary in the milestone.
