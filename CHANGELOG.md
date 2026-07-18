# Changelog

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
