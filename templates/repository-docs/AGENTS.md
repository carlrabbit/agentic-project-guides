# Agent Instructions

## Default implementation path

Read:

- `docs/ENGINEERING.md`
- the relevant milestone section or task description
- relevant specs under `docs/specs/`
- relevant source and test files

Use canonical `eng/` commands only.

## Conditional reading

Read public docs only when changing public behavior, package behavior, diagnostics, samples, or consumer-facing usage.

Read architecture and decisions only when changing durable subsystem boundaries or design rationale.

Read workflow docs only when changing CI, release, or workflow behavior.

## Ignored Coordination Metadata

Do not read or modify these files during ordinary implementation work unless the task explicitly says it is guide migration, milestone planning, documentation synchronization, release readiness, or release documentation work:

- `.guide-profile.json`
- `.guide-sync/`

These files are for planning and documentation synchronization agents. They are not implementation authority.

## Do not

- Do not invent build, test, package, or release commands.
- Do not perform broad documentation synchronization unless requested.
- Do not treat external guide documents as repository authority.
- Do not add copied guide documents to this repository.
