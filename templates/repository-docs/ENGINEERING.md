# Engineering

## Human review commands

When the human-review module is active:

```text
./eng/review-list.sh [--milestone <id>] [filters]
./eng/review-show.sh <review-id-or-alias>
./eng/review-request.sh --milestone <id> ...
./eng/review-record.sh <review-id-or-alias> <decision> ...
./eng/review-reopen.sh <review-id-or-alias> ...
./eng/review-check.sh --milestone <id>
```

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
