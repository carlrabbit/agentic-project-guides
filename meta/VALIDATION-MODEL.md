# Validation Model

## Status

Authoritative for validation tiers and validation evidence concepts.

## Validation tiers

| Tier | Name | Purpose |
|---|---|---|
| 0 | Edit sanity | Formatting, schema checks, touched-file checks. |
| 1 | Focused validation | Affected project, component, spec-area, or shard validation. |
| 2 | Standard local validation | Normal repository local gate. |
| 3 | PR integration validation | Full CI or workflow integration validation. |
| 4 | Release validation | Package, public API, public docs, samples, consumer-surface, and release checks. |
| 5 | Human review validation | Human acceptance of milestone evidence when automation cannot decide. |

## Consumer-surface validation

A distributable artifact is not validated merely because its source project, internal assemblies, command handlers, or unpackaged executable pass tests.

When a repository produces an artifact intended to be consumed through a packaging, installation, publication, or generated-launcher boundary, required validation must include at least one acceptance path that consumes the artifact through the intended consumer mechanism.

Examples:

```text
NuGet library
  -> pack the current package
  -> consume/reference the packed package from an isolated consumer
  -> exercise representative public behavior

dotnet tool
  -> pack the current tool package
  -> install that exact package through dotnet tool using an isolated tool path or local tool manifest
  -> invoke the installed tool through the generated tool command/shim
  -> exercise representative command behavior and exit semantics

standalone executable
  -> publish/package the current executable
  -> invoke the published artifact rather than the build-project entry point
```

The consumer-surface path must use the artifact produced by the current build. It must not accidentally resolve a globally installed package/tool, stale package cache result, repository build output that bypasses packaging, or developer-machine-only state.

For a `dotnet tool`, packaged-tool acceptance should normally prove at least:

- installation from the locally produced package succeeds;
- the installed command/shim resolves;
- `--help`, `--version`, or an equivalent basic invocation works when such a surface exists;
- at least one representative successful command executes through the installed tool;
- invalid invocation or failure exit semantics are exercised when they are part of the public contract;
- representative artifact/file I/O is exercised through the installed tool when that is a material product capability;
- execution does not depend on repository-relative source/build paths or unrelated global installation state.

Do not run every internal test through the packaged surface. Use internal/unit and direct integration tests for detailed behavior, then keep consumer-surface acceptance small and representative.

If a milestone changes package metadata, installation behavior, command discovery/routing, startup composition, executable packaging, public command behavior, or dependencies that affect a distributable surface, planning and completion validation must include the applicable consumer-surface path.

Consumer-surface validation is evidence about the distributable product boundary. It complements rather than replaces lower-tier unit, integration, and repository validation.

## Tier 5 scope

Tier 5 is milestone-scoped.

It is not a perpetual project quality gate.

A Tier 5 review:

- is declared by one milestone;
- evaluates evidence produced for that milestone;
- may block that milestone's completion;
- becomes historical evidence after completion;
- is not revalidated after unrelated future changes.

Later milestones declare their own Tier 5 requirements when appropriate.

## Resumable validation

Long automated validation may use independently executable shards, atomic fingerprinted receipts, and a fast aggregate verifier.

Validation receipts and human review records serve different purposes:

```text
validation receipt
  machine evidence that a bounded automated shard passed for a defined input state

human review record
  historical evidence that a human accepted milestone evidence at completion time
```

Automated receipts may become stale when their validation inputs change.

Completed human review records do not become stale under the generic model.
