# Agentic Project Guides

Version: 0.7.5

This repository contains a versioned guide system for creating and maintaining AI-friendly project documentation and engineering workflows.

The guide system is intentionally separate from product repositories.

Product repositories contain localized project truth. Planning, migration, documentation synchronization, and guide authoring may use this guide repository. Ordinary implementation agents work from localized repository authority documents and implementation-ready milestones.

## Core rule

```text
Guides live here.
Projects contain project truth.
Milestones are planned before they are implemented.
Planning resolves uncertainty and produces a ready milestone.
Planning may compress analysis but must preserve resolved material decisions.
A ready milestone must be executable by the project's baseline implementation model.
Implementation begins by decomposing the ready milestone into bounded execution work packages.
AI executors persist coverage and progress in a repository-local execution ledger.
Implementation derives concrete edits from the live repository and the ready milestone.
The executor owns milestone closure, not only code production and test execution.
Validation success is evidence, not milestone completion by itself.
Distributable artifacts are validated through their intended consumer mechanism.
Documentation sync consumes deferred sync hints.
Human review gates milestone completion when automation cannot decide acceptance.
```

## Version 0.7.5

Version 0.7.5 strengthens the planning-to-implementation information boundary.

Planning now has two separate readiness obligations:

```text
decision completeness
+ decision preservation
```

Decision completeness asks whether all material architecture, semantics, compatibility, scope, acceptance, validation, human-review, ownership, integration, and project-invariant decisions required for implementation have been made.

Decision preservation asks whether the material decisions already made survived into durable implementation authority with enough precision for the baseline executor to apply them without repeating project-level reasoning.

Planning may compress investigation paths, discarded alternatives, scratch work, and speculative implementation ideas. It must not semantically weaken a resolved material decision merely to make a milestone or overlay shorter.

The durable implementation input remains:

```text
ready milestone
+ referenced project authority
+ live repository facts
```

Project-wide decisions belong in the appropriate project authority and are referenced by the milestone. Milestone-specific decisions belong in the milestone. Decision-relevant rationale or negative requirements are preserved when their omission could cause the executor to reinterpret or incorrectly generalize a settled decision.

Before `ready`, planning applies a counterfactual audit: if the planning conversation and planning model disappeared, the configured baseline executor must still be able to recover every material decision already made during planning from durable project truth without repeating project-level reasoning.

This does not require transporting the planning chain of thought or producing exhaustive implementation instructions. Local implementation mechanics remain executor-owned inside the solution space established by durable decisions.

The v0.7.3 execution-ledger/closure model and v0.7.4 consumer-surface validation model remain unchanged.

## Upgrade

From v0.7.4, use:

```text
migrations/guide-system-v0.7.4-to-v0.7.5.md
```
