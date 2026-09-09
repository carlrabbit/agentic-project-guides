# Engineering

This document contains project engineering truth. Fill only sections that are active for this repository.

## Test strategy

State the repository's actual strategy when it is a material project rule, for example:

```text
integration-first
balanced
unit-focused
scenario/artifact-first
```

Do not inherit a generic test pyramid implicitly.

## Validation topology

For material validation obligations, record the applicable:

| Depth | Target | Locus | Platform/capability | Command | Evidence |
|---|---|---|---|---|---|
| <Tier> | <real boundary> | <local/CI/remote/mixed> | <requirements> | <command> | <evidence> |

Integration depth does not imply CI execution.

## Project-specific integration targets

When correctness depends on an external runtime, installed application, service, real database, browser, native subsystem, or similar target, define or reference the project-local specialization needed by implementation and validation.

Resolve as applicable:

- target and supported version/range;
- availability and required platform/capabilities;
- provisioning/connection;
- isolation and reset/cleanup;
- identity/secrets/permissions;
- repository command used to invoke validation;
- expected evidence;
- infrastructure versus product failure semantics;
- fallback validation when the target is unavailable;
- release and consumer-surface relationship.

Use a focused `docs/engineering/<topic>.md`, spec, architecture document, or decision record when this becomes too detailed for this file. Do not copy the external guide's specialization model into the repository.

## Human review commands

When the human-review module is active, expose the repository's supported launcher(s). Example bash surface:

```text
./eng/review-list.sh [--milestone <id>] [filters]
./eng/review-show.sh <review-id-or-alias>
./eng/review-request.sh --milestone <id> ...
./eng/review-record.sh <review-id-or-alias> <decision> ...
./eng/review-reopen.sh <review-id-or-alias> ...
./eng/review-check.sh --milestone <id>
```

Equivalent PowerShell or other supported launchers may be used. Do not imply platform support merely from an example launcher.

Human review is a completion gate for the milestone that owns the request.

`review-check` must be run with explicit milestone context. It validates only that milestone's required reviews.

Completed review records are historical evidence. They are not revalidated after later commits and are not a perpetual project-wide quality gate.

`review-list` may display ephemeral numeric aliases and write an ignored alias map under:

```text
artifacts/review/session/aliases.json
```

Aliases are only short-lived interactive conveniences.

Canonical review IDs are required in automation, milestones, requests, records, and committed artifacts.

A stale alias must fail and instruct the human to run `review-list` again.
