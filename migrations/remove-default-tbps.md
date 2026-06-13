# Migration — Remove Default TBPs

## Status

Draft.

## Purpose

Remove TBPs as a default repository layer.

## Required changes

- Remove `docs/TBPS.md` from `AGENTS.md` required reading.
- Remove TBP references from milestones unless the repository explicitly keeps a process-heavy profile.

## Conditional changes

- Delete `docs/TBPS.md` and `docs/tbps/` if no repository-specific methodology remains.

## Manual review

- Move concrete engineering constraints into `docs/ENGINEERING.md`.
- Move behavior truth into specs.
- Move documentation methodology into the external guide repository.

## Validation

- Implementation agents can perform ordinary tasks without TBP reading.
