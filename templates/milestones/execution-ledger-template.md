# Execution Ledger — <Milestone ID>

Primary milestone: `<repository-relative milestone path>`

This file is operational implementation state. It is not project authority and does not amend the ready milestone.

For AI-executed milestones, planning initializes this ledger before the milestone becomes `ready`. Planning seeds the lossless milestone-obligation registry and required validation gates. Implementation extends the ledger with work packages, evidence, status, and resume state.

The execution ledger may compress work. It must not compress obligations.

## Milestone Obligation Registry

Planner-owned columns are `ID`, `Type`, and `Obligation`. Implementation must not delete, merge, renumber, paraphrase, or replace planner-seeded obligation rows.

Implementation-owned columns are `Work package(s)`, `Implementation evidence`, `Validation evidence`, and `Status`.

| ID | Type | Obligation | Work package(s) | Implementation evidence | Validation evidence | Status |
|---|---|---|---|---|---|---|
| AC-01 | acceptance | <exact milestone acceptance obligation> | | | | todo |
| DOC-01 | documentation | <material documentation obligation, when applicable> | | | | todo |

Use stable milestone obligation IDs such as `AC-01`, `DOC-01`, `ART-01`, `MIG-01`, or `REV-01` where useful. The prefix taxonomy is illustrative; stable uniqueness and lossless correspondence with the milestone are what matter.

Every individually verifiable acceptance criterion and every other material completion obligation must have its own row. Several obligations may map to one work package, but they must remain separate rows.

Use `todo`, `in-progress`, `done`, or `not-applicable` for implementation status. `not-applicable` is valid only when the milestone itself makes the obligation conditional and current repository state proves the condition does not apply; record that evidence explicitly.

An obligation is `done` only when the live repository and recorded evidence establish that specific obligation. A broad test-suite pass, work-package completion, or neighboring criterion does not establish unrelated obligations.

Before implementation starts, verify that the set of applicable obligation IDs in the milestone equals the set represented in this registry. If the planner-seeded registry is incomplete or inconsistent with the milestone, reconcile it from the milestone without compressing obligations; if the mismatch reflects a material contract ambiguity, return to planning.

## Work Packages

Implementation owns this section.

### WP1 — <Coherent implementation outcome>

Covers:

- <one or more seeded obligation IDs, e.g. AC-01, AC-02>

Tasks:

- [ ] <local implementation task>

Relevant validation:

- <VAL ID, command, shard, test, or evidence>

Evidence:

- <fill as work completes>

Work packages may group many obligations. They do not replace the individual obligation rows above.

## Validation Gates

Planning seeds required validation gates before `ready`. Implementation records execution evidence and status.

| ID | Required validation | Target/locus | Proves obligations | Status | Evidence |
|---|---|---|---|---|---|
| VAL-01 | <command/check> | <target + local/CI/remote/mixed> | <AC-01, ...> | todo | |

A validation gate may prove several obligations, but `Proves obligations` must name the specific obligation IDs actually exercised. Do not infer criterion coverage merely because an aggregate suite passed.

## Resume Point

Implementation owns this section.

Last completed work package:

Current work package:

Next concrete action:

Known agent-resolvable gaps:

External blockers or planning escalations:

## Final Reconciliation

Before `COMPLETE`:

- [ ] reread the primary milestone from disk;
- [ ] enumerate the milestone's applicable obligation IDs;
- [ ] verify exact set equality with the planner-seeded obligation registry;
- [ ] verify no obligation was merged, deleted, renumbered, or replaced by a broader summary;
- [ ] reconcile every obligation ID against its concrete implementation evidence;
- [ ] verify each required validation claim actually exercises the obligation IDs it claims to prove;
- [ ] downgrade any stale, indirect-without-justification, substitute-only, or merely asserted `done` state;
- [ ] confirm every required validation gate has current evidence from the declared target/locus;
- [ ] confirm no agent-resolvable gap remains;
- [ ] run the milestone's final validation and completion audit.
