# Planning Artifact Transport and Handoff Model

## Scope and authority

Planning produces repository-relative artifacts that establish a ready milestone and any necessary project authority. For AI-executed milestones this includes the planning-seeded `.execution/<milestone-id>.md` ledger. The ready milestone and explicitly referenced project authority are the **semantic contract**; the ledger is non-authoritative operational coverage state. Transport is never another source of requirements.

This model applies to normal milestone planning, project bootstrap, guide adoption/update, specialized milestone planning, and documentation handoff workflows that produce repository-relative changes. Each canonical prompt controls which files may be authored; changing transport does not expand planning into implementation.

## Delivery modes

Choose the mode based on actual repository access and the assigned handoff, not on model capability.

### Git-native planning branch (preferred when authorized and available)

- Inspect the target repository and its intended base; create a dedicated planning branch from the correct base commit. Do not write directly to the default branch unless explicitly authorized.
- Commit **only planning-owned** new, updated, moved, or deleted repository-relative artifacts. Do not make source, test, generated-code, pipeline, or other implementation edits merely because Git transport permits them.
- Complete the milestone and seed/verify the execution-ledger coverage *before* declaring it ready. Preserve unresolved blockers as not ready.
- Provide the repository, branch, exact **planning-baseline commit SHA**, primary milestone path, affected files, and concise implementation handoff. Link a PR when one is created; a PR is not inherently a prerequisite for implementation unless project policy or the assignment requires it.
- The implementation agent starts from that planning commit and current target-repository authority. It may continue on the planning branch or create a separate implementation branch **from that exact commit**. Decide the branch topology in the handoff; never infer an immutable baseline from a branch name after implementation has advanced.
- Do not conflate committing a ready planning package, opening a planning PR, approving/merging that PR, or implementing the milestone. These are distinct actions; do not merge or start implementation unless assigned.
- If the branch changes between planning and executor pickup, reconcile the relevant changed authority/ledger/contract and identify the new accepted baseline before proceeding; do not silently treat the old handoff as current.

### Repository-relative ZIP overlay (for disconnected or unavailable Git write access)

- Supply an archive containing only the files the workflow permits and preserve the paths they will have in the target repository.
- Identify the target repository/base revision if known, the primary milestone path, and any required application instructions for moves or deletions. Do not preserve obsolete files simply because a ZIP cannot express deletion directly.
- Applying the overlay to the correct target revision must establish the **same ready milestone, referenced authority, and seeded ledger** as a Git delivery. The executor then implements from the applied repository state.
- A ZIP does not become project authority, and an overlay application note must not redefine the milestone or duplicate the canonical execution methodology.

## Transport-independent acceptance

Both modes must ensure:

1. The planning/implementation boundary, project authority, research status, allowed file types, and review/validation obligations are unchanged.
2. The ready milestone identifies the operative authority and is usable without the planning conversation or external guide repo.
3. AI-executed milestones contain a lossless planning-seeded ledger, with exact obligation/evidence-case ID reconciliation and declared gates.
4. The recipient knows which repository revision or applied-overlay state is the planning baseline, which milestone to open first, and any material unresolved handoff constraints.
5. Handoff reporting uses a **commit/branch/optional PR URL** for Git or an **archive link/application notes** for ZIP, followed by the workflow's normal file inventory, authority/evidence, and execution details.

The mode is a delivery choice, not a new guide profile, milestone execution profile, approval gate, or alternative implementation contract.
