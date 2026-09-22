# Milestone Execution Model

## Status

Authoritative for milestone lifecycle, execution profiles, planning/implementation separation, workflow classification, baseline-executor readiness, execution tractability, persistent execution state, execution completion, and milestone completion gates.

## Milestone lifecycle

Coding milestones use two explicit work phases:

```text
draft/planning -> ready -> implementing -> done
```

`draft/planning` means material implementation-affecting uncertainty may still exist.

`ready` means planning has resolved the decisions that would materially change architecture, semantics, compatibility, scope, acceptance, or validation, and has established that the project's baseline implementation model can execute the milestone without making a new material project-level decision. The milestone is a self-contained implementation contract together with the project authority it references.

`implementing` means the executor may determine concrete implementation mechanics from the live repository but must not silently change resolved milestone decisions. For AI-executed milestones, implementation includes execution decomposition and persistent repository-local progress state.

`done` means the milestone acceptance and completion gates have been satisfied.

If implementation discovers an unresolved decision that could materially alter architecture, semantics, compatibility, scope, acceptance, validation, or a required project specialization, stop the affected work and return that decision to planning. Local implementation choices that do not alter those boundaries remain implementation-owned.

## Planning phase

Planning reduces uncertainty. It should inspect enough repository truth and relevant planning knowledge to make the milestone safe to execute, but it should not predict implementation mechanics that the executor can derive reliably from the live repository.

A ready milestone defines, as applicable:

- goal and target state;
- scope and non-goals;
- resolved decisions;
- implementation constraints and invariants;
- required authority documents;
- acceptance criteria;
- validation depth, targets, execution loci, platform/capability requirements, commands, and evidence;
- direct documentation impact;
- deferred documentation synchronization;
- human-review gates;
- known exceptional implementation constraints;
- baseline-executor readiness.

Planning may create or update project-truth documents when a decision must become durable authority before implementation. This includes project-local specialization for concrete external runtimes, services, platforms, test environments, packaging boundaries, or domain architecture when generic guide guidance is insufficient.

Planning may also inspect, create, revalidate, supersede, or remove non-authoritative research according to `meta/RESEARCH-MODEL.md`.

Research preserves reusable evidence and investigation context, not operative project rules. Every research-derived conclusion required by ordinary implementation must be promoted into the ready milestone or referenced project authority before the milestone becomes `ready`.

Detailed file lists, class designs, edit sequences, and speculative implementation steps are not required unless they are themselves part of the architectural or compatibility contract.

If a milestone uses focus areas, workstreams, or similar decomposition, those describe expected concentration of work. They are not an exhaustive edit allowlist unless the milestone explicitly makes them contractual.

Planning must structure acceptance criteria and completion obligations clearly enough that implementation can map them to concrete execution work and evidence.

For AI-executed milestones, planning also assigns stable identities to every individually verifiable acceptance criterion and material completion obligation, then initializes the execution ledger with those obligations as separate pending rows and with the required validation gates.

Planning seeds coverage structure, not implementation decomposition. It does not pre-author the executor's local task list, work packages, concrete implementation mapping, evidence, or completion state.

The execution ledger may compress work. It must not compress obligations.

## Acceptance evidence topology

Lossless obligation tracking prevents an executor from dropping requirements, but a single obligation can still hide materially distinct behavioral paths.

Planning must therefore ask, for each acceptance/completion obligation:

> Does this obligation cover more than one materially distinct implementation path, state mechanism, compatibility surface, dispatch path, target surface, or failure behavior such that evidence for one path would not establish the others?

When the answer is yes, planning defines explicit evidence cases with stable IDs such as `EC-01a`, `EC-01b`, and seeds them into the execution ledger.

Examples may include:

- scalar versus enum generation when they use different dispatch paths;
- Root versus Batch state scopes;
- inherited versus directly declared behavior;
- source-project versus packed/installed consumer surfaces;
- provider-specific implementations;
- sync versus async paths;
- success behavior versus contractually distinct failure/diagnostic behavior.

Evidence cases describe what must be proven, not how to write the implementation or tests.

Do not generate the full Cartesian product of every possible dimension. Add a separate evidence case only when the distinction is materially capable of hiding a different implementation defect or contract failure.

If an obligation has no materially distinct proof paths, the obligation itself remains the evidence unit.

For AI-executed milestones, planning seeds the evidence-case registry before `ready`. Implementation may choose the concrete test structure and validation mechanics, but it cannot replace several required evidence cases with one aggregate claim.

## Research and diagnostic work

If a material planning decision cannot be resolved from current project authority and existing current evidence, planning may perform research directly or define a focused diagnostic/investigation milestone whose target state is the required evidence.

Durable research is justified only when the evidence is useful to future planning and would be expensive, unreliable, or wasteful to rediscover.

A diagnostic/investigation milestone should define the question, evidence to obtain, relevant environment/version constraints, and observable completion condition without pre-deciding the result.

After the evidence exists, planning should:

1. persist reusable research when justified;
2. re-evaluate the material decision;
3. promote any implementation-affecting conclusion into project authority;
4. create or revise the actual implementation milestone.

The guide does not define a generic persistent planning ledger. Research stores reusable evidence; ready milestones and project authority store resolved decisions; conversational scratch reasoning remains disposable.

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
- validation policy, target, or required execution topology;
- human-review policy;
- project-level invariants.

Planning owns the reasoning needed to reach that state.

The implementation contract must remain complete without requiring the executor to reconstruct planning decisions from `docs/research/`, planning chat history, or guide metadata.

Do not compensate for incomplete planning by selecting a `strong`, `frontier`, or similar stronger implementation tier. Such capability tiers are not part of the generic execution model.

Do not compensate by turning the milestone into a line-by-line patch plan. Baseline executability requires decision completeness and observable completion criteria, not pre-implementation of local mechanics in prose.

If a material decision cannot be resolved until more evidence exists, planning should define a focused diagnostic or investigation milestone whose target state is the required evidence. After that evidence exists, return to planning and produce or revise the final implementation milestone.

Baseline executability does not imply that milestones must be small. Large coherent migrations, transformations, or cross-cutting implementations may be ready when:

- project-level decisions are settled;
- boundaries and invariants are explicit;
- remaining implementation choices are local mechanics;
- milestone obligations can be mapped during implementation into bounded coherent work packages;
- long-running implementation can recover from repository-local execution state rather than depending on conversational memory;
- long-running validation can be bounded, sharded, or resumed where necessary;
- validation gives reliable completion evidence.

Execution volume and reasoning uncertainty are different concerns. Use planning for unresolved project-level reasoning. Use execution decomposition and persistent execution state for long implementation volume. Use constrained-execution and resumable-validation mechanisms for long validation volume.

The baseline model may still discover unexpected repository facts during implementation. If those facts can be handled through local mechanics within the ready contract, implementation continues. If they expose a material unresolved decision, the affected work returns to planning.

Ordinary implementation agents do not need to read `.guide-profile.json` to discover the baseline model. Planning uses that metadata to establish readiness; the ready milestone and referenced project authority remain the implementation contract.

## Execution tractability

Decision completeness is necessary but not sufficient for reliable AI execution.

Planning must also establish that the milestone's implementation volume is tractable for the baseline executor. A milestone is execution-tractable when:

- its obligations are explicit, observable, and individually identifiable where they can be verified independently;
- planning has seeded a lossless obligation registry for AI-executed milestones;
- planning has identified and seeded materially distinct evidence cases where one obligation needs independent proof across heterogeneous paths;
- implementation can group obligations into bounded coherent work packages without making new project-level decisions or replacing several obligations/evidence cases with a broad summary;
- work-package progress can be externalized into repository-local operational state;
- implementation and validation evidence can be associated with each specific applicable obligation and evidence case;
- an interrupted or compacted implementation session can reconstruct current execution state from the milestone, planning-seeded ledger, repository, and evidence.

Execution tractability does not require planning to predict the concrete work-package decomposition. That decomposition belongs to implementation because it depends on the live repository and local mechanics.

A large milestone should be split into multiple milestones when it is semantically incoherent, has independently valuable target states, or contains unresolved decisions that should be planned separately. It should not be split merely to compensate for the absence of persistent implementation state.

## Implementation phase

Implementation begins only from a ready milestone.

The executor's objective is to drive the milestone to a valid terminal execution outcome, not merely to produce code or pass tests.

The executor:

- starts with the milestone and explicitly required project authority;
- inspects the live source and tests needed for the change;
- may inspect additional repository-local material needed to implement or prove a milestone obligation;
- treats `docs/research/` as non-authoritative and reads it only when explicitly relevant to an investigation/evidence obligation or referenced evidence;
- derives concrete execution work packages and implementation mechanics;
- reads and reconciles the planning-seeded obligation registry, then extends the ledger with work-package mappings, evidence, status, and resume state for AI-executed milestones;
- follows established repository patterns where the milestone leaves implementation freedom;
- performs all implementation and supporting work required by the milestone contract;
- avoids unrelated product expansion;
- runs the specified validation in the declared target/locus topology and fixes agent-resolvable failures;
- produces required evidence and artifacts;
- freshly reconciles milestone obligations against execution state and repository evidence before completion;
- performs a mandatory completion audit;
- continues working while any unsatisfied milestone obligation is agent-resolvable.

The executor does not need the planning conversation, external guide repository, rejected alternatives, planning-agent scratch work, or research corpus to recover the project contract.

Ordinary implementation should not create research merely to record reasoning or discoveries. When a milestone explicitly assigns investigation/evidence preservation, the executor may create or update research, but research cannot amend project authority. Material decisions exposed by the evidence return to planning.

The instruction to remain within milestone scope forbids unrelated expansion. It does not forbid supporting edits necessary to satisfy the milestone goal, target state, acceptance criteria, validation, documentation, artifact, migration, cleanup, or review obligations.

## Execution decomposition

For AI-executed coding milestones, implementation has two internal stages without adding a new durable lifecycle phase.

Stage 1 is execution decomposition. Before production edits, the executor:

1. rereads the ready milestone, required authority, and planning-seeded `.execution/<milestone-id>.md`;
2. enumerates the milestone's applicable obligation IDs and verifies exact set equality with the seeded obligation registry;
3. verifies that no planner-seeded obligation row was merged, deleted, renumbered, paraphrased, or replaced by a broader summary;
4. inspects enough live repository state to locate implementation surfaces;
5. maps every applicable obligation row to at least one bounded work package or explicit gate while preserving the individual row;
6. maps required validation to the specific obligation IDs it actually exercises;
7. verifies that no work package requires reopening a settled material decision.

If a legacy or externally prepared milestone has no seeded ledger, the executor may initialize one from the milestone before implementation, but it must preserve every applicable obligation individually. A material ambiguity in the milestone contract returns to planning.

Stage 2 is iterative implementation of those work packages.

Execution decomposition may choose files, types, tests, refactorings, local sequencing, and other implementation mechanics. It must not amend architecture, semantics, compatibility, scope, acceptance, validation policy, required validation target/locus, project specialization, or human-review policy already settled by planning.

A small milestone may consist of one work package. AI-executed milestones do not skip persistent execution state merely because the work initially appears simple.

## Persistent execution ledger

The canonical repository-local ledger path is:

```text
.execution/<milestone-id>.md
```

The ledger is mutable operational state, not project authority. The milestone remains authoritative if the two disagree.

For AI-executed milestones, planning creates the initial ledger before the milestone becomes `ready`.

Planning owns the seeded coverage structure:

- primary milestone path;
- stable obligation IDs;
- one separate row for every individually verifiable acceptance criterion and material completion obligation;
- the obligation type and wording mirrored from the milestone;
- required evidence-case IDs for materially distinct proof paths;
- required validation-gate IDs, target/locus, and the obligation/evidence-case IDs each gate is intended to prove.

Implementation owns the evolving execution state:

- bounded work packages and their mapping to obligation IDs;
- implementation evidence;
- validation evidence actually obtained;
- obligation/work-package status;
- a concise resume point while work remains;
- agent-resolvable supporting work discovered during implementation.

Planner-seeded obligation rows are protected methodologically. Implementation must not delete, merge, renumber, paraphrase, or replace them merely to simplify execution tracking. Several obligations may map to one work package, but the obligations remain separate ledger rows.

The core invariant is:

```text
execution ledger may compress work
execution ledger must not compress obligations
```

A ledger row marked `done` is a claim about one specific obligation, not acceptance authority. Repository state and concrete evidence must independently establish that obligation.

An aggregate validation result proves only the evidence units whose required behavior the executed scenario actually exercises. When explicit evidence cases exist, those cases—not only the parent obligation—must be established. Passing a broad suite must not be used to fill evidence for behaviors that were not exercised.

The executor updates implementation-owned ledger fields after each coherent work package and relevant validation.

After context compaction, interruption, or session resume, the executor rereads the primary milestone and execution ledger before continuing and reconciles them with the live repository where necessary.

Before `COMPLETE`, the executor verifies:

```text
set(applicable milestone obligation IDs)
==
set(ledger obligation IDs)
```

and then verifies evidence for every individual applicable obligation.

When the milestone defines evidence cases, the executor also verifies exact set equality between required milestone evidence-case IDs and ledger evidence-case IDs, then verifies concrete evidence for every case.

Set equality is necessary but not sufficient; duplicate, stale, indirect-without-justification, substitute-only, neighboring-case, or merely asserted evidence does not establish completion.

The ledger is required while an AI-executed milestone is active. Retention after milestone completion is repository policy. Removing a completed ledger does not invalidate independently established milestone evidence.

No generic engineering command is required to initialize, update, check, or complete the ledger. Planning already owns the milestone obligation set and may seed the ledger directly without an intermediate parser or generator.

## Execution loop

Implementation follows this loop:

```text
read milestone, authority, and planning-seeded ledger
  -> verify lossless obligation registry
  -> execution decomposition
  -> map obligations to work packages
  -> implement coherent work package
  -> focused validation
  -> update ledger and evidence
  -> repeat as needed
  -> freshly reread milestone from disk
  -> reconcile milestone/evidence cases <-> ledger <-> repository/evidence
  -> final validation
  -> completion audit
  -> persist compact durable completion evidence
  -> terminal execution outcome
```

Tests and automated checks are evidence used by the execution ledger and completion audit. They are not substitutes for milestone reconciliation.

A successful build, test suite, or validation shard must not become an implicit stopping condition when other milestone obligations remain unsatisfied.

## Final reconciliation

Before a `COMPLETE` outcome, the executor must freshly reread the primary milestone from disk rather than relying on conversational memory or the ledger's summary.

It then reconciles:

```text
milestone obligations
<-> execution ledger
<-> live repository and concrete evidence
```

First, the executor enumerates the applicable obligation IDs from the freshly reread milestone and verifies exact set equality with the planning-seeded ledger registry. Missing, merged, duplicated, renumbered, or extra contract rows must be reconciled before completion; a material ambiguity returns to planning.

For every applicable obligation ID, the executor must then:

- identify the work package or gate that claims coverage;
- inspect the concrete implementation evidence;
- identify the validation evidence required for that specific obligation;
- when explicit evidence cases exist, enumerate and verify every required child evidence-case ID;
- verify that the executed validation actually exercises the behavior claimed by the obligation/evidence case;
- reject evidence inferred only from a neighboring criterion, sibling evidence case, different implementation path, or aggregate pass that did not exercise the required behavior.

Unsupported, stale, indirect-without-justification, substitute-only, or merely asserted `done` states must be reopened. Newly discovered agent-resolvable gaps become active execution work and the loop continues.

Final reconciliation also confirms that every required validation gate has current evidence from the required target/locus and that no agent-resolvable ledger item remains.

## Durable completion evidence

The mutable execution ledger exists to support implementation and recovery. Repository policy may remove it after milestone completion.

Before a `COMPLETE` milestone transitions to `done`, implementation must preserve a compact completion-evidence reconciliation in the milestone itself (or in another project-defined immutable completion record explicitly referenced by the milestone).

The durable record should map:

```text
obligation/evidence case
-> concrete evidence
-> validation gate/target
-> result
```

Where explicit evidence cases exist, preserve those cases individually rather than collapsing them back into the parent obligation.

The durable completion record is historical evidence. It does not amend the ready contract and must not contain work-package task lists, resume state, scratch reasoning, or the full mutable execution ledger.

This allows reviewers and later release/readiness work to inspect what proved milestone completion even when `.execution/<milestone-id>.md` is no longer retained.

## Completion audit

After final reconciliation and required validation, the executor audits all applicable milestone obligations, including:

- goal;
- target state;
- scope-required behavior;
- every acceptance criterion;
- required validation targets, loci, and evidence;
- required artifacts or generated outputs;
- direct documentation obligations;
- explicitly required research/evidence artifacts when investigation is part of the milestone;
- required migrations, cleanup, or compatibility work;
- human-review gates;
- constraints and invariants;
- supporting work discovered during implementation that is necessary for completion.

If an unsatisfied obligation can be resolved in the current execution context without changing the ready milestone contract, implementation continues and the ledger is updated.

If a required human decision is the only remaining gate, execution terminates as `AWAITING HUMAN REVIEW`.

If completion requires unavailable external capability or a material planning decision the executor is not authorized to make, execution terminates as `BLOCKED` with the exact dependency or decision identified.

## Success semantics

Implementation success, work-package completion, validation success, and milestone completion are distinct:

| Concept | Meaning |
|---|---|
| Implementation success | The intended implementation exists. |
| Work-package completion | A bounded implementation outcome and its mapped evidence are established. |
| Validation success | The required automated checks pass against the required targets/loci. |
| Milestone completion | Every applicable milestone obligation and completion gate is satisfied. |

Implementation success does not imply work-package completion.

Work-package completion does not imply aggregate validation success.

Validation success does not imply milestone completion.

Only milestone completion permits the milestone to transition to `done`.

## Terminal execution outcomes

An implementation run terminates only with one of these outcomes:

### `COMPLETE`

The milestone has been freshly reread, milestone-to-ledger-to-repository/evidence reconciliation succeeded, all applicable milestone obligations are satisfied, required validation is current, and no blocking review or external dependency remains.

The milestone may transition to `done`.

### `AWAITING HUMAN REVIEW`

All implementation and other agent-resolvable completion work is complete, but a required human review decision remains.

The milestone remains active until the review gate is resolved.

### `BLOCKED`

Completion requires something the implementation agent cannot resolve in the current execution context.

Examples include:

- unavailable credentials or permissions;
- unavailable required infrastructure, runtime, integration target, or external service;
- inaccessible required dependencies or artifacts;
- a material architectural, semantic, compatibility, scope, acceptance, validation, or specialization decision that must return to planning.

Ordinary implementation work, failing tests, missing documentation, incomplete artifacts, incomplete ledger items, or other agent-resolvable obligations are not blockers.

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

Persistent execution-ledger requirements apply to AI-executed coding milestones regardless of whether the profile is `ai-executed-human-reviewed` or `ai-executed-broad`.

## Workflow types

Workflow type describes the kind of work being planned. It is separate from lifecycle phase and execution profile.

Examples include:

- ordinary product or library milestone work;
- diagnostic/investigation work;
- engineering migration;
- documentation synchronization;
- release readiness.

Special workflow types may use dedicated planning prompts because they have different authority, scope, or completion semantics. When they result in coding or repository changes, they still converge on the same ready-milestone boundary and use the canonical implementation phase unless their workflow explicitly requires a different executor contract.

## Validation topology and execution mode

Validation topology describes what is exercised and where. It is independent of validation depth.

For each material obligation, planning may need to declare:

- validation tier/depth;
- target;
- execution locus: local, CI, remote, or mixed;
- required platform/capability;
- expected evidence.

Validation execution mode describes how a validation operation runs, for example:

- direct;
- resumable-sharded;
- human-review-gated where the final acceptance step is human.

A locus constraint such as `CI-only` or `local Windows only` is not itself a validation depth or execution profile.

Validation topology and execution mode must not be confused with implementation execution profile or workflow type.

## Milestone completion

A milestone defines its own completion gates.

Possible gates include:

- focused automated validation;
- standard repository validation;
- integration validation against declared targets;
- release/consumer validation;
- required artifact production;
- direct documentation obligations;
- explicitly assigned research/evidence production for investigation milestones;
- human review of milestone evidence.

These gates may run locally, in CI, against remote services, or through a mixed topology according to project authority.

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
