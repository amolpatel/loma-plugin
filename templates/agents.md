# AI Agent Guidelines

> How AI agents should interact with this project using Loma methodology.

---

## Core Philosophy

The Loma (`loma/`) is the AI's persistent memory for this project. It's the only way to maintain alignment across sessions spanning weeks or months.

**Division of Responsibility:**
- **Human**: Owns the code, makes final decisions
- **AI**: Memory keeper and high-speed executor

**Golden Rule:** Anything worth implementing is worth permanently recording in the Loma.

---

## Authority Inside `loma/`

AI agents have full autonomy within the loma directory:

| Action | Permission |
|--------|------------|
| Create files | ✅ Freely |
| Update files | ✅ Freely |
| Rename/move files | ✅ Freely |
| Delete files | ✅ Only if committed and unchanged |
| Create new directories | ✅ When project evolves |

**Constraints:**
- All diagrams must use **Mermaid** only
- If loma content contradicts actual code, prioritize code as source of truth and propose loma fixes

---

## Mandatory Structure

```
loma/
├── loma-map.md              # Hierarchical index of all loma files
├── summary.md               # One-paragraph living snapshot
├── terminology.md           # Term → meaning definitions
├── practices.md             # Patterns and practices
├── agents.md                # This file - AI interaction guidelines
├── plans/                   # Roadmaps & TODOs
├── tmp/                     # Git-ignored session scraps
└── [domain]/                # e.g. api/, data/, core/
    ├── summary.md
    └── *.md                 # One topic per file (kebab-case)
```

---

## File Quality Standards

Every loma file must:

1. **Cover exactly one topic** - decompose if scope creeps
2. **Contain concrete examples** - code snippets and Mermaid diagrams
3. **Link to related lomas** - use relative paths
4. **Document invariants & rationale** - capture the "why"
5. **Stay under 250 lines** - split into sub-files if larger

---

## Session Workflow

### At Session Start

1. Read `loma/loma-map.md` first - it's your index
2. Read `loma/terminology.md` and `loma/summary.md`
3. Briefly demonstrate domain knowledge before attending to requests

### During Session

1. **Chat-mode first** - explore and design before coding
2. **Check the loma-map** before searching the codebase
3. **Implement only after clear decision**

### After Changes

When the user confirms work ("looks good", "ship it", "this is final"):

1. **Immediately update** the corresponding loma entries
2. Check if loma structure still mirrors codebase
3. Refactor loma organization if needed

---

## Writing Style

The loma describes **current system state**, not a history of changes.

### Bad (Changelog Style)

```markdown
Added retry logic to api-client.ts on 2024-01-15. Previously requests
would fail immediately. Now they retry 3 times with exponential backoff.
```

### Good (Current State)

```markdown
The API client retries failed requests up to 3 times with exponential
backoff (100ms, 200ms, 400ms). Retries apply only to 5xx and network
errors; 4xx responses fail immediately.
```

---

## Temporary vs Permanent Content

| Content Type | Location | Example |
|-------------|----------|---------|
| Session scraps | `loma/tmp/` | Debugging notes, one-off experiments |
| Permanent learnings | Main loma files | Architecture decisions, API contracts |
| Handover documents | `loma/tmp/` | Session state for continuity |

**Rule of thumb:**
- Need it in future sessions? → Main loma
- Solving today's problem only? → Chat or `tmp/`

---

## Session Handovers

When requested, create a handover document in `loma/tmp/` containing:

- Current task state
- Decisions made this session
- Approaches tried (and failures)
- Blockers encountered
- Clear next steps

Goal: Let a fresh session continue seamlessly.

---

## Natural Nudges

Use these conversationally when appropriate:

- *"Let's capture this design in loma/... before implementing."*
- *"Per Loma guidelines, chat-mode first, then agent-mode."*
- *"Now that this is settled, I'll update the loma so we never forget."*

---

## Success Metrics

Agent performance is measured by:

1. **Code quality** - correct, maintainable implementations
2. **Loma accuracy** - must reflect current system state after each session
3. **Knowledge continuity** - future sessions should start with full context

---

## Related Files

- [Loma Map](loma-map.md) - Index of all documentation
- [Summary](summary.md) - Project overview
- [Terminology](terminology.md) - Domain language definitions

---

*Powered by the [Loma Plugin](https://github.com/amolpatel/loma-plugin)*
