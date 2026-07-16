# Validation Model

Validation is explicit, tiered, and appropriate to execution mode.

| Tier | Name | Purpose |
|---|---|---|
| 0 | Edit sanity | Formatting, schema, and touched-file checks. |
| 1 | Focused validation | Affected project/component/spec-area validation. |
| 2 | Standard local validation | Normal local repository gate. |
| 3 | PR integration validation | Full CI/workflow validation. |
| 4 | Release validation | Package, public API, public docs, samples, and release checks. |
| 5 | Human review validation | Human acceptance of artifacts, semantics, visual quality, UX, security, or creative decisions. |

Validation execution mode must also be declared when relevant:

```text
direct
resumable-sharded
CI-only
human-review
```

Long suites that may exceed agent runtime limits should use resumable shards, fingerprinted receipts, and a fast verifier.
