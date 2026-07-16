# Prompt — Plan an AI-Executed, Human-Reviewed Milestone

Create an implementation-ready package for:

```text
{milestone}
```

Execution mode: `ai-executed-human-reviewed`.

The milestone must declare:

- repository role and maturity;
- scope and non-goals;
- coherent AI-sized focus areas;
- authority documents;
- validation tier;
- validation execution mode: direct, resumable-sharded, CI-only, or human-review;
- concrete validation commands;
- human review applicability, class, evidence, blocking point, and completion criteria;
- direct documentation impact;
- deferred `.guide-sync/pending/` hints.

If validation may exceed an agent runtime budget, require a resumable suite with `--plan-json`, bounded shards, receipts, and `--verify`.

Generate a filled execution prompt in chat for the later implementation agent.
