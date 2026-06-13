# Migration — Remove Repository Guide Copies

## Status

Draft.

## Purpose

Remove copied setup, engineering, or meta guides from product repositories as active documentation.

## Applies when

A product repository contains guide documents under paths such as:

```text
docs/research/project-setup-guide-*.md
docs/research/engineering-guide-*.md
```

## Required changes

- Remove guide references from `AGENTS.md` required reading.
- Remove guide references from milestone required reading.
- Remove guide references from README contributor routing.

## Conditional changes

- Delete copied guide files if they have no historical value.
- Keep them only as archived research if the repository explicitly needs historical traceability.

## Manual review

- Move useful localized rules into `docs/ENGINEERING.md`, `AGENTS.md`, or relevant specs.

## Validation

- Implementation instructions no longer require external or copied guides.
- Product docs remain self-contained.
