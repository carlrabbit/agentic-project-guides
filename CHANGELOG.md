# Changelog

## 0.8.0

Migration required: recommended for repositories using integration validation, concrete project-type guidance, mixed/scoped profiles, external/runtime-bound validation, integration-first testing, or durable planning research; otherwise metadata/template review may be sufficient.

Affected areas:

- validation model and tier terminology;
- validation targets and execution loci;
- integration-ready maturity semantics;
- profile model and scoped profile composition;
- guide-profile schema version 2;
- reusable source-generator profile;
- project-local specialization;
- planning research and durable evidence;
- planning/implementation context boundary;
- .NET library test-strategy guidance;
- milestone planning/template semantics;
- bootstrap/adoption/version-migration prompts;
- platform-support guidance;
- concrete `project-types/` layer.

### Changed — validation topology

Validation depth is now independent of execution location.

Tier 2 is `standard repository validation` rather than `standard local validation`.

Tier 3 is `integration validation` rather than `PR integration validation`.

Material validation obligations may separately declare:

```text
depth
+ target
+ execution locus
+ platform/capability requirements
+ evidence
```

Local, CI, remote-service, and mixed execution are valid according to project authority. CI is not part of the generic definition of integration depth or integration-ready maturity.

### Added — validation targets and integration-bound projects

The validation model now names the real boundary being exercised as a validation target.

For external/runtime-bound validation, project authority should resolve applicable availability, locus/platform, provisioning, isolation/reset, identity, invocation, evidence, failure-semantics, fallback, release, and consumer-surface concerns.

Concrete target rules remain project-local.

### Added — integration-first policy

Projects may explicitly adopt integration-first testing.

The generic `.NET library` profile no longer assumes a test pyramid or requires unit tests as the default correctness mechanism. Unit tests remain appropriate when isolated validation is materially cheaper, more exhaustive, or more diagnostic.

### Changed — profiles and specialization

Profiles are broad reusable engineering shapes, not feature tags.

Do not create profiles merely for operating system, local/CI execution, integration-first testing, one packaging mechanism, one named external product/service, or one concrete project architecture.

`meta/SPECIALIZATION-MODEL.md` defines project-local specialization: the guide system defines reusable decision surfaces; product repositories contain the concrete answers needed by implementation.

### Added — scoped profile composition

Repositories may combine a small number of profiles when multiple broad engineering shapes genuinely apply.

Profile applicability may be repository-wide, component-scoped, or surface-scoped. Applicable obligations compose additively; profile order has no semantic meaning and no profile silently overrides another.

Material conflicts between applicable profiles must be resolved into project-local authority before implementation.

`.guide-profile.json` schema version 2 records semantic profile scopes for planning/traceability. Component and surface IDs are project-defined semantic identifiers whose meaning comes from ordinary project authority rather than path globs in metadata.

### Added — source-generator profile

0.8 adds a reusable `source-generator` profile for Roslyn source-generator/analyzer-style compile-time surfaces.

It may compose with `dotnet-library`, including in mixed package suites where only selected generator components/surfaces receive the additional source-generator obligations.

Concrete compiler/MSBuild compatibility, generated-source, diagnostic, packaging, and version-alignment rules remain project-local where project-specific.

### Added — planning research and durable evidence

`meta/RESEARCH-MODEL.md` makes research a first-class non-authoritative planning-knowledge layer.

The generic flow is:

```text
investigation/evidence
  -> durable research when future planning value justifies retention
  -> planning conclusion
  -> project authority when implementation depends on the conclusion
  -> implementation
```

Research may preserve external documentation findings, experiments, compatibility probes, historical reconstruction, comparisons, uncertainty, provenance, and revalidation triggers.

Research must not become shadow project authority. Implementation-affecting conclusions must be promoted into ordinary project authority before a ready milestone depends on them.

Planning should load research selectively. Ordinary implementation must remain executable from the ready milestone and referenced project authority without reconstructing decisions from the research corpus.

A lightweight `templates/research/research-template.md` is provided for durable investigations. Projects should not create empty research folders, indexes, or placeholder artifacts merely because the guide supports research.

Existing `docs/research/` content should be classified rather than blindly retained or deleted: useful evidence may be retained/revalidated/superseded, operative rules should be promoted, obsolete notes may be removed, and copied guide documents remain legacy guide leakage rather than project research.

### Changed — bootstrap and migration handling

`new-project.md` uses research only when bootstrap investigation produces evidence worth retaining; it does not create research scaffolding by default.

`adopt-guide-system.md` distinguishes genuine project research from copied legacy guide material and promotes any de-facto project rules before implementation handoff.

`update-guide-system.md` derives research migration semantics from the applicable version-to-version migration chain rather than hard-coding 0.8 behavior into future guide updates.

### Removed — concrete project-type catalog

The central `project-types/agentic-2d-game-engine/` guide is removed.

Concrete game-engine architecture/role/runtime rules belong in the engine repository. Reusable concepts remain covered by profiles and generic validation/engineering models.

The guide repository should not grow a parallel catalog of concrete projects or vendor integrations.

### Platform/local-first clarification

Platform support is established by declared representative validation evidence, not by CI alone.

A repository may intentionally use a Windows-local authoritative integration environment while GitHub provides portable checks, release automation, or publication.

### Migration

Use:

```text
migrations/guide-system-v0.7.5-to-v0.8.0.md
```

## 0.7.5

Migration required: recommended for repositories using disconnected planning/implementation handoff; otherwise no-op when durable implementation authority already preserves all resolved material planning decisions.

Affected areas:

- planning-to-implementation information boundary;
- decision completeness and preservation;
- ready-milestone audit;
- baseline implementation model handoff;
- guide-profile version metadata.

### Strengthened

Planning readiness now has two separate obligations:

```text
decision completeness
+ decision preservation
```

Planning may compress investigation history, rejected alternatives, and speculative implementation ideas, but must preserve every resolved material decision required by the baseline executor in durable milestone or referenced project authority.

Before `ready`, planning applies a counterfactual audit: if the planning conversation disappeared, the baseline executor must still be able to recover every material decision without repeating project-level reasoning.

The v0.7.3 execution-ledger/closure model and v0.7.4 consumer-surface validation model remain unchanged.

### Migration

Use:

```text
migrations/guide-system-v0.7.4-to-v0.7.5.md
```

## 0.7.4

Migration required: recommended for repositories that produce distributable artifacts; otherwise version-metadata-only/no-op.

Affected areas:

- validation model;
- distributable artifact acceptance;
- milestone validation template;
- guide-profile version metadata.

### Added

Distributable artifacts now require representative consumer-surface validation through their intended consumption mechanism.

Testing only source projects, internal assemblies, command handlers, unpackaged executables, or successful packaging is not sufficient to prove the distributable boundary.

The generic rule is:

```text
build/package current artifact
-> consume/install/publish through intended mechanism
-> exercise representative public behavior
```

Specific guidance now covers:

- NuGet libraries consumed from the current packed package by an isolated consumer;
- `dotnet tool` packages installed from the current local package through `dotnet tool` and invoked through the installed command/shim;
- standalone executables invoked from the current published/package artifact.

For `dotnet tool`, packaged-tool acceptance should normally prove installation, command resolution, representative successful behavior, applicable failure/exit semantics, and absence of repository-relative/global-install assumptions.

Consumer-surface acceptance should remain small and representative. Detailed behavior continues to belong primarily in lower-level tests.

### Clarified

- consumer-surface validation uses the artifact produced by the current build;
- validation must avoid accidental reliance on globally installed, stale, cached, or repository-internal substitutes;
- milestones that materially affect a distributable surface must include the applicable artifact-level validation gate;
- this is a validation capability, not a new project type, lifecycle phase, or engineering-command requirement.

### Migration

Use:

```text
migrations/guide-system-v0.7.3-to-v0.7.4.md
```

## 0.7.3

Migration required: recommended for repositories using AI-executed coding milestones; otherwise no-op for workflows that do not use the canonical AI implementation prompt.

Affected areas:

- implementation execution shape;
- baseline execution tractability;
- persistent implementation progress;
- final completion reconciliation;
- canonical planning and execution prompts;
- milestone execution model and template;
- planning-to-implementation handoff;
- guide-profile version metadata.

### Corrected

The v0.7.1 completion audit made milestone closure the executor objective, but long runs could still rely too heavily on conversational working memory until the final audit.

v0.7.3 makes requirement coverage and implementation progress explicit throughout execution rather than reconstructing them retrospectively after implementation and validation.

### Added

AI-executed coding milestones now begin with implementation-owned execution decomposition.

Before production edits, the executor creates or reconciles:

```text
.execution/<milestone-id>.md
```

The execution ledger maps milestone obligations and acceptance criteria to bounded work packages, tracks progress, records required validation, and stores concrete evidence/resume state.

A small milestone may use one work package. AI executors do not skip the ledger merely because work appears simple.

The ledger is operational implementation state, not project authority. It cannot amend or reinterpret the ready milestone.

After each coherent work package and relevant validation, the executor updates the ledger.

On context compaction, interruption, or resume, the executor rereads the milestone and ledger before continuing.

### Strengthened completion

Before `COMPLETE`, the executor must freshly reread the primary milestone from disk and reconcile:

```text
milestone obligations
<-> execution ledger
<-> live repository and concrete evidence
```

A checked ledger row is not proof by itself. Unsupported or stale completion claims must be reopened and resolved.

The existing completion audit and terminal outcomes remain in force after this reconciliation.

### Planning and readiness

Baseline-model readiness now includes execution tractability in addition to decision completeness.

Large coherent milestones may remain single semantic milestones when:

- material project-level decisions are settled;
- obligations are explicit and observable;
- implementation can derive bounded coherent work packages without reopening planning;
- long-running progress can be recovered from repository-local operational state;
- validation/evidence can establish completion reliably.

Planning does not pre-author the execution ledger or detailed implementation task list.

### Handoff cleanup

Planning must not generate bespoke per-milestone `EXECUTE-Mxxx.md` or equivalent files that duplicate the canonical execution prompt, milestone acceptance criteria, or referenced project authority.

The normal disconnected handoff is the ready milestone plus referenced authority and the stable `templates/prompts/execute-milestone.md` methodology. Overlay application instructions and a concise milestone-path handoff remain valid transport artifacts.

### Not added

v0.7.3 does not add:

- a new durable milestone lifecycle phase;
- generic milestone/ledger/checklist engineering commands;
- model-strength execution tiers;
- planner-authored line-by-line implementation plans.

### Migration

Use:

```text
migrations/guide-system-v0.7.2-to-v0.7.3.md
```

## 0.7.2

Migration required: recommended for repositories using AI implementation agents; otherwise no-op when existing milestone planning already guarantees baseline-model executability.

Affected areas:

- `ready` milestone semantics;
- planning responsibility;
- baseline implementation model metadata;
- canonical planning prompt;
- milestone template;
- milestone execution model;
- prompt index;
- guide-profile version metadata.

### Added

Milestone readiness now includes a baseline-executability requirement.

For the default ChatGPT-focused guide profile, the baseline implementation model is GPT-5.6 Luna.

Planning must make the milestone executable by the configured baseline implementation model without requiring that executor to invent a new material decision about:

- architecture;
- semantics or behavior;
- compatibility;
- scope or non-goals;
- acceptance criteria;
- validation policy;
- human-review policy;
- project-level invariants.

The baseline model is planning metadata. Ordinary implementation agents still work from the ready milestone and referenced project authority rather than `.guide-profile.json`.

### Clarified

- difficult project-level reasoning belongs in planning;
- a stronger implementation model is not the normal remedy for an under-specified milestone;
- `strong`, `frontier`, and similar model-capability execution tiers are not part of the generic guide model;
- execution profiles continue to describe autonomy and review expectations rather than model strength;
- baseline executability requires decision completeness, not line-by-line implementation prescription;
- large coherent milestones remain valid when decisions are settled and execution or validation can be bounded or resumed;
- if material decisions require new evidence, planning may create a diagnostic milestone first and then return to planning for the final implementation milestone.

### Retained

The v0.7.1 execution contract remains unchanged:

```text
implement -> validate -> completion audit -> continue or terminate
```

Implementation still terminates only as:

- `COMPLETE`;
- `AWAITING HUMAN REVIEW`;
- `BLOCKED`.

The milestone-scoped human-review model and ephemeral interactive review aliases remain unchanged.

### Migration

Use:

```text
migrations/guide-system-v0.7.1-to-v0.7.2.md
```

## 0.7.1

Migration required: recommended for repositories using AI or disconnected implementation agents; otherwise no-op.

Affected areas:

- milestone execution objective;
- completion audit;
- terminal execution outcomes;
- executor scope and reading boundaries;
- canonical execution prompt;
- milestone execution model;
- guide-profile version metadata.

### Corrected

The implementation agent now owns milestone closure, not only implementation and validation.

Execution follows:

```text
implement -> validate -> completion audit -> continue or terminate
```

Passing tests, successful compilation, or completion of listed focus areas is not sufficient by itself to claim milestone completion.

The executor must continue resolving every unsatisfied milestone obligation that is agent-resolvable in the current execution context.

### Added

A mandatory completion audit checks all applicable milestone obligations, including:

- goal and target state;
- acceptance criteria;
- required validation and evidence;
- required artifacts or generated outputs;
- direct documentation obligations;
- migrations, cleanup, and compatibility work;
- human-review gates;
- constraints and invariants;
- supporting work discovered during implementation that is necessary for completion.

Implementation runs terminate only as:

- `COMPLETE`;
- `AWAITING HUMAN REVIEW`;
- `BLOCKED`.

`COMPLETE` requires actual milestone completion, not merely implementation or validation success.

`BLOCKED` is intentionally narrow and is not used for work the agent can continue fixing itself.

### Clarified

- implementation success, validation success, and milestone completion are distinct concepts;
- scope guardrails prohibit unrelated product expansion but permit supporting work necessary to satisfy the milestone contract;
- focus areas and workstreams are guidance rather than edit allowlists unless explicitly contractual;
- implementation may inspect additional repository-local material when necessary to implement or prove a milestone requirement;
- `AWAITING HUMAN REVIEW` and `BLOCKED` are terminal outcomes for the current execution run, not new durable milestone lifecycle states.

### Not added

v0.7.1 does not add generic `milestone-show`, `milestone-check`, or `milestone-complete` engineering commands. Closure remains part of the executor contract and may use repository-specific commands when they already exist.

### Migration

Use:

```text
migrations/guide-system-v0.7.0-to-v0.7.1.md
```

## 0.7.0

Migration required: recommended for repositories using milestone-driven coding workflows; otherwise no-op.

Affected areas:

- milestone lifecycle;
- planning/implementation boundary;
- milestone template;
- canonical planning and execution prompts;
- prompt directory structure;
- meta-guide and migration terminology;
- migration guidance.

### Changed

Coding milestones now have an explicit two-phase lifecycle:

```text
draft/planning -> ready -> implementing -> done
```

Planning resolves material architectural, semantic, compatibility, scope, acceptance, and validation uncertainty.

Implementation begins from a ready milestone, re-inspects the live repository, derives concrete implementation mechanics, implements, tests, and validates.

Execution profile is orthogonal to lifecycle phase. The guide system does not encode particular model tiers as durable execution modes.

Migration, documentation synchronization, and release readiness are workflow types, not execution modes.

### Simplified

The generic milestone contract now emphasizes:

- goal and target state;
- scope and non-goals;
- resolved decisions and constraints;
- required project authority;
- acceptance criteria;
- validation;
- milestone-owned human review when applicable;
- an explicit escalation boundary.

Exhaustive file lists, predicted class changes, and detailed edit sequences are no longer generic milestone requirements unless they are themselves contractually significant.

The normal prompt surface is now:

```text
templates/prompts/
  plan-milestone.md
  execute-milestone.md
  new-project.md
  adopt-guide-system.md
  update-guide-system.md
  special/
  version-specific/
```

For normal development, use `plan-milestone.md` followed by `execute-milestone.md`.

The old human-led, AI-assisted, broad-AI, and AI-executed-human-reviewed planning prompt variants are no longer separate user-facing entry points. Execution profile is selected during planning.

Special planning workflows live under `templates/prompts/special/`. Historical and exact-target migration/repair prompts live under `templates/prompts/version-specific/`.

### Handoff model

The ready milestone plus referenced project authority is the durable planning-to-implementation handoff.

`templates/prompts/execute-milestone.md` is the canonical execution methodology. Planning may provide a concise handoff note or overlay application instructions, but it does not need to regenerate a bespoke execution prompt for each milestone.

### Added

- explicit `ready` milestone semantics;
- implementation ownership of local code/test mechanics;
- return-to-planning behavior for material unresolved decisions;
- `migrations/guide-system-v0.6.0-to-v0.7.0.md`.

### Retained

- external guide authority and localized project truth;
- existing execution profiles;
- deferred documentation synchronization;
- milestone-scoped human review;
- constrained execution and resumable validation.

## 0.6.0

Migration required: conditional.

Affected areas:

- human-review model;
- milestone completion gates;
- review request and record templates;
- review command semantics;
- milestone planning prompts;
- implementation execution prompts;
- validation guidance.

### Changed

Human review is now milestone-scoped.

A review answers:

```text
Was the evidence produced for this milestone acceptable when the milestone completed?
```

It does not establish ongoing project-wide approval.

Approved review records:

- remain historical evidence;
- do not become stale after later commits;
- are not revalidated against future repository state;
- do not require repeated human approval.

`review-check` now validates required reviews for a named active milestone.

### Retained

- review classes;
- repository-local `.review/` state;
- canonical review IDs;
- ephemeral numeric aliases for interactive use;
- thin `eng/` launchers over shared tested implementation;
- constrained-execution and resumable-validation models.

### Removed from the generic model

- perpetual approval validity;
- repository-wide fingerprint-based review staleness;
- re-review triggers caused by later unrelated commits;
- treating historical approvals as current project quality gates;
- requiring completed reviews to be reopened after subsequent work.

### Conditional migration

Repositories that already implemented the previous review model should:

- bind every pending review to one active milestone;
- stop invalidating approved records because repository state changed;
- change `review-check` to require `--milestone <id>` or an equivalent explicit milestone context;
- preserve completed records as historical evidence;
- remove generic stale/re-review behavior from review commands and templates;
- decide how to classify legacy pending requests that do not identify a milestone.

### No-op

Repositories that do not use human review require no product-repository change.

## 0.5.2

Added ephemeral numeric aliases for interactive human-review commands while retaining canonical review IDs as durable identity.

## 0.5.1

Restored full operational prompt templates after abbreviated replacements were introduced in v0.5.0.

## 0.5.0

Added constrained agent execution and resumable validation suites.

## 0.4.0

Added repository-local human review and cross-platform engineering command architecture.
