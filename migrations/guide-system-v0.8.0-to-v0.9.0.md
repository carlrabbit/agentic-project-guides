# Migration — Guide System v0.8.0 to v0.9.0

## Purpose

Adopt planning-seeded, lossless execution-ledger coverage for AI-executed milestones.

0.9 corrects a weakness in the 0.8 execution model: an implementation agent could create a structurally valid ledger while compressing many independently verifiable milestone obligations into broad work-package summaries, weakening completion traceability.

## Migration required

Recommended for repositories that use AI-executed milestones and persistent `.execution/<milestone-id>.md` ledgers.

Repositories that do not use AI-executed milestone execution may update guide metadata with no behavioral repository change.

## Model change

0.8 used:

```text
planning
  -> ready milestone

implementation
  -> create/reconcile execution ledger
  -> derive work packages
```

0.9 uses:

```text
planning
  -> ready milestone
  -> seed lossless obligation registry in .execution/<milestone-id>.md

implementation
  -> verify seeded obligation coverage
  -> derive work packages
  -> map work packages to obligation IDs
  -> attach criterion-specific evidence
```

The ledger remains operational state rather than project authority.

## Planning requirements

For every new AI-executed ready milestone:

1. assign stable IDs to every independently verifiable acceptance criterion and every other material completion obligation;
2. assign stable IDs to required validation gates;
3. record which obligation IDs each validation gate is intended to prove;
4. create `.execution/<milestone-id>.md` before `ready`;
5. seed one pending row per obligation;
6. verify exact set equality between applicable milestone obligation IDs and seeded ledger rows;
7. leave work-package mapping, implementation tasks, evidence, status progression, and resume state empty for implementation.

Do not collapse several separately provable behaviors into one criterion or ledger row merely to reduce document size.

## Implementation requirements

Implementation must preserve the planner-seeded obligation registry.

It may map several obligation IDs to one work package, but it must not delete, merge, renumber, paraphrase, or replace seeded obligation rows merely to simplify execution.

A validation result proves only the obligation IDs whose required behavior the executed test/scenario actually exercises.

Before `COMPLETE`, verify:

```text
set(applicable milestone obligation IDs)
==
set(ledger obligation IDs)
```

Then verify concrete implementation and validation evidence for every individual applicable obligation.

## Existing milestone treatment

### Draft/planning milestones

Before marking an AI-executed milestone `ready`:

- add stable obligation IDs where missing;
- make independently verifiable criteria separate;
- seed the execution ledger;
- seed required validation gates and their intended obligation coverage.

### Ready but not yet implemented

Prefer migrating the milestone and ledger to the 0.9 shape before implementation starts.

If no seeded ledger exists, create it from the milestone without compressing obligations.

### Active implementation

Reconcile the current milestone and ledger:

- enumerate every applicable milestone obligation separately;
- assign stable IDs where the milestone lacks them;
- preserve existing work packages;
- expand grouped ledger summaries into separate obligation rows;
- map existing work packages/evidence to those rows;
- reopen any `done` obligation whose specific evidence is missing, indirect without justification, substitute-only, or inferred only from an aggregate pass.

Do not discard useful existing execution evidence merely because the ledger shape changes.

### Completed milestones

No retroactive ledger migration is required.

If a completed milestone is later reopened, apply the 0.9 ledger model at that time.

## Validation mapping example

Do not treat:

```text
VAL-03 integration scenario: PASS
```

as evidence for every acceptance criterion associated with the feature.

Instead record the behaviors actually exercised:

```text
VAL-03
  proves: AC-07, AC-08, AC-09
```

If `AC-10` requires a direct-placement scenario and `AC-11` requires numeric references, they remain pending until validation actually exercises those behaviors.

## Guide metadata

Update `.guide-profile.json` guide-system and applicable profile versions to `0.9.0` when adopting this guide version.

No schema-version change is required; `.guide-profile.json` remains schema version 2.

## Completion

Migration is complete when new AI-executed planning seeds a lossless obligation ledger before `ready`, implementation owns only the execution extension of that ledger, and completion reconciliation proves each applicable obligation individually rather than relying on grouped work summaries or aggregate validation claims.
