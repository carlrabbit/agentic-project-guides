# Migration Model

## Status

Authoritative for guide and repository migrations.

## Purpose

Guide updates are applied through profile-aware migrations, not vague upgrade instructions.

Do not ask agents to simply "upgrade to the latest guide".

## Migration flow

```text
1. Identify current guide profile metadata.
2. Identify target guide profile metadata.
3. Assess repository state.
4. Create a migration plan.
5. Classify changes.
6. Apply migration steps as focused milestones.
7. Run validation.
8. Run documentation sync.
```

## Change classification

| Class | Meaning |
|---|---|
| Required | Must be applied for the target profile. |
| Conditional | Apply only when a module/profile/maturity condition is met. |
| Deprecated | Remove or stop referencing. |
| Manual review | Requires human or documentation-agent judgment. |
| No-op | Intentionally not applicable. |

## Migration document structure

A migration document should include:

```text
Source profile/version
Target profile/version
Affected repository roles
Affected maturity stages
Required changes
Conditional changes
Deprecated concepts
Manual review points
Validation expectations
Documentation sync expectations
Rollback notes
```
