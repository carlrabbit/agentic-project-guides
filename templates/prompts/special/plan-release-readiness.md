# Prompt — Plan a Release Readiness Milestone

Create a release-readiness milestone package for:

\`{milestone}\`

Use the current guide methodology for planning; implementers must not need the external guide or planning conversation. The package may be committed directly to the requested branch or supplied as a repository-relative ZIP. Never publish merely because release readiness was requested.

## Distinct release boundary

Release qualification is a deliberate **release-candidate** activity, not a validation gate inherited by every feature milestone. A release milestone establishes confidence in the integrated candidate **as actually consumed and supported**.

Identify the target version, candidate commit/artifacts, supported distribution mechanism, intended consumers, supported platform/runtime matrix, relevant public contracts, and release/publish decisions. Distinguish qualification from publication.

Read the minimum relevant product authority: README, AGENTS, release/packaging engineering policy, API/compatibility baselines, public documentation/examples, candidate build config, directly relevant completed milestone evidence, and existing CI/installation scripts. Resolve important profile/scope and real-runtime details without making implementers read selection metadata.

## Ready release contract

Use the ordinary milestone template, with release-specific content:
- **Goal:** exact candidate/version and supported distribution surfaces.
- **Invariants:** required API, persisted data, public CLI/configuration, platform/security and compatibility commitments.
- **Scope:** packages/executables, documentation, examples, installers, relevant integrations; exclude publication unless specifically requested and authorized.
- **Acceptance:** small number of meaningful final-candidate outcomes, not one case for every internal requirement.
- **Qualification:** actual package or installed artifact, representative real consumer behavior, critical runtime/integration behavior, platform/compatibility and failure scenarios proportional to risk.
- **Authority:** execution loci, platform and credential permissions, clean isolation, and required human approval when actually needed.

A release may legitimately need a richer validation plan than an ordinary milestone. Justify expensive gates by consumer consequence or release risk—not merely by artifact count or a historical test matrix.

## Consumer and compatibility evidence

Qualify the **current candidate artifact**, avoiding accidental resolution of developer build products, global installations, stale caches, or unpublished substitutions. Examples:
- NuGet library: packed package consumed by isolated client.
- .NET tool: local package installed through \`dotnet tool\` and invoked by generated command/shim.
- Standalone executable: published executable invoked outside the source-project run path.
- Generator: relevant compiled consumer and actual shipped package layout.

Cover important public command behavior, API/diagnostics, examples, and supported environments. Do not repeat all internal unit/integration tests through every consumer. Reuse applicable current milestone integration evidence if candidate inputs and behavior remain equivalent; rerun checks whose results can no longer establish the final candidate.

Integration depth and execution locus are independent. Real-boundary validation may happen on a workstation while publication uses CI. Missing required targets are blockers, not license to create new CI infrastructure without authorization.

## Cost and completion

Prefer direct scripts and focused consumer smoke scenarios. Resumable shards, receipts and aggregate verifiers are **opt-in** for demonstrably expensive execution, not mandatory simply because this is release readiness. Formal human review is explicitly scoped to this release milestone when required.

The release milestone closes when its declared candidate qualification is credibly met, required artifacts/docs are prepared, and approvals are resolved. Publication remains a separately authorized action. Record passed checks, known limitations, and any unqualified supported surface clearly.

Do not seed a mandatory \`.execution/\` ledger, acceptance/evidence-case registry, or one-to-one proof table. A lightweight progress note is optional for long release qualification.

## Deliverable

Prepare the primary ready milestone and only essential new/updated project authority, release documents, migration items, or review requests. Do not include product implementation, generated packages, copied guide docs, broad unrelated cleanup, or speculative CI pipelines.

Report the milestone location, target/version, actual required qualification targets and loci, known constraints, publication boundary, and requested transport/PR or ZIP path when available. Use the canonical implementation prompt for subsequent execution.
