# Profile Model

## Status

Authoritative for reusable profile selection, applicability, and composition.

## Purpose

A profile is a reusable project category that activates documentation, engineering, validation, and release expectations.

Profiles avoid one universal repository template while keeping concrete project technology and architecture in project-local authority.

Example profiles:

```text
base
dotnet-library
source-generator
blazor-component
artifact-first-runtime
```

A profile defines a broad reusable engineering shape. It may define applicability, documentation layers, engineering blocks, validation expectations, maturity behavior, repository-role behavior, and migration concerns.

## Profiles are not feature tags

Do not create a profile merely for:

- an operating system;
- local versus CI execution;
- one external product or service;
- one packaging mechanism;
- one test-strategy preference;
- one concrete product architecture.

Those concerns should normally be expressed through project engineering policy, validation targets/loci, reusable generic guidance, or project-local specialization.

## Multi-profile composition

A repository may combine a small number of profiles when multiple broad engineering shapes genuinely apply.

Profiles compose additively:

```text
base obligations
+ every applicable profile obligation
+ project-local specialization/resolution
= effective project contract
```

Profile order has no semantic meaning. There is no `primary` profile, `secondary` profile, last-profile-wins behavior, or implicit precedence hierarchy.

Avoid profile proliferation that merely reconstructs a project from feature tags.

## Profile applicability

A profile may apply:

```text
repository-wide
component-scoped
surface-scoped
```

Use repository-wide applicability when the engineering shape describes the repository as a whole.

Use component scope when the profile describes one or more durable semantic components in a mixed repository, for example a set of source-generator packages inside a larger .NET package suite.

Use surface scope when the profile applies to a durable consumer/engineering surface that is not naturally identical to one directory or project, for example a compile-time generator consumption surface.

Applicability is semantic rather than path-based. Component and surface identifiers are project-defined identifiers whose meaning must be recoverable from normal project authority such as `docs/ARCHITECTURE.md`, `docs/ENGINEERING.md`, or a relevant specification.

Do not make path globs in `.guide-profile.json` the authoritative definition of a component or surface. Paths may change during refactoring while the semantic applicability remains stable.

## `.guide-profile.json` scope metadata

`.guide-profile.json` records profile selection and scope for planning/traceability. It is not ordinary implementation authority.

Guide-profile schema version 2 represents profile applicability with `scopes` entries.

Repository-wide example:

```json
{
  "id": "dotnet-library",
  "version": "0.8.0",
  "scopes": [
    { "kind": "repository" }
  ]
}
```

Scoped example:

```json
{
  "id": "source-generator",
  "version": "0.8.0",
  "scopes": [
    {
      "kind": "component",
      "ids": [
        "generator-packages"
      ]
    }
  ]
}
```

Supported scope kinds are:

- `repository` — applies to the whole repository; `ids` is omitted;
- `component` — applies to one or more project-defined component IDs;
- `surface` — applies to one or more project-defined surface IDs.

A profile may declare multiple scopes when necessary. Do not duplicate profile entries merely to enumerate IDs of the same applicability kind.

Legacy schema-version-1 profile entries without scope metadata are interpreted as repository-wide during migration unless project evidence shows that a narrower scope was intended.

## Conflict handling

Compatible applicable obligations are combined.

A more specialized profile does not silently override a broader profile. If two applicable profiles impose materially incompatible expectations, planning must resolve the conflict explicitly before implementation proceeds.

The resolution belongs in project-local authority when it affects implementation, validation, packaging, compatibility, or release behavior.

Examples of valid resolution authority include:

```text
docs/ENGINEERING.md
docs/ARCHITECTURE.md
docs/specs/<topic>.md
docs/decisions/<decision>.md
```

Do not encode conflict resolution by reordering `appliedProfiles`.

## Mixed-repository example

A .NET package suite containing ordinary runtime libraries and two Roslyn source-generator packages may use:

```text
base                [repository]
dotnet-library       [repository]
source-generator     [component: generator-packages]
```

The `.NET library` obligations continue to apply to the package suite. Source-generator obligations additionally apply to the generator components. Generator-specific packaging or compiler-host behavior is then resolved in project-local engineering authority.

Concrete target integrations such as EF Core, Power BI, SQL Server, browsers, or named vendor runtimes remain project-local specializations unless a vendor-independent reusable engineering shape justifies a future profile.

## Promotion boundary

Concrete technology/runtime behavior belongs in project-local authority unless it has matured into reusable guide-level guidance independent of the originating project.

Create a new profile only when the candidate describes a recognizable reusable engineering shape and materially affects several repository concerns such as documentation, validation, packaging, public surface, or release behavior.
