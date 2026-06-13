# Artifact-First Runtime Setup Profile

## Status

Profile guide for repositories that provide or consume artifact-first runtimes, tools, validators, scenario systems, asset/content pipelines, or authoring systems.

## Applies when

Use this profile when correctness involves more than source code and unit tests, for example:

- structured project data;
- generated artifacts;
- runtime scenarios;
- artifact reports;
- previews or overlays;
- human review gates.

## Role-sensitive rule

Provider repositories implement the capability.

Consumer repositories use the capability to validate authored products or content.

Mixed/dogfood repositories do both, but dogfood scope must remain bounded.

## Potential active layers

```text
docs/SPECS.md
docs/ENGINEERING.md
docs/SCENARIOS.md
docs/ARTIFACTS.md
docs/HUMAN-REVIEW.md
```

Activate these only when the repository role and maturity stage require them.
