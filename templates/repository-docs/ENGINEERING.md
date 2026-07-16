# Engineering

## Canonical command interface

`eng/` is the stable engineering API.

Platform launchers remain thin. Complex logic belongs in tested application code.

## Validation tiers

| Tier | Purpose |
|---|---|
| 0 | Edit sanity |
| 1 | Focused validation |
| 2 | Standard local validation |
| 3 | PR integration validation |
| 4 | Release validation |
| 5 | Human review validation |

## Validation execution modes

```text
direct
resumable-sharded
CI-only
human-review
```

## Human review commands

When activated:

```text
./eng/review-list.sh
./eng/review-request.sh
./eng/review-record.sh
./eng/review-check.sh
```

## Resumable suite contract

When activated:

```text
./eng/<suite>.sh --list
./eng/<suite>.sh --plan-json
./eng/<suite>.sh --shard <id>
./eng/<suite>.sh --verify
```

Aggregate success is established by `--verify`, not by partial output from a long wrapper.
