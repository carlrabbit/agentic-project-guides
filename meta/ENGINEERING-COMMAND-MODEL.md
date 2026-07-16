# Engineering Command Model

## Core doctrine

```text
eng/ defines the stable engineering API.
Platform scripts are thin launchers.
Complex engineering semantics live in tested application code.
Platform support is declared and tested.
```

## Implementation levels

### Level 1 — Direct thin scripts

Use for simple restore, build, test, or format commands.

### Level 2 — Shared launcher helpers

Use for modest process orchestration without domain semantics.

### Level 3 — Engineering command host

Use when commands require JSON parsing, workspace resolution, fingerprints, manifests, artifact generation, complex filtering, review state, or resumable validation.

A typical host is:

```text
src/<Project>.Engineering
```

or an existing product CLI with an `engineering` command group.

## Launcher model

```text
eng/check.sh ─────┐
                  ├──> shared .NET engineering command
eng/check.ps1 ────┘
```

Launchers must forward arguments and exit codes without duplicating semantics.

## Cross-platform support

A launcher existing on a platform does not prove that platform is supported.

Repositories should declare:

- supported launchers;
- tested platforms;
- native dependencies;
- CI matrix coverage.

Relevant platform behavior includes paths, case sensitivity, executable permissions, line endings, symlinks, file locks, atomic moves, temporary directories, Git behavior, process cancellation, and native dependencies.
