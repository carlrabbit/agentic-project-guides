# Agentic Project Guides

Version: 0.6.0

This repository contains a versioned guide system for creating and maintaining AI-friendly project documentation and engineering workflows.

The guide system is intentionally separate from product repositories.

Product repositories contain localized project truth. Planning, migration, documentation synchronization, and guide authoring may use this guide repository. Ordinary implementation agents work from localized repository authority documents and implementation-ready milestone packages.

## Core rule

```text
Guides live here.
Projects contain project truth.
Planning produces implementation-ready packages and execution prompts.
Implementation follows localized project authority.
Documentation sync consumes deferred sync hints.
Human review gates milestone completion when automation cannot decide acceptance.
```

## Version 0.6.0

Version 0.6.0 corrects and simplifies the human-review model.

Human review is now explicitly a milestone-scoped completion gate:

- a review belongs to one milestone;
- it evaluates evidence produced for that milestone;
- approval permits that milestone to complete;
- completed review records are immutable historical evidence;
- later commits do not make completed reviews stale;
- later milestones declare their own review requirements when needed;
- `review-check` validates one active milestone, not perpetual project-wide approval.

The review classes remain available:

- semantic;
- visual;
- UX;
- creative;
- security;
- public API;
- release;
- migration;
- artifact quality.

Ephemeral numeric aliases from v0.5.2 remain supported for interactive commands. Canonical review IDs remain the only durable identity.

## Upgrade

Use:

```text
migrations/guide-system-v0.5.2-to-v0.6.0.md
```

The migration includes correction guidance for repositories that implemented repository-wide review staleness or fingerprint revalidation.
