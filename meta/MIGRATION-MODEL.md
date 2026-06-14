# Migration Model

Guide updates are applied through profile-aware migrations, not vague implementation instructions.

Do not ask implementation agents to simply "upgrade to the latest guide".

Allowed planning prompt:

```text
Plan migration to the latest available guide-system version.
```

The planning agent must resolve the latest version explicitly from the guide repository, inspect changelog and migration documents, and create a repository-specific migration package.

## Migration flow

```text
1. Identify current guide profile metadata.
2. Resolve latest guide-system version.
3. Read changelog and relevant migrations.
4. Assess repository state.
5. Create a migration plan.
6. Classify changes.
7. Create implementation-ready migration package.
8. Generate execution prompt.
9. Run implementation.
10. Run documentation sync.
```

## Change classification

| Class | Meaning |
|---|---|
| Required | Must be applied for the target profile. |
| Conditional | Apply only when a module/profile/maturity condition is met. |
| Deprecated | Remove or stop referencing. |
| Manual review | Requires human or documentation-agent judgment. |
| No-op | Intentionally not applicable. |
