# Meta Guide

## Status

Authoritative meta-level guide for creating, versioning, applying, executing, and migrating the guide system.

## Purpose

The meta guide defines how this guide system is structured and how guide artifacts are applied to concrete repositories.

It does not define a single universal repository template or maintain a catalog of concrete project types. Instead, it defines how to compose reusable profiles and generic models, then specialize them through project-local authority for a repository's actual technology, runtime, validation, and architectural constraints.

## Core doctrine

```text
Guide repository owns methodology and reusable engineering shapes.
Product repositories contain project truth and concrete specializations.
Milestones separate planning from implementation.
Implementation agents read product repository documentation and ready milestones only.
Planning and documentation-sync agents may use this guide system.
```

## Product repository boundary

Product repositories must not copy guide documents as active authority.

A product repository may contain `.guide-profile.json` for traceability and `.guide-sync/pending/` for deferred documentation synchronization hints.

These files are coordination metadata, not ordinary implementation authority.

Concrete specializations and semantic component/surface definitions are ordinary project truth and belong in the repository's normal engineering, specification, architecture, or decision documents.

## Guide composition principle

Guides compose; repositories do not inherit everything.

A repository should be planned from an explicit small profile selection such as:

```text
base + dotnet-library + public-preview maturity
```

or:

```text
base + artifact-first-runtime + capability-provider role + implementation-ready maturity
```

Profiles describe broad reusable engineering shapes. They are not feature tags for operating systems, test strategies, packaging choices, execution locations, named vendor products, or concrete project architectures.

### Scoped composition

Multiple broad engineering shapes may coexist in one repository.

Profile applicability may be:

```text
repository-wide
component-scoped
surface-scoped
```

For example, a package suite containing ordinary .NET libraries and source-generator packages can use:

```text
base                [repository]
dotnet-library       [repository]
source-generator     [component: generator-packages]
```

Profiles compose additively. Profile order has no semantic meaning and no profile silently overrides another.

If applicable profile obligations conflict materially, planning resolves the conflict into project-local authority before implementation proceeds.

`.guide-profile.json` records profile applicability for planning/traceability. Component and surface IDs are semantic project-defined identifiers; their meaning comes from normal project authority, not path globs in metadata.

Project-local authority then specializes the reusable model where concrete answers are required.

Example:

```text
profile:
  dotnet-library

project policy:
  integration-first

validation target:
  installed external desktop runtime

project-local specialization:
  concrete runtime, Windows requirements, invocation,
  isolation/reset, evidence, and failure semantics
```

See `meta/PROFILE-MODEL.md`, `meta/SPECIALIZATION-MODEL.md`, and `meta/VALIDATION-MODEL.md`.

## Planning/implementation separation

Milestone work has two distinct phases independent of the human, model, interface, or tool used for either phase.

Planning agents may read this guide repository. They inspect enough product-repository truth to resolve implementation-affecting uncertainty and produce a ready milestone.

Planning owns decisions that materially affect:

- architecture;
- semantics;
- compatibility;
- scope and non-goals;
- acceptance criteria;
- validation and review policy;
- applicable profiles and their semantic scopes;
- conflicts between applicable profile obligations;
- required project-local specializations.

Planning may create or update durable project-truth documents when those decisions need repository authority.

Planning should not prescribe concrete implementation mechanics that a capable executor can derive from the live repository unless those mechanics are themselves part of the required contract.

Implementation agents execute a ready milestone. They inspect the live source and tests, derive concrete edits, implement, validate, and produce evidence. They should not read this guide repository unless explicitly assigned planning, guide migration, documentation synchronization, or release documentation work.

The implementation handoff must not depend on the planning conversation. Everything required to execute must exist in the ready milestone or its referenced project authority.

If implementation discovers a material unresolved architectural, semantic, compatibility, scope, acceptance, validation, profile-applicability/conflict, or specialization decision, the milestone returns to planning. Implementation must not silently create new project policy.

Planning agents may also create:

- documentation packages;
- migration packages;
- optional overlays when planning itself requires repository-relative file additions, replacements, moves, or deletions;
- concise execution prompts when a disconnected execution interface benefits from one.

An overlay is a transport mechanism, not a second source of planning authority.
