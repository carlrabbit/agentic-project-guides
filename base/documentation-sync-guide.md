# Documentation Sync Guide

## Status

Base guide for documentation synchronization passes.

## Purpose

Documentation sync is a separate task type. It may use the guide system and read broadly.

Implementation work should not inherit documentation-sync obligations unless the implementation directly contradicts an authoritative spec or public API contract.

## Documentation sync responsibilities

A documentation sync pass may update:

- README;
- AGENTS;
- terminology;
- specs;
- architecture;
- decisions;
- engineering docs;
- milestones;
- public docs;
- indexes and cross-references.

## Rules

- Do not change implementation code unless explicitly requested.
- Do not copy guide documents into the product repository.
- Do not add operational references from product docs to external guide docs.
- Localize rules into product-specific documents.
