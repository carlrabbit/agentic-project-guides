# Agentic 2D Game Engine Project-Type Setup Guide

## Status

Project-type guide for an agentic 2D game engine repository.

## Depends on

- base setup guide
- dotnet-library profile
- artifact-first-runtime profile

## Repository role

Default role:

```text
capability-provider
```

Optional role:

```text
mixed-dogfood
```

The engine repository implements scenario, artifact, content, validation, and review capabilities. It is not required to behave like a full consumer game repository unless a bounded dogfood project is intentionally included.

## Recommended active docs by maturity

Implementation-ready provider repository:

```text
README.md
AGENTS.md
docs/TERMINOLOGY.md
docs/SPECS.md
docs/ARCHITECTURE.md
docs/DECISIONS.md
docs/ENGINEERING.md
docs/MILESTONES.md
```

Add selectively as capabilities become active:

```text
docs/SCENARIOS.md
docs/ARTIFACTS.md
docs/HUMAN-REVIEW.md
```

Public-preview or release-ready repository may add:

```text
docs/PUBLIC-DOCS.md
public-docs/
```
