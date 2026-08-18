# Changelog

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
