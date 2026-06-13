# Agentic 2D Game Engine Engineering Guide

## Status

Project-type engineering guide for an agentic 2D game engine repository.

## Provider validation emphasis

For the engine repository, prefer:

- unit tests;
- integration tests;
- CLI contract tests;
- artifact schema tests;
- deterministic fixture tests;
- golden-file tests;
- bounded dogfood scenarios.

Do not require broad game-style scenario suites until there is a consumer game or intentionally larger dogfood product.

## Example provider commands

```text
./eng/check.sh
./eng/check-affected.sh
./eng/cli-smoke.sh
./eng/fixture-tests.sh
./eng/artifact-schema.sh
```

Later, when the engine CLI exists, repository commands may wrap product CLI commands.
