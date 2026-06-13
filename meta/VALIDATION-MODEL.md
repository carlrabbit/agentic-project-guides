# Validation Model

## Status

Authoritative for validation tier concepts.

## Purpose

Validation must be explicit, tiered, and appropriate to the execution mode.

One broad validation command is not enough for AI-first work.

## Validation tiers

| Tier | Name | Purpose |
|---|---|---|
| 0 | Edit sanity | Formatting, schema checks, touched-file checks. |
| 1 | Focused validation | Affected project/component/spec-area validation. |
| 2 | Standard local validation | Normal repository local gate. |
| 3 | PR integration validation | Full CI/workflow validation. |
| 4 | Release validation | Package, public API, public docs, samples, release checks. |
| 5 | Human review validation | Human acceptance of artifacts, semantics, visual quality, UX, or creative decisions. |

## Rule

Milestones and tasks should state the expected validation tier.

Implementation agents should not always run release or full integration validation locally when PR workflows are the integration authority.

## Canonical commands

Repositories should expose canonical commands, but commands should support focused and broad validation paths.

Examples:

```text
./eng/check.sh
./eng/check-affected.sh
./eng/test-project.sh <project>
./eng/release-check.sh <version>
```
