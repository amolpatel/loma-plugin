# Agent Instructions — {{PROJECT_NAME}}

This project uses **Loma** (Living Organized Memory Architecture) to maintain persistent context across AI sessions.

---

## At Session Start

Before writing any code, read these files in order:

1. `loma/loma-map.md` — index of all documentation
2. `loma/summary.md` — project overview and current status
3. `loma/terminology.md` — domain vocabulary

Briefly demonstrate domain knowledge before attending to the user's request.

---

## During the Session

- **Chat-mode first** — explore and design before coding
- **Check loma-map** before searching the codebase
- **Implement only after a clear decision has been made**

---

## After Confirmed Changes

When the user confirms work ("looks good", "ship it", "this is final"):

1. Update the corresponding loma entries to reflect current state
2. Verify the loma structure still mirrors the codebase
3. Refactor loma organisation if needed

---

## Loma Authority

Inside `loma/`, you may create, update, rename, and reorganise files freely. If loma content contradicts the actual code, treat the code as source of truth and update the loma to match.

---

## Available Loma Skills

| Skill | Description |
|-------|-------------|
| `/loma:audit` or `$loma-audit` | Audit loma for correctness |
| `/loma:handover` or `$loma-handover` | Create a session continuity document |
| `/loma:update-map` or `$loma-update-map` | Regenerate loma-map.md |
| `/loma:maintain` or `$loma-maintain` | Run weekly maintenance checklist |

---

*Powered by [Loma Plugin](https://github.com/amolpatel/loma-plugin)*
