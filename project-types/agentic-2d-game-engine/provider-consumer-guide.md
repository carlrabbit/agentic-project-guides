# Agentic 2D Game Engine Provider/Consumer Guide

## Status

Authoritative project-type distinction between engine implementation and engine usage.

## Core rule

```text
Because the engine supports scenarios, the engine repository must prove the scenario capability works.
A game repository using the engine uses scenarios to validate game behavior.
```

## Provider responsibilities

The engine repository validates:

- runtime model correctness;
- CLI command behavior;
- scenario runner contracts;
- artifact emission;
- content schema validation;
- asset pipeline mechanics;
- review gate mechanics;
- debug/release semantic equivalence fixtures.

## Consumer responsibilities

A game repository validates:

- gameplay scenarios;
- authored maps;
- authored assets;
- UI behavior;
- save/load behavior;
- performance budgets;
- human review of creative or high-impact artifacts.

## Dogfood rule

Dogfood content in the engine repository must remain small and representative.

It must not silently become the production game.
