# 0019 — Persist Execution Coverage and Progress

## Status

Accepted in guide system v0.7.3.

## Context

A ready milestone can be semantically complete yet still require a long implementation trajectory. During long agent runs, repository inspection, edits, test output, validation receipts, retries, and context compaction can make the executor's conversational working state unreliable.

The v0.7.1 completion audit corrected the stopping condition, but a purely retrospective audit still requires the executor to reconstruct requirement coverage after substantial work has already occurred.

A milestone should remain one coherent semantic contract when appropriate. Splitting every large milestone into smaller milestones would fragment project semantics and reintroduce planning overhead. The missing mechanism is implementation-owned persistent execution state.

## Decision

For AI-executed coding milestones, the canonical executor creates or reconciles a repository-local execution ledger before production edits:

```text
.execution/<milestone-id>.md
```

The ledger is operational implementation state. It is not project authority and must not amend, reinterpret, or replace the ready milestone or its referenced authority.

Before implementation, the executor performs execution decomposition and maps all applicable milestone obligations into bounded work packages. The ledger records at least:

- the primary milestone path;
- bounded work packages;
- milestone acceptance criteria and completion obligations covered by each work package;
- status for each work package or obligation;
- required validation gates;
- concrete evidence as work completes;
- a concise resume point when work remains.

A small milestone may use one work package. The executor does not skip the ledger merely because the work appears simple.

Execution decomposition is not a new planning phase. It may decide local implementation order, files, types, tests, refactorings, and other mechanics already owned by implementation. It must not reopen architectural, semantic, compatibility, scope, acceptance, validation, or human-review decisions settled by planning.

The executor updates the ledger after each coherent work package and its relevant validation. On resume or after context compaction, it rereads the ready milestone and the ledger before continuing.

Before `COMPLETE`, the executor must freshly reread the primary milestone from disk and reconcile:

```text
milestone obligations
<-> execution ledger
<-> live repository and concrete evidence
```

A checked ledger row is not proof by itself. If the repository state or evidence does not establish the mapped obligation, the item is still incomplete.

The ledger is required while the milestone is active. After milestone completion, retention is repository policy; removing an operational ledger after completion does not invalidate independently established milestone evidence.

## Consequences

- implementation progress survives context compaction, session interruption, and model attention drift;
- completion auditing becomes coverage reconciliation rather than retrospective memory reconstruction;
- large coherent milestones can remain semantically unified while implementation proceeds through bounded work packages;
- human reviewers can inspect current execution coverage directly when useful;
- `.execution/` must never become an alternate authority layer;
- no generic engineering commands are required for ledger management;
- planning must shape large milestones so their obligations can be mapped to bounded implementation work packages, but planning does not pre-author the executor's task list.
