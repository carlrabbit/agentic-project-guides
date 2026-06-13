# Dotnet Library Engineering Profile

## Status

Engineering profile for .NET libraries.

## Common engineering blocks

- .NET solution
- shared build configuration
- editorconfig
- fast tests
- validation tiers
- package validation when public packages are active
- public API validation when public API compatibility matters
- release validation when release-ready

## Canonical commands

```text
./eng/restore.sh
./eng/build.sh
./eng/test.sh
./eng/check.sh
```

Public package repositories may add:

```text
./eng/package.sh <version>
./eng/package-smoke.sh <version>
./eng/public-api.sh
./eng/public-docs.sh
./eng/release-check.sh <version>
```

## Rule

Do not require release validation for ordinary implementation work.
