# Constrained Execution Model

## Purpose

Make repository validation resilient to agent environments with capped execution time, process-group cleanup, output limits, or short-lived command sessions.

## Core doctrine

```text
Agent execution environments may be short-lived.
Long validation must be decomposable into bounded shards.
Successful shards produce atomic, fingerprinted receipts.
Aggregate success is established by a fast verifier.
The repository must never infer success from partial execution output.
```

## Execution modes

```text
direct
resumable-sharded
CI-only
human-review
```

## Resumable suite interface

```text
./eng/<suite>.sh --list
./eng/<suite>.sh --plan-json
./eng/<suite>.sh --shard <id>
./eng/<suite>.sh --verify
./eng/<suite>.sh
```

No-argument mode may run all shards and then verify in unconstrained local or CI environments.

## Receipt location

```text
artifacts/validation/<suite>/<shard>.json
```

Receipts are generated evidence and are normally ignored by Git.

## Atomic success rule

```text
run shard
→ validate result
→ write temporary receipt
→ atomically move to final receipt
```

Killed, interrupted, timed-out, or failed shards must leave no valid passing receipt.

## Fingerprints

A receipt should identify:

- repository fingerprint;
- suite fingerprint;
- command fingerprint;
- input fingerprint;
- optional result fingerprint.

A safe default repository fingerprint combines:

- HEAD commit;
- tracked working-tree diff;
- relevant untracked files.

Exclude generated artifacts, `bin/`, `obj/`, temporary fixtures, and validation receipts.

## Verification

`--verify` must be fast and must not rerun tests. It validates required receipts, pass status, suite/shard identity, current fingerprints, and referenced artifacts.

## Agent behavior

In a constrained environment:

1. run `--plan-json`;
2. execute each shard in a separate invocation;
3. stop on real shard failure;
4. run `--verify`;
5. report verifier result;
6. never claim aggregate success from partial child output.

## Explicit non-solutions

The repository must not rely on these as remedies for a hard harness lifetime:

```text
nohup
backgrounding
disown
setsid
larger shell timeout
output redirection
heartbeat-only workaround
```

A repository cannot reliably escape an external process-group or cgroup lifetime from inside `eng/`.
