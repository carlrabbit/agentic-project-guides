# Migration — Guide System 1.0.0 → 1.0.1

**Classification:** Patch clarification of implementation readiness and verification feasibility. No mandatory product-repository restructuring or retrospective rework of completed milestones.

1. After `v1.0.1` is published, update the **complete unmodified** repository-local `.guide/system/` snapshot from that tag and in the same change set `.guide-profile.json`'s `guideSystem.version`, `tag`, `revision` (peeled commit SHA), and any applied shared profile versions. Preserve local-profile versions and normal project authority.
2. For **new substantive milestones**, investigate the intended executor's actual tools/OS/runtime, permissions, and accessible execution locations sufficiently to make implementation and focused milestone verification credible. Distinguish verified access from documented or assumed capabilities, and critically review the draft before `ready`.
3. For **already ready but not completed** milestones, revisit feasibility only when there is a material reason to suspect implementation or milestone verification cannot run as planned (for example, missing SDK/runtime, unavailable CI/desktop session, or unauthorized integration target). Reconcile material changes with planning. Do not automatically rewrite every active milestone or its ledger.
4. For newly confirmed planning or earlier-review oversights, the review workflow may start a project-local `docs/agent-feedback/planner.log` with one concise entry per miss. Do not create an empty file or backfill completed milestones; the log is for retrospective learning, not a readiness or acceptance gate.
5. No change to the planner-seeded obligation ledger for substantive milestones, acceptance identities, bounded implementation experimentation, or release-qualification policy. No new environment inventory, evidence cases, validation receipts, or per-obligation test mappings.

A straightforward snapshot/metadata upgrade may be made directly under the guide update workflow. This patch does not require a migration milestone solely for changing the guide pin.
