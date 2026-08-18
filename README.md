# Agentic Project Guides

Version: 0.7.1

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
The executor owns milestone closure, not only code production and test execution.
Validation success is evidence, not milestone completion by itself.
Documentation sync consumes deferred sync hints.
Human review gates milestone completion when automation cannot decide acceptance.
```

## Version 0.7.1

Version 0.7.1 strengthens milestone closure semantics for implementation agents.

The lifecycle remains:

```text
draft/planning -> ready -> implementing -> done
```

Implementation now follows an explicit completion loop:

```text
implement -> validate -> completion audit -> continue or terminate
```

After implementation and validation, the executor must audit all milestone obligations and continue resolving anything it can complete in the current execution context.

Passing tests, successful compilation, or completing listed focus areas does not by itself establish milestone completion.

An implementation run terminates only as:

- `COMPLETE` — every applicable milestone obligation and completion gate is satisfied;
- `AWAITING HUMAN REVIEW` — all agent-resolvable work is complete and a required human decision remains;
- `BLOCKED` — completion requires unavailable external capability or a material planning decision the executor cannot make.

Scope guardrails prevent unrelated product expansion but do not prohibit supporting edits necessary to satisfy the milestone contract. Focus areas and workstreams are guidance rather than edit allowlists unless explicitly made contractual.

No additional engineering commands are required by v0.7.1.

Execution profiles such as `human-led`, `ai-assisted`, and `ai-executed-human-reviewed` remain orthogonal to lifecycle phase.

## Upgrade

From v0.7.0, use:

```text
migrations/guide-system-v0.7.0-to-v0.7.1.md
```

The migration is a focused execution-contract correction. It does not require new engineering commands or broad project-documentation changes.
