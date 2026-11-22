# Planning Handoff Transport Model

## Scope and authority

This model governs delivery of repository-relative planning artifacts: ready milestones, referenced project authority, and planner-seeded obligation ledgers for substantive work. Git commits and ZIP overlays are **transports**, not additional sources of requirements or implementation authority. Both must preserve the same milestone contract, obligation completeness, review/validation boundaries, and implementation independence.

## Git-native handoff

When authorized target-repository Git access exists, prefer committing **planning-owned** changes to a dedicated planning branch from the intended repository base. Honor an explicitly assigned branch or authorized default-branch write. Do not infer such authorization from credentials or create a branch before an empty repository has an initial commit. Changing transport does not permit unrelated source, test, CI, or product-implementation edits.

Declare a milestone `ready` only once the planner has seeded its material obligations where applicable. Record the **exact accepted planning commit SHA**, repository, branch, primary milestone path, and intended implementation-branch relationship in the *handoff report*. Do not attempt to record a commit's own SHA inside that same commit (self-reference). A branch name or PR link alone is not an immutable planning baseline.

Implementation may continue on the authorized planning branch **from that accepted commit** or branch separately **from the same exact commit**. If the branch has advanced before pickup, inspect changes affecting the milestone, seeded ledger, or referenced authority and explicitly reconcile a new accepted baseline before relying on them; do not silently treat the moving head as the agreed handoff. Preserve unrelated existing work. Committing planning, opening a planning PR, approving/merging it, and beginning implementation are distinct decisions. None is implied by selecting Git transport.

## ZIP handoff

When Git write access is unavailable/inappropriate, or a ZIP is specifically requested, provide a repository-relative overlay containing only the files permitted by the selected workflow. Identify the intended target repository/base revision **when known**, the primary milestone path, and application instructions for file additions, moves, and deletions. Do not keep obsolete files merely because a ZIP cannot express deletion directly. Do not invent a Git commit SHA if no commit was created.

After the recipient applies the ZIP to the intended repository state, the resulting ready milestone, referenced authority, and seeded ledger constitute the *same semantic contract* as a Git delivery. The archive and application notes do not become another source of requirements or replace the canonical implementation prompt.

## Direct changes without a milestone

Guide adoption/updates and documentation synchronization may be straightforward **direct changes**. They require no manufactured ready milestone, obligation ledger, or implementation handoff. For Git, report the actual resulting commit SHA and changed files; this is a change record, not a separate implementation baseline. For ZIP, report the applicable base if known and any application instructions.

## Verification

Confirm that delivered repository-relative files, required obligation rows, and project authority are consistent. Report Git repository, branch, **exact accepted commit**, milestone path and optional PR; or ZIP, intended base when known, and application instructions. The handoff contract does **not** introduce evidence-case mappings, receipts, additional approval gates, publication, or release qualification.
