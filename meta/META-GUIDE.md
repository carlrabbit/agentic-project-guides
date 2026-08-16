# Meta Guide

## Status

Authoritative meta-level guide for creating, versioning, applying, executing, and migrating project-type guides.

## Purpose

The meta guide defines how this guide system is structured and how guide artifacts are applied to concrete repositories.

It does not define a single universal repository template. Instead, it defines how to compose project-specific guide profiles by project type, repository role, maturity stage, validation model, and execution model.

## Core doctrine

```text
Guide repository owns methodology.
Product repositories contain project truth.
Milestones separate planning from implementation.
Implementation agents read product repository documentation and ready milestones only.
Planning and documentation-sync agents may use this guide system.
```

## Product repository boundary

Product repositories must not copy guide documents as active authority.

A product repository may contain `.guide-profile.json` for traceability and `.guide-sync/pending/` for deferred documentation synchronization hints.

These files are coordination metadata, not ordinary implementation authority.

## Guide composition principle

Guides compose; repositories do not inherit everything.

A repository should be generated from an explicit profile selection such as:

```text
base + dotnet-library + source-generator + public-preview maturity
```

or:

```text
base + artifact-first-runtime + capability-provider role + implementation-ready maturity
```

## Planning/implementation separation

Milestone work has two distinct phases independent of the human, model, interface, or tool used for either phase.

Planning agents may read this guide repository. They inspect enough product-repository truth to resolve implementation-affecting uncertainty and produce a ready milestone.

Planning owns decisions that materially affect:

- architecture;
- semantics;
- compatibility;
- scope and non-goals;
- acceptance criteria;
- validation and review policy.

Planning may create or update durable project-truth documents when those decisions need repository authority.

Planning should not prescribe concrete implementation mechanics that a capable executor can derive from the live repository unless those mechanics are themselves part of the required contract.

Implementation agents execute a ready milestone. They inspect the live source and tests, derive concrete edits, implement, validate, and produce evidence. They should not read this guide repository unless explicitly assigned planning, guide migration, documentation synchronization, or release documentation work.

The implementation handoff must not depend on the planning conversation. Everything required to execute must exist in the ready milestone or its referenced project authority.

If implementation discovers a material unresolved architectural, semantic, compatibility, scope, acceptance, or validation decision, the milestone returns to planning. Implementation must not silently create new project policy.

Planning agents may also create:

- documentation packages;
- migration packages;
- optional overlays when planning itself requires repository-relative file additions, replacements, moves, or deletions;
- concise execution prompts when a disconnected execution interface benefits from one.

An overlay is a transport mechanism, not a second source of planning authority.
