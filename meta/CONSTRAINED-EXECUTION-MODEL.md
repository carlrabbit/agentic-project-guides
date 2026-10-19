# Constrained Execution Model

## Purpose

Make repository validation resilient to agent execution limits and economically resumable when expensive validation has late failures. Independent stages are valuable even without timeouts.

## Core doctrine

```text
Agent execution environments may be short-lived.
Long validation must be decomposable into bounded shards.
Successful shards produce atomic, fingerprinted receipts.
Aggregate success is established by a fast verifier.
The repository must never infer success from partial execution output.
```

Validation stages are execution units, not milestone obligation IDs or evidence cases. Full validation can be a cheap direct command; do not require a generic staged framework for small suites.

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

No-argument mode may run all required missing/stale stages and then verify, or directly execute a cheap full suite, according to project policy. In a constrained environment, run each required shard in a separate invocation.

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

A safe **conservative fallback** repository fingerprint combines HEAD, tracked working-tree diff, and relevant untracked files, excluding generated artifacts and receipts. It may invalidate all stages after unrelated edits.

For expensive suites, project authority may define narrower stage-specific dependency fingerprints, covering relevant source and test code, stage command/harness, configuration and lockfiles, fixtures, toolchain/runtime/platform, environment assumptions, and upstream artifacts or prerequisite-stage results. Invalidate dependents when an upstream artifact changes. When dependency coverage is uncertain, widen the scope or rerun; never infer independence from filenames alone or fingerprint stage-generated artifacts circularly.

A passing receipt is reusable only when its full dependency contract matches current inputs, required target/locus and artifacts. Failed/interrupted runs cannot leave a valid passing receipt for current inputs.

## Verification

`--verify` must be fast and must not rerun tests. It validates required receipts, pass status, suite/shard identity, current fingerprints, and referenced artifacts.

Complete final evidence verification does **not** mean unconditional full-suite re-execution. Execute only missing/stale stages when safe evidence reuse is established; otherwise rerun conservatively. The final milestone audit still maps actual evidence to individual obligations/evidence cases. A final release artifact may impose a stricter fresh-validation contract.

For expensive validation, observe stage duration and significant setup/teardown cost. Avoid repeating process startup, restore and fixture/workspace initialization without weakening determinism or isolation. A universal cost budget, mandatory receipts and generalized cache engine are not required.

## Agent behavior

During implementation, use focused checks and rerun only affected expensive stages when valid stage-level reuse is available. For `--plan-json` suites in constrained environments:

1. inspect required stages and available valid receipts;
2. execute missing/stale shards separately and stop on real failures;
3. preserve unaffected passing evidence whose dependencies still match;
4. run `--verify` only when required evidence is complete;
5. report actual verifier results, never aggregate success from partial logs.

Investigative simulations/probes are separate from these authoritative receipts and are excluded from regular suites unless explicitly required as a milestone gate.

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
