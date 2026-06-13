# Meta Guide

## Status

Authoritative meta-level guide for creating, versioning, applying, and migrating project-type guides.

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

## Non-goals

This meta guide is not:

- a concrete .NET setup guide;
- a concrete game-engine design document;
- a mandatory product-repository document;
- required reading for ordinary implementation agents.

## Guide application flow

```text
1. Select repository role.
2. Select maturity stage.
3. Select base guide modules.
4. Select project profiles.
5. Select project-type guides if needed.
6. Generate localized repository documentation.
7. Plan milestones from localized project truth.
8. Run implementation work against localized docs only.
9. Run documentation sync passes using this guide system when needed.
10. Apply future changes through profile-aware migrations.
```

## Product repository boundary

Product repositories must not copy guide documents as active authority.

Do not place these in final product repositories as required operational docs:

```text
docs/research/project-setup-guide-*.md
docs/research/engineering-guide-*.md
docs/research/meta-guide-*.md
```

A product repository may contain `.guide-profile.json` for traceability. That file is metadata for planning and documentation-sync agents, not normal implementation context.

## Guide composition principle

Guides compose; repositories do not inherit everything.

A repository should be generated from an explicit selection such as:

```text
base + dotnet-library + source-generator + public-preview maturity
```

or:

```text
base + artifact-first-runtime + capability-provider role + implementation-ready maturity
```

## Default exclusions

The following are not default repository layers:

- TBPs;
- issue templates;
- copied guide documents;
- release-readiness structure before release maturity;
- public documentation before a public surface exists;
- process-heavy workflow documents unless the repository needs them.

They may be activated by a profile or project-type guide, but they are absent by default.
