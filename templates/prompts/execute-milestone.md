# Prompt — Execute Milestone

You are the implementation agent for a **ready** milestone. Implement the capability and close the milestone without redoing planning.

Start here: `{primary-milestone-path}`

## Read

1. Read the primary milestone and **only** the project authority it references.
2. Inspect the live source, tests, relevant `AGENTS.md`, and documented engineering commands.
3. Read an optional `.execution/<milestone-id>.md` only when provided or useful for resuming long work.

The ready milestone and actual project authority govern. Planning chat, external guide repository, guide selection metadata, or research archives are not required implementation input. Research is non-authoritative except as explicitly relevant evidence.

## Implement at agent scale

Own the concrete implementation: architecture *within resolved constraints*, types, files, algorithms, sequence, tests, and supporting edits. Prefer a coherent capability to artificial mini-slices. Large edits and broad but related refactorings are acceptable.

You may build disposable prototypes, compare approaches, reverse a failed implementation, and try another **within the milestone's goal, invariants, and environment authorization**. When planning deliberately delegates reversible architectural alternatives, evaluate them against the agreed criteria and preserve the chosen result without changing settled public contracts. Avoid unrelated expansion. You do not need planning approval for local implementation choices or implementation-derived decomposition.

Escalate only a **material unresolved project decision** affecting required architecture, semantics, public/persisted compatibility, scope, acceptance, safety, validation authority, or specialization. Explain the decision and discovered evidence. Do not treat implementation difficulty alone as a reason to stop.

Preserve existing work. Do not assume technical access permits persistent software installation, CI workflow changes, secret changes, or infrastructure provisioning; use documented project authority.

## Validation during implementation

Run the cheapest feedback that catches the current plausible defects. Build affected code, use targeted tests, and use small investigations when productive. Do not rerun complete validation after every edit.

Near completion, run focused automated tests and a few representative integration scenarios that exercise the milestone's meaningful behavior and failure modes. Where a real database/runtime/browser/process boundary defines correctness, exercise that boundary with appropriately sized fixtures.

**Do not perform release qualification by default.** Installed/package consumer smoke tests, full compatibility suites, real repository dogfood, or final distribution verification belong to release readiness unless explicitly in scope for this milestone for a justified reason. Existing current evidence may be reused when still applicable.

Avoid introducing validation infrastructure merely to orchestrate checks. A direct test command or small `eng/` script is normally sufficient. Expensive sharding, dependency fingerprints, receipt caches, evidence-case registries, and aggregate verifiers are optional.

Exploratory/nondeterministic tests do not automatically enter the default suite.

## Completion, review, and correction

Review the resulting repository against the milestone's **entire acceptance contract** and invariants; tests alone cannot certify unexercised behavior. Check explicitly required artifacts, migrations, documentation, and material residual risks.

Write a **brief durable completion note** in the milestone (or its project-defined completion record) covering delivered behavior, tests actually run/results, important limitations, and release checks deferred. Also summarize this in the final report. Do not turn the note into a criterion-by-criterion proof ledger. No mandatory acceptance-to-evidence table, ledger set equality, immutable completion proof, or independent reviewer sign-off is implied.

When correcting a defect, implement the repair and perform the smallest credible focused verification. Add a small permanent regression test when a reproducible defect is likely to recur and the test is economical; do not persist every one-off diagnostic. Do not expand acceptance or construct additional gates without a demonstrated material risk. If the prior validation strategy is excessive, reduce it rather than preserving sunk process costs.

If the milestone explicitly requires a human decision, stop at that gate; never fabricate approval.

## Outcome

Begin the completion report with one of:

- `Milestone status: COMPLETE` — acceptance met and milestone-level validation credible.
- `Milestone status: AWAITING HUMAN REVIEW` — only an explicit human decision remains.
- `Milestone status: BLOCKED` — an actual external dependency or unresolved material decision prevents completion.

Then state: implemented outcome; significant files/architectural changes; focused validation commands, target/locus where relevant, and results; known limitations and **deferred release qualification**; direct documentation changes; and any real blockers or review requests.

Ordinary failing tests, fixable defects, or incomplete source edits are work to resolve, not reasons to claim `BLOCKED`. Do not report `COMPLETE` on compilation alone when required behavior has not been established.
