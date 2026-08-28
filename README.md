# Agentic Project Guides

Version: 0.7.3

This repository contains a versioned guide system for creating and maintaining AI-friendly project documentation and engineering workflows.

The guide system is intentionally separate from product repositories.

Product repositories contain localized project truth. Planning, migration, documentation synchronization, and guide authoring may use this guide repository. Ordinary implementation agents work from localized repository authority documents and implementation-ready milestones.

## Core rule

```text
Guides live here.
Projects contain project truth.
Milestones are planned before they are implemented.
Planning resolves uncertainty and produces a ready milestone.
A ready milestone must be executable by the project's baseline implementation model.
Implementation begins by decomposing the ready milestone into bounded execution work packages.
AI executors persist coverage and progress in a repository-local execution ledger.
Implementation derives concrete edits from the live repository and the ready milestone.
The executor owns milestone closure, not only code production and test execution.
Validation success is evidence, not milestone completion by itself.
Documentation sync consumes deferred sync hints.
Human review gates milestone completion when automation cannot decide acceptance.
```

## Version 0.7.3

Version 0.7.3 adds execution tractability and persistent execution state to the implementation contract.

A ready milestone remains the semantic implementation contract. The executor does not redo architectural planning, but before production edits it converts the milestone into bounded implementation work packages and creates:

```text
.execution/<milestone-id>.md
```

The execution ledger is operational state, not project authority. It maps milestone obligations and acceptance criteria to work packages, tracks status, and records concrete evidence. Its purpose is to make long implementation runs resumable and to prevent completion from depending on conversational memory.

The implementation loop is now:

```text
read milestone and authority
-> execution decomposition
-> create/reconcile execution ledger
-> implement a work package
-> validate it
-> update ledger
-> repeat
-> reread milestone from disk
-> reconcile milestone <-> ledger <-> repository/evidence
-> final validation and completion audit
-> terminal outcome
```

Before `COMPLETE`, the executor must freshly reread the milestone from disk and prove coverage of every applicable acceptance criterion and completion obligation. A checked ledger row without supporting repository state or evidence is not proof.

Planning still owns project-level decisions. Large coherent milestones do not need to be split merely because they contain substantial implementation volume, but they must be tractable as bounded execution work packages for the baseline implementation model.

Planning handoff is also simplified. Do not generate bespoke per-milestone `EXECUTE-Mxxx.md` files that duplicate the canonical execution methodology or repeat milestone authority. Overlay application instructions and a short handoff identifying the ready milestone remain valid transport artifacts.

No new engineering commands are introduced by v0.7.3.

The terminal outcomes remain:

- `COMPLETE` — every applicable milestone obligation and completion gate is satisfied;
- `AWAITING HUMAN REVIEW` — all agent-resolvable work is complete and a required human decision remains;
- `BLOCKED` — completion requires unavailable external capability or a material planning decision the executor cannot make.

## Upgrade

From v0.7.2, use:

```text
migrations/guide-system-v0.7.2-to-v0.7.3.md
```
