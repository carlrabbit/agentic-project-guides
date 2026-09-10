# Migration Model

Guide updates are applied through profile-aware migration planning, not vague implementation instructions.

Do not ask an implementation agent to simply "upgrade to the latest guide".

Use one of the stable planning entry points:

```text
templates/prompts/adopt-guide-system.md
templates/prompts/update-guide-system.md
```

The planning phase resolves the latest version explicitly from the guide repository, inspects the changelog and relevant migration documents, assesses the target repository, and produces a ready migration milestone or equivalent implementation-ready package.

Migration is a special planning workflow. It is not a milestone execution mode.

When migration requires coding or repository changes, the resulting work follows the normal lifecycle:

```text
planning -> ready -> implementing -> done
```

The execution profile for that milestone is selected independently from the migration workflow type.

## Migration flow

```text
1. Identify current guide profile metadata.
2. Resolve latest guide-system version.
3. Read changelog and relevant migrations.
4. Assess repository state.
5. Resolve migration decisions and classify changes.
6. Evaluate optional transition capabilities required/recommended by the migration chain.
7. Create the ready migration milestone/package.
8. Apply any planning-time overlay required to establish project truth.
9. Execute the ready milestone with the canonical execution prompt.
10. Run validation and milestone-owned review gates.
11. Run deferred documentation synchronization when applicable.
```

A bespoke execution prompt is not required. `templates/prompts/execute-milestone.md` is the canonical executor entry point for ready milestones. A planning interface may provide a short handoff note that identifies the primary milestone path or overlay application instructions.

## Change classification

| Class | Meaning |
|---|---|
| Required | Must be applied for the target profile. |
| Conditional | Apply only when a module/profile/maturity condition is met. |
| Deprecated | Remove or stop referencing. |
| Manual review | Requires human or documentation-agent judgment. |
| No-op | Intentionally not applicable. |

## Optional transition capabilities

A migration may introduce a reusable capability whose historical adoption is useful but not required for guide-system compliance.

Treat such work separately from required migration changes.

For example, guide-system 0.8 introduces a durable planning-research model. A repository crossing from a pre-research-model version may optionally bootstrap historical planning knowledge from surviving chats, notes, experiments, or other evidence.

The migration document that introduces the capability defines when it should be evaluated and how it relates to compliance.

Generic migration rules:

- do not make an optional historical reconstruction a hidden prerequisite for guide compliance;
- do not fabricate unavailable historical evidence;
- allow bounded adoption to occur inside the migration when cheap and useful;
- prefer a dedicated special workflow when adoption is substantial;
- allow optional bootstrap work to happen later if evidence becomes available after the guide migration;
- keep the resulting durable artifacts in the authority/knowledge layer defined by the capability rather than adding ad-hoc migration metadata.

The generic update prompt follows the migration chain. It must not hard-code one version's optional transition behavior as a permanent rule for every future guide update.
