# Agentic Project Guides

Version: 0.7.4

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
Implementation begins by decomposing the ready milestone into bounded execution work packages.
AI executors persist coverage and progress in a repository-local execution ledger.
Implementation derives concrete edits from the live repository and the ready milestone.
The executor owns milestone closure, not only code production and test execution.
Validation success is evidence, not milestone completion by itself.
Distributable artifacts are validated through their intended consumer mechanism.
Documentation sync consumes deferred sync hints.
Human review gates milestone completion when automation cannot decide acceptance.
```

## Version 0.7.4

Version 0.7.4 strengthens validation at distributable product boundaries.

A repository that ships a package, tool, published executable, or similar distributable artifact must include representative acceptance coverage that consumes the artifact through the mechanism real consumers use. Testing only source projects, internal assemblies, command handlers, or unpackaged build outputs is insufficient to prove the distributable surface.

For a `dotnet tool`, applicable validation must pack the current tool package, install that exact package through `dotnet tool` using an isolated tool path or local tool manifest, and invoke the installed command/shim. The acceptance path should remain small and representative; detailed behavior still belongs primarily in lower-level tests.

The generic examples are:

```text
NuGet library
  -> pack -> isolated consumer -> representative public behavior

dotnet tool
  -> pack -> dotnet tool install -> installed command/shim -> representative command behavior

standalone executable
  -> publish/package -> invoke published artifact
```

Consumer-surface validation must use the artifact produced by the current build and avoid accidental reliance on globally installed, cached, stale, or repository-internal artifacts.

This is a validation rule, not a new project type or engineering-command requirement.

The v0.7.3 execution-ledger and milestone-closure model remains unchanged.

## Upgrade

From v0.7.3, use:

```text
migrations/guide-system-v0.7.3-to-v0.7.4.md
```
