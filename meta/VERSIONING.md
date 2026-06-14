# Versioning

## Status

Authoritative for guide-system versioning.

## Versioned artifacts

The following artifacts are versioned independently when useful:

- guide system;
- base guides;
- profiles;
- project-type guides;
- migrations;
- templates;
- prompt families.

## Semantic versioning

Use semantic versioning.

```text
MAJOR
  Breaking guide model change.
  Existing repositories likely need migration planning.

MINOR
  New optional guide module, profile, maturity stage, building block, prompt family, or guidance.
  Existing repositories do not require immediate migration unless they use the affected workflow.

PATCH
  Clarification, typo, example improvement, or non-semantic wording.
  No repository migration expected.
```

## Changelog rules

Each minor or major version entry should state:

- migration required: yes/no/conditional;
- affected areas;
- affected product repositories;
- required migration;
- conditional migration;
- deprecated concepts;
- manual review points.

This lets latest-version migration prompts inspect `CHANGELOG.md` and construct repository-specific migration plans.
