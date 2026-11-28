# Prompt — Review a Milestone Implementation and Prepare Focused Corrections

Review the implementation or pull request for:

`{milestone-or-pr}`

Use the ready milestone, its referenced project authority, changed code/tests, relevant existing checks, and—for substantive work—the planner-seeded `.execution/<milestone-id>.md` obligation ledger. When an exact accepted planning-baseline commit is supplied, distinguish that handoff from later branch/PR changes and check material contract changes were reconciled rather than silently substituted. This is **engineering review**, not automatically a formal human-acceptance gate. Do not require the implementation agent to read the pinned guide snapshot or external upstream repository.

## Objective

Determine whether the intended **whole coherent capability** is delivered within its authorized change boundaries. Examine intended behavior, expressly permitted consequences, protected invariants, related modes/integrations, architecture, documentation, and plausible defects. A build or green happy-path suite does not establish that protected boundaries survived; look for high-information boundary or cross-mode evidence where material. Do not treat intentionally permitted breakage as a defect, nor require an exhaustive test matrix.

For a substantive milestone, compare the ledger's stable obligation IDs with the ready milestone, and inspect whether **each material deliverable is actually present**. A `done` status without the deliverable is not completion; a missing or compressed obligation is a real handoff defect. This is completeness accounting, not a requirement for one test or proof artifact per row.

Review at agent scale. Do not penalize a broad but coherent change merely because it contains many edits or would be large for a human team.

## Findings

For each actionable finding, give:
- the concrete defect and relevant file/location;
- its observable consequence or contract violation and severity;
- the **smallest credible focused verification** of its correction.

Distinguish actual defects from stylistic suggestions, speculative risks, and release-only qualification. Prioritize by consequence and likelihood, not number of missing evidence cases. Do not turn every acceptance clause into a new test, validation gate, or proof row.

## Corrections without process inflation

If asked for a correction prompt, direct the implementer to fix **all substantiated findings** within the existing milestone contract, using focused tests and small representative integration fixtures. Do not create new acceptance IDs, evidence-case registries, fingerprinted receipts, sharding systems, broad test matrices, or installed-consumer checks merely because a review found a defect.

Add a lasting regression test when a reproducible bug can plausibly recur and a small deterministic check is economical. Otherwise a disposable focused check and review may be adequate. If inherited validation obligations are excessive, recommend deleting or reducing them; sunk effort is not a reason to preserve them.

Expand the milestone contract or require stronger validation **only** for a newly demonstrated material product risk, an explicit product requirement, or a truly changed public/integration boundary. Explain that justification. Package, installed-consumer, real-repository dogfood, and broad compatibility checks normally remain at release readiness.

## Correction planning and amendments

Apply *Correction discipline* and *Retrospective planner feedback* in `meta/MILESTONE-EXECUTION-MODEL.md`. In short:

- Before writing a correction, inspect the current milestone and any amendments, relevant project authority, the actual branch and ledger, and your findings. For material or recurring findings, classify the cause (clear instruction ignored, ambiguity or omission, wrongly delegated technical or verification design, wrong feasibility assumption, or obligations too coarse). Resolve missing decisions yourself, including nontrivial test oracles and boundaries, or define a bounded evaluation; do not just demand better implementation or tests.
- If the existing contract and obligations are sufficient, write a focused correction prompt.
- If a material decision changes, or corrective outcomes are not covered by the existing obligations, the correction needs a versioned **amendment**. Writing it is planning work: if you have planning and write authority for this milestone, you act as planner for the amendment and follow the planning rules; otherwise propose the amendment and its ledger changes to the planner instead of claiming they were applied. Obtain authority for scope changes. Keep the original handoff, existing obligation IDs and implementation progress, and reference the exact amended revision in a short execution instruction.

## Retrospective planner feedback (only if warranted)

If concrete later evidence shows a material omission in the **ready planning handoff** or an avoidable miss or overreach by an **earlier implementation reviewer**, add one line to the project's planner feedback log as the execution model describes. This applies even in a first review when it establishes that planning omitted a material requirement. Do not log ordinary implementation defects, unforeseeable failures, hypothetical risks, or entries that only show a review happened. In a read-only review, propose the line instead.

Report **Accept**, **Corrections required**, or **Blocked on material decision**. Cite exact evidence from code and checks for findings; acknowledge unverified areas without manufacturing defects. When corrections are required, provide a concise actionable correction prompt (or an amendment handoff when required) for the implementer and the specific focused rechecks. Do not require an independent approval subsystem unless the milestone explicitly needs human judgment.
