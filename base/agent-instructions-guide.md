# Agent Instructions Guide

## Status

Base guide for generating product-repository `AGENTS.md` files.

## Purpose

`AGENTS.md` is a local operational routing document for implementation agents.

It must be concise. It must not become a copy of the guide system.

## Recommended content

```md
# Agent Instructions

## Default implementation path

Read:
- docs/ENGINEERING.md
- the relevant milestone section or task description
- relevant specs under docs/specs/
- relevant source and test files

Use canonical `eng/` commands only.

## Conditional reading

Read public docs only when changing public behavior.
Read architecture and decisions only when changing durable boundaries.
Read workflow docs only when changing CI/release/workflow behavior.

## Do not

- Do not invent commands.
- Do not perform broad documentation synchronization unless requested.
- Do not treat external guide documents as repository authority.
```
