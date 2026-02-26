# Agent Instructions — loma-plugin

This is the **Loma Plugin** repository: a cross-platform AI skills package that gives AI coding assistants a structured, persistent memory system (the "loma") for long-running projects.

---

## Project Structure

```
loma-plugin/
├── .claude-plugin/plugin.json   # Claude Code plugin manifest
├── skills/                      # Skill definitions (SKILL.md per skill)
│   ├── init/                    # /loma:init  — initialize loma/ structure
│   ├── audit/                   # /loma:audit — verify correctness
│   ├── handover/                # /loma:handover — session continuity docs
│   ├── update-map/              # /loma:update-map — regenerate index
│   └── maintain/                # /loma:maintain — weekly checklist
├── templates/                   # Starter files copied on init
│   ├── AGENTS.md                # Root-level Codex bootstrap template
│   ├── agents.md                # loma/agents.md template
│   ├── summary.md
│   ├── terminology.md
│   ├── practices.md
│   ├── loma-map.md
│   └── plans/README.md
├── commands/loma.md             # Help text for /loma command
├── marketplace.json             # Plugin registry metadata
└── README.md
```

---

## Key Conventions

- **Skills** live in `skills/<name>/SKILL.md`. Each `SKILL.md` contains step-by-step instructions that the AI follows when the skill is invoked. Keep them procedural and unambiguous.
- **Templates** live in `templates/`. They use `{{PROJECT_NAME}}` and `{{DATE}}` as placeholders replaced at init time.
- The `AGENTS.md` in `templates/` is the file that gets placed at the **root of a user's project** when they run `/loma:init`. It bootstraps Codex (and other agents) to read the loma at session start.
- The plugin name is `loma`; all commands are prefixed `loma:` in Claude Code and `loma-` in Codex.

---

## When Modifying Skills

1. Each skill should be self-contained — assume the agent has no other context.
2. Use concrete, numbered steps. Avoid vague instructions like "handle errors gracefully"; instead spell out exactly what to do.
3. If a skill creates files, document the exact output format in the skill.
4. After updating a skill, verify it is consistent with the README command table.

---

## When Modifying Templates

- Preserve all `{{PLACEHOLDER}}` markers — the init skill replaces them at runtime.
- Templates describe **current state**, not history. Write them in present tense.
- Keep templates under 250 lines.

---

*Powered by [Loma Plugin](https://github.com/amolpatel/loma-plugin)*
