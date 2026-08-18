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
6. Create the ready migration milestone/package.
7. Apply any planning-time overlay required to establish project truth.
8. Execute the ready milestone with the canonical execution prompt.
9. Run validation and milestone-owned review gates.
10. Run deferred documentation synchronization when applicable.
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
