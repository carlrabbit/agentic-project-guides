# Milestone Execution Model

## Status

Authoritative for milestone lifecycle, execution profiles, planning/implementation separation, workflow classification, and milestone completion gates.

## Milestone lifecycle

Coding milestones use two explicit work phases:

```text
draft/planning -> ready -> implementing -> done
```

`draft/planning` means material implementation-affecting uncertainty may still exist.

`ready` means planning has resolved the decisions that would materially change architecture, semantics, compatibility, scope, acceptance, or validation. The milestone is a self-contained implementation contract together with the project authority it references.

`implementing` means the executor may determine concrete implementation mechanics from the live repository but must not silently change resolved milestone decisions.

`done` means the milestone acceptance and completion gates have been satisfied.

If implementation discovers an unresolved decision that could materially alter architecture, semantics, compatibility, scope, acceptance, or validation, stop and return the milestone to planning. Local implementation choices that do not alter those boundaries remain implementation-owned.

## Planning phase

Planning reduces uncertainty. It should inspect enough repository truth to make the milestone safe to execute, but it should not predict implementation mechanics that the executor can derive reliably from the live repository.

A ready milestone defines, as applicable:

- goal and target state;
- scope and non-goals;
- resolved decisions;
- implementation constraints and invariants;
- required authority documents;
- acceptance criteria;
- validation commands and validation execution mode;
- direct documentation impact;
- deferred documentation synchronization;
- human-review gates;
- known exceptional implementation constraints.

Planning may create or update project-truth documents when a decision must become durable authority before implementation.

Detailed file lists, class designs, edit sequences, and speculative implementation steps are not required unless they are themselves part of the architectural or compatibility contract.

## Implementation phase

Implementation begins only from a ready milestone.

The executor:

- reads the milestone and explicitly required project authority;
- inspects the live source and tests needed for the change;
- derives the concrete implementation plan;
- follows established repository patterns where the milestone leaves implementation freedom;
- implements the smallest coherent change satisfying the target state;
- runs the specified validation and fixes attributable failures;
- produces required evidence and completion reporting.

The executor does not need the planning conversation, external guide repository, rejected alternatives, or planning-agent scratch work.

## Execution profiles

Execution profile is orthogonal to lifecycle phase and describes who or what performs implementation and with what autonomy or review expectations.

| Profile | Meaning |
|---|---|
| `human-led` | Human actively drives implementation decisions. |
| `ai-assisted` | Human implements or steers; AI assists. |
| `ai-executed-human-reviewed` | AI performs implementation; human reviews declared milestone evidence. |
| `ai-executed-broad` | AI performs a larger coherent implementation with strong autonomy and validation. |

A repository may use different humans, models, tools, or interfaces for planning and implementation without changing the milestone contract.

## Workflow types

Workflow type describes the kind of work being planned. It is separate from lifecycle phase and execution profile.

Examples include:

- ordinary product or library milestone work;
- engineering migration;
- documentation synchronization;
- release readiness.

Special workflow types may use dedicated planning prompts because they have different authority, scope, or completion semantics. When they result in coding or repository changes, they still converge on the same ready-milestone boundary and use the canonical implementation phase unless their workflow explicitly requires a different executor contract.

## Validation execution mode

Validation execution mode describes how required validation runs, for example:

- direct;
- resumable-sharded;
- CI-only;
- human-review-gated.

Validation execution mode must not be confused with execution profile or workflow type.

## Milestone completion

A milestone defines its own completion gates.

Possible gates include:

- focused automated validation;
- standard local validation;
- PR integration validation;
- release validation;
- human review of milestone evidence;
- documentation directly required for implementation correctness.

Human review is not inherited indefinitely by the project.

When a milestone requires human review, it must define:

- review class;
- applicability: recommended, required, or blocking;
- canonical review ID or allocation rule;
- review subject;
- evidence to be produced;
- acceptance criteria;
- human reviewer role when relevant;
- completion behavior;
- waiver policy when applicable.

After the milestone completes, its review records are historical evidence. Future milestones decide independently whether new review is required.
