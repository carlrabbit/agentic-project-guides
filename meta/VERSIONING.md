# Versioning

## Status

Authoritative for guide-system versioning.

## Versioned artifacts

The following artifacts are versioned independently:

- guide system;
- base guides;
- profiles;
- project-type guides;
- migrations;
- templates.

## Semantic versioning

Use semantic versioning.

```text
MAJOR
  Breaking guide model change.
  Existing repositories likely need migration planning.

MINOR
  New optional guide module, profile, maturity stage, building block, or guidance.
  Existing repositories do not require immediate migration.

PATCH
  Clarification, typo, example improvement, or non-semantic wording.
  No repository migration expected.
```

## Change metadata

Every meaningful guide change should declare:

```text
Migration required: yes/no
Affected profiles
Affected repository roles
Affected maturity stages
Affected documentation layers
Affected validation tiers
```

## Product repository traceability

Use `.guide-profile.json` when traceability is needed.

Do not use Markdown documentation inside product repositories to explain the guide system unless the repository itself is a guide repository.
