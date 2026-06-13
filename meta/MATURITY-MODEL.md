# Maturity Model

## Status

Authoritative for repository maturity stages.

## Purpose

Maturity stages prevent premature documentation, release, and validation obligations.

## Stages

| Stage | Meaning |
|---|---|
| `exploration` | Ideas, spikes, research, unstable design. |
| `design-ready` | Terminology, specs, and key decisions are normalized enough for implementation planning. |
| `implementation-ready` | Milestones and validation strategy are clear enough for implementation. |
| `integration-ready` | CI and integration validation protect the repository. |
| `public-preview` | External-facing docs, samples, and compatibility expectations are emerging. |
| `release-ready` | Public API, packages, docs, samples, and release validation are complete enough for release. |
| `published-maintenance` | Compatibility, migration, deprecation, and release discipline dominate. |

## Rule

Do not apply release-ready obligations to exploration or implementation-ready repositories.

Do not apply public-documentation obligations until there is a real public surface or public-preview target.
