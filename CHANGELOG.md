# Changelog

## 0.5.0

Migration required: conditional.

Affected areas:

- validation execution;
- agent runtime constraints;
- engineering command host;
- milestone planning and execution prompts;
- validation reporting.

Added:

- `meta/CONSTRAINED-EXECUTION-MODEL.md`;
- resumable validation suite model;
- validation receipt and plan templates;
- ADR-0014 through ADR-0018;
- migration from v0.4.0 to v0.5.0;
- prompt rules for sharded execution and fast verification.

Conditional migration:

- convert aggregate validation commands that may exceed agent runtime limits;
- expose `--list`, `--plan-json`, `--shard`, and `--verify` modes;
- add atomic, fingerprinted receipts;
- move non-trivial receipt and fingerprint logic into tested .NET code.

Deprecated:

- one long process as the only proof of aggregate validation;
- claiming aggregate success from partial logs;
- attempting to escape a hard execution harness lifetime with `nohup`, backgrounding, `setsid`, or larger shell timeouts.

## 0.4.0

Migration required: conditional.

Added:

- `meta/HUMAN-REVIEW-MODEL.md`;
- `meta/ENGINEERING-COMMAND-MODEL.md`;
- repository-local `.review/` model;
- review command templates;
- thin cross-platform launchers over shared .NET engineering implementation;
- ADR-0009 through ADR-0013;
- migration from v0.3.0 to v0.4.0.

Conditional migration:

- activate `.review/` when Tier 5 human review is used;
- move complex shell logic into tested .NET commands;
- add PowerShell launchers only when native Windows is an actively tested platform.

## 0.3.0

Added execution handoff prompts and generic latest-version migration/adoption prompts.
