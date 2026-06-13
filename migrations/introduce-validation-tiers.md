# Migration — Introduce Validation Tiers

## Status

Draft.

## Purpose

Replace one-size-fits-all local validation with explicit validation tiers.

## Required changes

- Update `docs/ENGINEERING.md` with validation tiers.
- Update `AGENTS.md` to allow focused validation when named by the task or milestone.
- Update milestone templates to include validation tier.

## Conditional changes

- Add `./eng/check-affected.sh` or project-specific focused commands if the repository benefits from them.

## Manual review

- Decide which PR workflows are integration authority.
- Decide which commands are local, CI-only, release-only, or human-review-only.

## Validation

- Existing `./eng/check.sh` still works.
- New focused commands work if added.
