# Base Engineering Guide

## Core principles

```text
eng/ is the stable engineering API.
Commands are canonical.
Validation is tiered.
Long validation can be resumable.
Launchers stay thin.
Complex orchestration lives in tested code.
Platform support is explicit and tested.
Human review is repository-local when activated.
```

## Recommended commands

```text
./eng/restore.sh
./eng/build.sh
./eng/test.sh
./eng/check.sh
```

Optional review commands:

```text
./eng/review-list.sh
./eng/review-request.sh
./eng/review-record.sh
./eng/review-check.sh
```

Optional resumable validation suite commands:

```text
./eng/<suite>.sh --list
./eng/<suite>.sh --plan-json
./eng/<suite>.sh --shard <id>
./eng/<suite>.sh --verify
```

Use a .NET engineering command host when shell launchers would otherwise own workspace semantics, fingerprinting, receipt validation, review state, or complex structured data processing.
