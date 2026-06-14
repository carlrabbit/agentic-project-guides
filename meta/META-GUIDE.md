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
Implementation agents read product repository documentation only.
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

## Planning/execution separation

Planning agents may read this guide repository.

Planning agents create:

- milestone packages;
- documentation packages;
- migration packages;
- execution prompts for later implementation agents.

Implementation agents execute the plan. They should not read this guide repository unless explicitly assigned planning, guide migration, documentation synchronization, or release documentation work.
