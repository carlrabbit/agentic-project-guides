# Migration — Guide System 1.0.0 → 1.1.0

**Classification:** Minor release. It changes when a substantive milestone counts as `ready`, and adds milestone amendments, two ledger statuses and an optional planner feedback log. No product-repository restructuring and no rework of completed milestones.

1. After `v1.1.0` is published, update the **complete unmodified** repository-local `.guide/system/` snapshot from that tag. In the same change set, update `.guide-profile.json`'s `guideSystem.version`, `tag`, `revision` (peeled commit SHA) and any applied shared profile versions. Keep local-profile versions and normal project authority unchanged.
2. **New substantive milestones** follow the 1.1.0 readiness rules in `meta/MILESTONE-EXECUTION-MODEL.md` and `meta/VALIDATION-MODEL.md`: confirm the intended executor can implement and verify the work where it runs (labeling capabilities checked, documented or assumed), resolve quality-critical design and verification decisions, and review the draft before `ready`.
3. **Ready but not completed milestones:** revisit only when there is a concrete reason to doubt readiness, for example a missing SDK or runtime, an unavailable CI runner or desktop session, an unauthorized integration target, an open quality-critical decision or too-coarse obligations. Reconcile material changes with planning. Do not rewrite every active milestone or ledger.
4. **Existing ledgers** stay valid. Use the new `reopened`/`superseded` statuses and the *Amendments* section of `templates/milestones/execution-ledger-template.md` only when a planning amendment changes obligations.
5. **Planner feedback log (optional):** the review workflow may start `docs/agent-feedback/planner.log` with its first qualifying entry. To use another path, state it in `docs/PROJECT-GUIDANCE.md`. Do not create an empty file or backfill completed milestones.

A straightforward snapshot and metadata upgrade may be made directly under the guide update workflow; changing the guide pin alone does not require a migration milestone.
