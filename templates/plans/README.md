# Implementation Plans

> Roadmaps, handover documents, and session continuity notes.

---

## Structure

- **Handover documents**: `handover-YYYY-MM-DD.md` - Session state for continuity (in `tmp/`)
- **Milestone plans**: `milestone-*.md` - Detailed implementation plans
- **Rollout plans**: `rollout-*.md` - Production deployment strategies

---

## Handover Protocol

When ending a session, create a handover document containing:

1. **Current task state** - What was being worked on
2. **Decisions made** - Architecture choices, API discoveries
3. **Approaches tried** - What worked, what didn't
4. **Blockers encountered** - Issues preventing progress
5. **Next steps** - 3 concrete actions for next session
6. **How to reproduce** - Test commands, environment setup

Use `/loma:handover` to generate a handover document automatically.

---

## Plan Template

```markdown
# Plan: [Feature Name]

> Brief description of what this plan covers.

## Goals

- [ ] Goal 1
- [ ] Goal 2

## Non-Goals

- Not doing X
- Not doing Y

## Approach

[Describe the approach]

## Tasks

- [ ] Task 1
- [ ] Task 2
- [ ] Task 3

## Risks

- Risk 1: [Mitigation]

## Timeline

- Phase 1: [Description]
- Phase 2: [Description]
```

---

## Related Files

- [Loma Map](../loma-map.md) - Documentation index
- [Practices](../practices.md) - Development conventions
