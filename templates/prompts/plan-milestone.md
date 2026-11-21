# Prompt — Plan Milestone

Convert the requested capability into a ready milestone for a disconnected implementation agent:

\`{milestone}\`

Use \`carlrabbit/agentic-project-guides\` as **planning** methodology. Do not copy guide documents into product repositories or require ordinary implementers to read this guide.

## Objective: agent-scaled, coherent delivery

Plan the **largest coherent capability economical to implement and evaluate**, not the smallest human-sized vertical slice. A milestone may implement an entire subsystem, cross-cutting feature, or structural migration. Do not split merely because many edits or tests are involved.

Explicitly distinguish **reversible implementation uncertainty** (cheap to experiment, discard, and retry) from **consequential risks** (irreversible data, security, public/persisted compatibility, operational impact). Prefer enabling experimentation to preemptively shrinking reversible work. Split or stage only where independent outcomes, meaningful boundaries, unresolved material decisions, or expensive failure consequences justify it.

Optimize planning + implementation + validation + review + expected rework. Avoid process artifacts without demonstrated value.

## Planning authority and repository inspection

Inspect enough of the target repository to understand applicable project truth:
- \`AGENTS.md\`, \`README.md\`, relevant specs, engineering rules, architecture, decisions, milestones, and representative source/tests;
- \`.guide-profile.json\` for applicable shared profiles, semantic scopes, execution metadata, and repository role;
- \`docs/PROJECT-GUIDANCE.md\` and registered \`.guide/profiles/<id>/PROFILE.md\` for project-local planning extensions;
- focused \`docs/research/\` only when relevant to material open questions;
- review or sync metadata only if relevant to this assignment.

Resolve applicable base/shared/local profiles and conflicts through concrete project authority. Do not invent a new central profile to express one SDK, runtime choice, or test strategy. Research is planning evidence, never active implementation authority. Promote durable, implementation-affecting conclusions to normal project truth.

Planning owns target capability, meaningful architectural/semantic/compatibility decisions, invariants, scope, acceptance, exceptional validation/review, and authorization for any non-routine environment changes. Do not make detailed file lists or patch steps a prerequisite for \`ready\`.

## Ready milestone contract

Produce a single primary milestone following \`templates/milestones/milestone-template.md\` with:

1. **Goal / target:** the observable capability and why it belongs together.
2. **Architecture and invariants:** settled material decisions and preserved contracts.
3. **Scope / exclusions:** inclusion and non-goals without a speculative edit allowlist.
4. **Acceptance:** concise, verifiable outcomes covering the complete capability.
5. **Validation:** a small, credible set of focused tests and representative integration behaviors; identify material consequence risks and checks deferred to release.
6. **Required authority and exceptional obligations:** only where they matter, including direct docs, local specializations, permissions, or required human judgment.

Acceptance is mandatory; **a distinct test/evidence case per criterion is not**. Do not produce a mandatory \`.execution/\` ledger, evidence-case registry, receipt plan, gate matrix, or immutable proof artifact. An optional lightweight progress/resume ledger may be prescribed only where long-running execution needs it.

Make the contract complete for the project's baseline executor without relying on planning chat history or reading the guide. Do not reduce a coherent milestone merely because implementing it may be lengthy; the implementer can decompose and resume work internally.

If a **material project decision** really cannot be made without evidence, research it or plan a focused diagnostic investigation. Do not treat cheap alternative implementation trials as an unresolved planning decision.

## Validation policy

Use \`meta/VALIDATION-MODEL.md\`:
- During implementation: affected build, static feedback, targeted tests.
- At milestone completion: focused behavioral checks and a few representative integration fixtures; review architecture and invariants.
- At release: final package/installed tool/real consumer, compatibility, broader operational and platform qualification where required.

A real integration boundary may matter at milestone stage even when installed-product qualification does not. State exceptional earlier consumer tests only where packaging/installation is itself the milestone outcome, project authority mandates it, or the risk of deferring is material.

Do not make a general test matrix from every acceptance clause. Reuse relevant current evidence; do not add fingerprinting/sharding infrastructure unless repeated validation cost justifies it. Use the target/locus/platform detail necessary for meaningful real-boundary checks; integration need not run in CI. Authorized execution is not permission for new machine software or CI infrastructure.

For reviews/corrections, prefer concrete defects and minimal focused rechecks. Never pre-author a policy that every correction must grow the validation contract.

## Project documentation and transport

Update engineering/specification/decision authority only when required to fix project truth. Add \`.guide-sync/pending/\` hints only for genuinely deferred documentation changes. Do not duplicate the implementation prompt in the package. Project-local planning research is optional and non-authoritative.

A milestone package may be written **directly into a branch/repository** or delivered as a ZIP containing repository-relative files, depending on the user's delivery request and available capabilities. ZIP is not a universal requirement. It is a transport mechanism, not a second source of authority.

Provide the primary milestone path, affected authority documents, any applied changes/transport instructions, key validation expectations, explicitly deferred release checks, human-review obligations if any, and a concise handoff using \`templates/prompts/execute-milestone.md\`. Do not promise a file artifact or PR that has not been created.

## Readiness check

Before marking \`ready\`, verify:
- material architectural, semantic, compatibility, security, and scope choices are resolved;
- the outcome is coherent and appropriately ambitious for agent execution;
- acceptance is observable and covers the actual requested capability;
- validation is proportionate and release qualification is properly separated;
- any required external target/authority is real and authorized;
- an implementer can act independently using the ready milestone and project truth;
- no mandatory ledger, validation-host, receipt, or human-review ceremony has been introduced without a specific justification.

Do not confuse implementation uncertainty with missing project policy. Return genuinely material unresolved decisions to planning.
