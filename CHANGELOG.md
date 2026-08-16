# Changelog

## 0.7.0

Migration required: recommended for repositories using milestone-driven coding workflows; otherwise no-op.

Affected areas:

- milestone lifecycle;
- planning/implementation boundary;
- milestone template;
- implementation execution prompt;
- meta-guide doctrine;
- prompt guidance.

### Changed

Coding milestones now have an explicit two-phase lifecycle:

```text
draft/planning -> ready -> implementing -> done
```

Planning resolves material architectural, semantic, compatibility, scope, acceptance, and validation uncertainty.

Implementation begins from a ready milestone, re-inspects the live repository, derives concrete implementation mechanics, implements, tests, and validates.

Execution mode is orthogonal to lifecycle phase. The guide system does not encode particular model tiers as durable execution modes.

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

### Added

- explicit `ready` milestone semantics;
- implementation ownership of local code/test mechanics;
- return-to-planning behavior for material unresolved decisions;
- `migrations/guide-system-v0.6.0-to-v0.7.0.md`.

### Retained

- external guide authority and localized project truth;
- existing execution modes;
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
