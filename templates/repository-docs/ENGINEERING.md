# Engineering

## Purpose

This document defines this repository's local engineering commands, validation tiers, and tooling rules.

## Canonical commands

```text
./eng/restore.sh
./eng/build.sh
./eng/test.sh
./eng/check.sh
```

## Validation tiers

| Tier | Purpose | Command |
|---|---|---|
| 0 | Edit sanity | Repository-specific. |
| 1 | Focused validation | Repository-specific. |
| 2 | Standard local validation | `./eng/check.sh` |
| 3 | PR integration validation | GitHub workflows. |
| 4 | Release validation | Repository-specific. |
| 5 | Human review validation | Repository-specific. |

## Rule

Use the validation tier named by the milestone or task.
