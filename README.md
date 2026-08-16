# Agentic Project Guides

Version: 0.7.0

This repository contains a versioned guide system for creating and maintaining AI-friendly project documentation and engineering workflows.

The guide system is intentionally separate from product repositories.

Product repositories contain localized project truth. Planning, migration, documentation synchronization, and guide authoring may use this guide repository. Ordinary implementation agents work from localized repository authority documents and implementation-ready milestones.

## Core rule

```text
Guides live here.
Projects contain project truth.
Milestones are planned before they are implemented.
Planning resolves uncertainty and produces a ready milestone.
Implementation derives concrete edits from the live repository and the ready milestone.
Documentation sync consumes deferred sync hints.
Human review gates milestone completion when automation cannot decide acceptance.
```

## Version 0.7.0

Version 0.7.0 makes planning and implementation explicit, separate phases of milestone work regardless of which human or model performs either phase.

The lifecycle is:

```text
draft/planning -> ready -> implementing -> done
```

Planning owns:

- repository inspection needed to understand the change;
- architectural, semantic, compatibility, and scope decisions;
- target state, constraints, non-goals, and acceptance criteria;
- required authority documents;
- validation and human-review gates.

Implementation owns:

- inspection of the live source and tests needed to perform the change;
- concrete file, type, function, and refactoring choices not fixed by planning;
- implementation, testing, iteration, and evidence production.

An implementation agent must not reconstruct or silently reopen resolved planning decisions. If implementation discovers a material unresolved architectural, semantic, compatibility, or scope decision, the milestone returns to planning rather than allowing the implementation phase to invent new project policy.

Execution modes such as `human-led`, `ai-assisted`, and `ai-executed-human-reviewed` remain available and are orthogonal to lifecycle phase.

## Upgrade

Use:

```text
migrations/guide-system-v0.6.0-to-v0.7.0.md
```

The migration is primarily a workflow and milestone-contract update. Existing project truth does not need to be rewritten merely to adopt the two-phase lifecycle.
