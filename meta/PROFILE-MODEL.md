# Profile Model

## Status

Authoritative for guide profile selection and composition.

## Purpose

A profile is a reusable project category that activates documentation, engineering, validation, and release expectations.

Profiles avoid one universal repository template.

## Example profiles

```text
base
dotnet-library
source-generator
blazor-component
artifact-first-runtime
```

## Profile responsibilities

A profile defines:

- applicability;
- active documentation layers;
- optional documentation layers;
- deferred documentation layers;
- engineering building blocks;
- validation tiers;
- maturity-stage behavior;
- repository-role behavior;
- migration concerns.

## Profile composition

Profiles may compose.

Example:

```text
base + dotnet-library + source-generator
```

A project-type guide may depend on one or more profiles.

Example:

```text
agentic-2d-game-engine depends on artifact-first-runtime and dotnet-library.
```

## Rule

A profile must not force unrelated project concerns into a repository.

A profile should make concepts active only when the repository role and maturity stage require them.
