# Migration — Guide System v0.9.3 to v0.9.4 (draft)

## Purpose

Remove mandatory ZIP-only planning-package delivery. Git-native, committed planning artifacts and repository-relative ZIP overlays now carry the same ready milestone contract.

## Migration required

No repository migration by default. Update the guide version in `.guide-profile.json` when adopting v0.9.4, and use the new delivery rules for future planning tasks.

Existing ready, implementing, and completed milestones remain valid. No obligation, evidence-case, validation, or execution-ledger reconstruction is required merely because transport options changed.

## Conditional updates

If project-local planning automation, setup scripts, or an `AGENTS.md` handoff instruction requires a ZIP regardless of access, replace that transport assumption with the equivalent two-mode rule, only where it is operative. Preserve repository-specific policy if the project intentionally requires archives or gates planning changes through a PR.

For an authorized Git-native handoff:

1. Establish a dedicated planning branch from the intended project base.
2. Commit only planning-owned files, including the ready milestone and its planning-seeded ledger where required.
3. Record the exact planning-baseline commit SHA, branch, primary milestone path, and optional PR URL.
4. State whether implementation continues on that branch or forks from that exact commit; never treat a moving branch name as the frozen baseline.

For a disconnected ZIP handoff, keep repository-relative paths, target revision/application instructions, and explicit handling for moves/deletions. Do not use the archive as separate authority.

## Compatibility and authority

The planning/implementation boundary, allowed planning files, project-truth authority, research non-authority, execution-ledger coverage, and milestone validation/human-review gates are unchanged. No new profile or execution mode is introduced.

The release contract is `meta/HANDOFF-TRANSPORT-MODEL.md` and the current canonical planning prompts. Historical version-specific prompt snapshots are not retroactively edited.

## Completion

Verify the project can deliver future planning artifacts through an authorized Git branch or ZIP overlay without implementation having to reconstruct planning context, and that any modified local handoff entrypoint names the primary milestone and immutable Git commit or properly applied overlay state.
