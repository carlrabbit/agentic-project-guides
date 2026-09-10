# Agentic Project Guides

Version: 0.8.0

This repository contains a versioned guide system for creating and maintaining AI-friendly project documentation and engineering workflows.

The guide system is intentionally separate from product repositories.

Product repositories contain localized project truth and concrete project specializations. They may also retain selective non-authoritative research for future planning. Planning, migration, documentation synchronization, and guide authoring may use this guide repository. Ordinary implementation agents work from localized repository authority documents and implementation-ready milestones.

## Core rule

```text
Guides live here.
Projects contain project truth and concrete specializations.
Projects may retain selective non-authoritative planning research.
Profiles describe broad reusable engineering shapes, not feature tags.
Multiple profiles compose additively and may have explicit semantic applicability scopes.
Validation depth is independent of target and execution locus.
Milestones are planned before they are implemented.
Planning resolves uncertainty and produces a ready milestone.
Planning may preserve reusable evidence without preserving the planning conversation.
Planning promotes implementation-affecting research conclusions into project authority.
A ready milestone must be executable by the project's baseline implementation model without research reconstruction.
Implementation begins by decomposing the ready milestone into bounded execution work packages.
AI executors persist coverage and progress in a repository-local execution ledger.
Implementation derives concrete edits from the live repository and the ready milestone.
The executor owns milestone closure, not only code production and test execution.
Validation success is evidence, not milestone completion by itself.
Distributable artifacts are validated through their intended consumer mechanism.
Documentation sync consumes deferred sync hints.
Human review gates milestone completion when automation cannot decide acceptance.
```

## Version 0.8.0

Version 0.8.0 makes project specialization, scoped profile composition, planning research, and integration-first/local-first validation first-class without expanding the central guide into a catalog of concrete project types.

### Planning research

Planning often needs more evidence and investigation context than should become implementation context or durable project authority.

0.8 defines `docs/research/` as an optional non-authoritative planning-knowledge layer.

Use it to preserve evidence that would be materially useful to future planning and expensive, unreliable, or wasteful to rediscover, such as external documentation findings, experiments, compatibility probes, historical reconstruction, comparisons, uncertainty, and revalidation triggers.

The generic flow is:

```text
investigation/evidence
  -> durable research when justified
  -> planning conclusion
  -> project authority when implementation depends on the conclusion
  -> implementation
```

Research is not project authority. Ordinary implementation must remain executable from the ready milestone and referenced project authority without reconstructing planning decisions from research.

See `meta/RESEARCH-MODEL.md` and `templates/research/research-template.md`.

### Validation model

Validation tiers now describe depth and purpose only.

```text
Tier 0  edit sanity
Tier 1  focused validation
Tier 2  standard repository validation
Tier 3  integration validation
Tier 4  release and consumer validation
Tier 5  human review validation
```

A material validation obligation may separately declare:

```text
depth
+ target
+ execution locus
+ platform/capability requirements
+ evidence
```

Integration validation may therefore be authoritative on a local Windows workstation, in CI, against a remote service, through an installed desktop runtime, or through a mixed topology.

CI is not part of the generic definition of integration depth or repository maturity.

### Project specialization

The guide system defines reusable decision surfaces. Product repositories record concrete answers.

Named vendor/runtime/architecture details such as Power BI Desktop integration, a particular database topology, organization-specific authentication, or a concrete native runtime normally remain project-local engineering/specification/decision authority.

The former central `project-types/agentic-2d-game-engine/` layer is removed. Concrete project archetypes should not grow a parallel guide hierarchy.

### Profiles and mixed repositories

Profiles remain broad reusable engineering shapes such as `dotnet-library`, `source-generator`, or `artifact-first-runtime`.

Do not create profiles merely for an operating system, local/CI execution, integration-first testing, one packaging mechanism, one external product, or one concrete project architecture.

A repository may combine a small number of profiles when several broad engineering shapes genuinely apply.

Applicability can be:

```text
repository-wide
component-scoped
surface-scoped
```

For example:

```text
base                [repository]
dotnet-library       [repository]
source-generator     [component: generator-packages]
```

Profiles compose additively. Ordering has no semantic meaning, and no profile silently overrides another. Material conflicts must be resolved into project-local authority before implementation.

`.guide-profile.json` schema version 2 records semantic profile scopes for planning/traceability. Component/surface IDs are defined by normal project authority rather than path globs in metadata.

### Integration-first libraries

The `.NET library` profile no longer implies a unit-test-first/test-pyramid strategy. Projects may explicitly adopt integration-first testing and use unit tests only where isolated validation is materially cheaper, more exhaustive, or more diagnostic.

Consumer-surface validation from v0.7.4 remains in force: a packed NuGet package must be exercised through an intended consumer path when that distributable boundary is affected.

### Planning-to-implementation boundary

The v0.7.5 decision-preservation model remains in force and is extended by the research model.

Planning may retain useful evidence, but a ready milestone must not depend on the implementation agent reconstructing the decision from that evidence.

When correctness depends on a concrete external runtime/service/environment, planning must ensure that the target, execution locus, capability constraints, invocation/evidence policy, and any required project-local specialization are durable before a milestone becomes `ready`.

When multiple scoped profiles apply, planning must also determine the affected semantic scope, combine applicable obligations, and resolve any material conflicts into durable project authority.

Implementation still owns concrete code/test mechanics that fit that contract.

## Upgrade

From v0.7.5, use:

```text
migrations/guide-system-v0.7.5-to-v0.8.0.md
```
