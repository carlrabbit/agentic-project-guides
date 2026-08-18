# Milestone Execution Model

## Status

Authoritative for milestone lifecycle, execution profiles, planning/implementation separation, workflow classification, baseline-executor readiness, execution completion, and milestone completion gates.

## Milestone lifecycle

Coding milestones use two explicit work phases:

```text
draft/planning -> ready -> implementing -> done
```

`draft/planning` means material implementation-affecting uncertainty may still exist.

`ready` means planning has resolved the decisions that would materially change architecture, semantics, compatibility, scope, acceptance, or validation, and has established that the project's baseline implementation model can execute the milestone without making a new material project-level decision. The milestone is a self-contained implementation contract together with the project authority it references.

`implementing` means the executor may determine concrete implementation mechanics from the live repository but must not silently change resolved milestone decisions.

`done` means the milestone acceptance and completion gates have been satisfied.

If implementation discovers an unresolved decision that could materially alter architecture, semantics, compatibility, scope, acceptance, or validation, stop the affected work and return that decision to planning. Local implementation choices that do not alter those boundaries remain implementation-owned.

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
- known exceptional implementation constraints;
- baseline-executor readiness.

Planning may create or update project-truth documents when a decision must become durable authority before implementation.

Detailed file lists, class designs, edit sequences, and speculative implementation steps are not required unless they are themselves part of the architectural or compatibility contract.

If a milestone uses focus areas, workstreams, or similar decomposition, those describe expected concentration of work. They are not an exhaustive edit allowlist unless the milestone explicitly makes them contractual.

## Baseline implementation model and `ready` boundary

Each project may define a baseline implementation model as planning metadata.

The default ChatGPT-focused guide profile uses:

```text
GPT-5.6 Luna
```

Projects may intentionally configure another baseline implementation model. The guide does not require every project to use the same model.

The baseline implementation model is not a per-milestone capability tier. It is the normal executor that planning targets when deciding whether a milestone is ready.

A milestone is baseline-executable when the configured baseline implementation model can use the ready milestone, referenced project authority, live repository, and normal repository tooling to complete the work without inventing a new material decision about:

- architecture;
- semantics or behavior;
- public or persisted compatibility;
- scope or non-goals;
- acceptance criteria;
- validation policy;
- human-review policy;
- project-level invariants.

Planning owns the reasoning needed to reach that state.

Do not compensate for incomplete planning by selecting a `strong`, `frontier`, or similar stronger implementation tier. Such capability tiers are not part of the generic execution model.

Do not compensate by turning the milestone into a line-by-line patch plan. Baseline executability requires decision completeness and observable completion criteria, not pre-implementation of local mechanics in prose.

If a material decision cannot be resolved until more evidence exists, planning should define a focused diagnostic or investigation milestone whose target state is the required evidence. After that evidence exists, return to planning and produce or revise the final implementation milestone.

Baseline executability does not imply that milestones must be small. Large coherent migrations, transformations, or cross-cutting implementations may be ready when:

- project-level decisions are settled;
- boundaries and invariants are explicit;
- remaining implementation choices are local mechanics;
- long-running work can be bounded, sharded, or resumed where necessary;
- validation gives reliable completion evidence.

Execution volume and reasoning uncertainty are different concerns. Use constrained-execution and resumable-validation mechanisms for volume; use planning for unresolved project-level reasoning.

The baseline model may still discover unexpected repository facts during implementation. If those facts can be handled through local mechanics within the ready contract, implementation continues. If they expose a material unresolved decision, the affected work returns to planning.

Ordinary implementation agents do not need to read `.guide-profile.json` to discover the baseline model. Planning uses that metadata to establish readiness; the ready milestone and referenced project authority remain the implementation contract.

## Implementation phase

Implementation begins only from a ready milestone.

The executor's objective is to drive the milestone to a valid terminal execution outcome, not merely to produce code or pass tests.

The executor:

- starts with the milestone and explicitly required project authority;
- inspects the live source and tests needed for the change;
- may inspect additional repository-local material needed to implement or prove a milestone obligation;
- derives the concrete implementation plan;
- follows established repository patterns where the milestone leaves implementation freedom;
- performs all implementation and supporting work required by the milestone contract;
- avoids unrelated product expansion;
- runs the specified validation and fixes agent-resolvable failures;
- produces required evidence and artifacts;
- performs a mandatory completion audit;
- continues working while any unsatisfied milestone obligation is agent-resolvable.

The executor does not need the planning conversation, external guide repository, rejected alternatives, or planning-agent scratch work.

The instruction to remain within milestone scope forbids unrelated expansion. It does not forbid supporting edits necessary to satisfy the milestone goal, target state, acceptance criteria, validation, documentation, artifact, migration, cleanup, or review obligations.

## Execution loop

Implementation follows this loop:

```text
implement
  -> validate
  -> completion audit
  -> fix every agent-resolvable gap
  -> repeat as needed
  -> terminal execution outcome
```

Tests and automated checks are evidence used by the completion audit. They are not a substitute for it.

A successful build or test suite must not become an implicit stopping condition when other milestone obligations remain unsatisfied.

## Completion audit

Before terminating an implementation run, the executor must audit all applicable milestone obligations, including:

- goal;
- target state;
- scope-required behavior;
- every acceptance criterion;
- required validation and evidence;
- required artifacts or generated outputs;
- direct documentation obligations;
- required migrations, cleanup, or compatibility work;
- human-review gates;
- constraints and invariants;
- supporting work discovered during implementation that is necessary for completion.

If an unsatisfied obligation can be resolved in the current execution context without changing the ready milestone contract, implementation continues.

If a required human decision is the only remaining gate, execution terminates as `AWAITING HUMAN REVIEW`.

If completion requires unavailable external capability or a material planning decision the executor is not authorized to make, execution terminates as `BLOCKED` with the exact dependency or decision identified.

## Success semantics

Implementation success, validation success, and milestone completion are distinct:

| Concept | Meaning |
|---|---|
| Implementation success | The intended implementation exists. |
| Validation success | The required automated checks pass. |
| Milestone completion | Every applicable milestone obligation and completion gate is satisfied. |

Implementation success does not imply validation success.

Validation success does not imply milestone completion.

Only milestone completion permits the milestone to transition to `done`.

## Terminal execution outcomes

An implementation run terminates only with one of these outcomes:

### `COMPLETE`

All applicable milestone obligations are satisfied and no blocking review or external dependency remains.

The milestone may transition to `done`.

### `AWAITING HUMAN REVIEW`

All implementation and other agent-resolvable completion work is complete, but a required human review decision remains.

The milestone remains active until the review gate is resolved.

### `BLOCKED`

Completion requires something the implementation agent cannot resolve in the current execution context.

Examples include:

- unavailable credentials or permissions;
- unavailable required infrastructure or external services;
- inaccessible required dependencies or artifacts;
- a material architectural, semantic, compatibility, scope, acceptance, or validation decision that must return to planning.

Ordinary implementation work, failing tests, missing documentation, incomplete artifacts, or other agent-resolvable obligations are not blockers.

These are terminal outcomes for the current implementation run, not additional durable milestone lifecycle states. `AWAITING HUMAN REVIEW` and `BLOCKED` leave the milestone active.

## Execution profiles

Execution profile is orthogonal to lifecycle phase and describes who or what performs implementation and with what autonomy or review expectations.

| Profile | Meaning |
|---|---|
| `human-led` | Human actively drives implementation decisions. |
| `ai-assisted` | Human implements or steers; AI assists. |
| `ai-executed-human-reviewed` | AI performs implementation; human reviews declared milestone evidence. |
| `ai-executed-broad` | AI performs a larger coherent implementation with strong autonomy and validation. |

A repository may use different humans, models, tools, or interfaces for planning and implementation without changing the milestone contract.

Execution profiles do not encode model strength. In particular, the generic guide does not add `strong` or `frontier` execution profiles. Baseline-model readiness is decided during planning before any AI-executed milestone becomes `ready`.

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
- required artifact production;
- direct documentation obligations;
- human review of milestone evidence.

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
