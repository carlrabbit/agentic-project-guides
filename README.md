# Agentic Project Guides

Version: 0.7.2

This repository contains a versioned guide system for creating and maintaining AI-friendly project documentation and engineering workflows.

The guide system is intentionally separate from product repositories.

Product repositories contain localized project truth. Planning, migration, documentation synchronization, and guide authoring may use this guide repository. Ordinary implementation agents work from localized repository authority documents and implementation-ready milestones.

## Core rule

```text
Guides live here.
Projects contain project truth.
Milestones are planned before they are implemented.
Planning resolves uncertainty and produces a ready milestone.
A ready milestone must be executable by the project's baseline implementation model.
Implementation derives concrete edits from the live repository and the ready milestone.
The executor owns milestone closure, not only code production and test execution.
Validation success is evidence, not milestone completion by itself.
Documentation sync consumes deferred sync hints.
Human review gates milestone completion when automation cannot decide acceptance.
```

## Version 0.7.2

Version 0.7.2 makes baseline-model executability part of the `ready` milestone boundary.

For the default ChatGPT-focused profile, the baseline implementation model is GPT-5.6 Luna.

The purpose is not to make milestones tiny or prescribe implementation line by line. Planning should perform the difficult project-level reasoning and leave the implementation agent a bounded contract whose remaining choices are local implementation mechanics.

A milestone is not `ready` when its executor would still need to make a material decision about architecture, semantics, compatibility, scope, acceptance, or validation policy. In that case planning continues, or a focused diagnostic milestone is planned first when evidence must be gathered before the final implementation contract can be decided.

The guide does not introduce `strong` or `frontier` execution tiers. Execution profiles such as `human-led`, `ai-assisted`, `ai-executed-human-reviewed`, and `ai-executed-broad` continue to describe autonomy and review expectations rather than model capability.

Large or cross-cutting work can still be baseline-executable when its decisions are settled, its boundaries are explicit, and its validation is sufficiently deterministic or resumable.

The v0.7.1 closure contract remains unchanged:

```text
implement -> validate -> completion audit -> continue or terminate
```

An implementation run terminates only as:

- `COMPLETE` — every applicable milestone obligation and completion gate is satisfied;
- `AWAITING HUMAN REVIEW` — all agent-resolvable work is complete and a required human decision remains;
- `BLOCKED` — completion requires unavailable external capability or a material planning decision the executor cannot make.

## Upgrade

From v0.7.1, use:

```text
migrations/guide-system-v0.7.1-to-v0.7.2.md
```

The migration primarily changes planning and milestone-readiness semantics. The canonical v0.7.1 execution prompt remains compatible and does not require replacement merely to adopt v0.7.2.
