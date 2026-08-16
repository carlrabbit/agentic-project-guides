# Guide System Migration — v0.6.0 to v0.7.0

## Purpose

Adopt the explicit two-phase milestone lifecycle introduced in v0.7.0 without rewriting valid project truth or introducing model-specific workflow rules.

## Core change

Coding milestone work is separated into:

```text
planning -> ready milestone -> implementation
```

Planning resolves material uncertainty and defines the implementation contract. Implementation derives concrete mechanics from the live repository.

This separation applies regardless of whether either phase is performed by a human, ChatGPT, Codex, another agent, or another model tier.

## Migration impact

Migration required: recommended for repositories using milestone-driven coding workflows; otherwise no-op.

Existing completed milestones are historical and need no conversion.

Existing active milestones may continue unchanged if already implementation-ready. When practical, normalize them to the v0.7.0 contract before implementation.

## Normalize active milestone contracts

For active coding milestones, ensure the implementation-facing milestone contains enough information to execute without the planning conversation:

- goal and target state;
- scope and non-goals;
- resolved architectural, semantic, compatibility, and scope decisions;
- constraints and invariants;
- required project authority;
- acceptance criteria;
- validation commands and execution mode;
- human-review gates when applicable;
- documentation policy and exceptional execution constraints when applicable.

Remove or avoid planning residue that is not needed for execution:

- rejected alternatives unless needed to prevent a known regression;
- planning-agent scratch notes;
- speculative file-by-file edit lists;
- predicted class or function changes that are not contractual;
- detailed implementation sequences the executor can derive from the repository;
- dependencies on the planning chat transcript.

## Planning workflow

Planning should inspect enough repository truth to resolve decisions safely.

Planning may create or update specs, architecture, decisions, or engineering documents when a conclusion must become durable project authority.

Planning may produce an overlay ZIP when repository-relative additions, replacements, moves, or deletions are needed before implementation. The overlay is transport, not separate authority.

A coding milestone becomes `ready` only when implementation can proceed without making a new material decision about architecture, semantics, compatibility, scope, acceptance, or validation policy.

## Implementation workflow

Implementation starts from the ready milestone and referenced project authority.

The executor re-inspects the live source and tests and owns concrete implementation mechanics that fit the contract.

Do not require the executor to read:

- the external guide repository;
- `.guide-profile.json` or `.guide-sync/` unless explicitly needed;
- planning transcripts;
- planning-agent scratch work.

If implementation discovers a material unresolved decision, stop the affected work and return the milestone to planning with the decision and evidence. Do not silently broaden or reinterpret the milestone.

## Execution modes

Retain existing execution modes. They remain orthogonal to lifecycle phase.

Do not add model names such as Sol, Terra, or Luna to durable milestone execution modes merely to adopt v0.7.0.

## Documentation migration

Do not rewrite project-truth documentation solely to describe the guide methodology.

Update repository-local agent or milestone workflow documentation only when it currently instructs implementation agents to perform architectural planning, reconstruct planning context, read the external guide system, or depend on detailed planning transcripts.

## Validation

After migration, verify that a fresh coding milestone can follow this path:

1. planning inspects the repository and resolves material decisions;
2. the ready milestone and referenced project authority contain the durable handoff;
3. a disconnected implementation agent can determine concrete edits from the live repository;
4. implementation can validate completion without the planning transcript;
5. material unresolved decisions have an explicit path back to planning.
