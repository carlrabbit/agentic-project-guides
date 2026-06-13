# Base Setup Guide

## Status

Base guide for creating localized repository documentation from selected profiles.

## Purpose

This guide defines the minimum repository documentation model shared by most project types.

It is not copied into product repositories.

## Required base repository docs

```text
README.md
AGENTS.md
docs/ENGINEERING.md
```

Add other docs only when the selected profile, maturity stage, and repository role require them.

## Default repository rule

Product repositories contain localized project truth.

Do not copy guide documents into the product repository as active documentation.

## Default AGENTS.md rule

`AGENTS.md` should be short and local.

It should route implementation agents to:

- `docs/ENGINEERING.md`;
- the relevant milestone or task description;
- relevant specs;
- relevant source/test areas.

It should not route implementation agents to the guide repository.

## Optional traceability

Use `.guide-profile.json` when repository-guide traceability is needed.
