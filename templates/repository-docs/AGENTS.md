# Agent Instructions

## Default implementation path

Read:

- `docs/ENGINEERING.md`;
- the relevant milestone or task;
- authority documents listed by that milestone;
- relevant source and test files.

Use canonical `eng/` commands only.

## Coordination metadata

During ordinary implementation, ignore unless explicitly in scope:

- `.guide-profile.json`;
- `.guide-sync/`;
- `.review/`.

Read `.review/` only when the milestone activates Tier 5 review, requests review evidence, or requires review validation.

## Constrained execution

When a validation command exposes `--plan-json`, do not run its long aggregate mode in a constrained agent environment.

Run each planned shard in a separate invocation and finish with `--verify`.

Do not claim aggregate success from partial logs.

Do not attempt to bypass execution limits with `nohup`, backgrounding, `disown`, `setsid`, or shell timeout changes.

## Do not

- invent commands;
- broaden scope;
- perform broad documentation synchronization unless requested;
- treat external guide documents as repository authority;
- put complex project semantics into shell launchers.
