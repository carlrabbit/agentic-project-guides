# Agentic Project Guides

This repository contains a versioned guide system for creating and maintaining AI-friendly project documentation and engineering workflows.

The guide system is intentionally separate from product repositories.

Product repositories should contain localized project truth only:

- `README.md`
- `AGENTS.md`
- `docs/*`
- `eng/*`
- source, tests, samples, and artifacts

Product repositories should not contain copied setup guides, engineering guides, or meta guides as operational documentation.

## Core rule

```text
Guides live here.
Projects contain project truth.
Planning and documentation-sync work may use the guides.
Implementation work uses localized project documentation only.
```

## Repository structure

```text
meta/                         Meta-level guide system rules.
base/                         Base setup, engineering, agent, and documentation-sync guides.
profiles/                     Reusable project profiles.
project-types/                More specific project-type guides built from profiles.
decisions/                    Decision records for the guide system itself.
migrations/                   Profile-aware guide/repository migration documents.
templates/                    Reusable templates for generated repository documentation.
```

## Versioning

Guide artifacts use semantic versioning.

- `MAJOR`: breaking guide model change; repository migration likely required.
- `MINOR`: new optional profile, building block, maturity stage, or guidance.
- `PATCH`: clarification, typo, examples, or non-semantic wording.

See `meta/VERSIONING.md`.
