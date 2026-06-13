# Base Engineering Guide

## Status

Base engineering guide for project-type engineering guides.

## Purpose

This guide defines common engineering concepts: canonical commands, validation tiers, local vs CI validation, release validation, and implementation-agent expectations.

Concrete project-type guides specialize this base guide.

## Core principles

```text
Commands are canonical.
Validation is tiered.
Implementation validation is not always release validation.
CI is the integration authority when configured.
Documentation sync is separate from implementation.
```

## Recommended base commands

```text
./eng/restore.sh
./eng/build.sh
./eng/test.sh
./eng/check.sh
```

Repositories may add focused commands:

```text
./eng/check-affected.sh
./eng/test-project.sh <project>
./eng/test-filter.sh <filter>
```

Release-capable repositories may add:

```text
./eng/package.sh <version>
./eng/public-api.sh
./eng/public-docs.sh
./eng/release-check.sh <version>
```

## Validation tiers

Use the tiers from `meta/VALIDATION-MODEL.md`.

Milestones should state expected local, PR, and release validation.
