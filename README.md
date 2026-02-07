# Loma Plugin

**Living Organized Memory Architecture** - An AI-persistent project knowledge system for Claude Code.

Loma helps AI coding assistants maintain context and alignment across sessions spanning weeks or months. It's a rebranded and enhanced version of the [Lode Coding](https://github.com/fjzeit/lode) methodology.

---

## Installation

### From GitHub (recommended)

```bash
claude plugin install github:amolpatel/loma-plugin
```

### Local Development

```bash
git clone https://github.com/amolpatel/loma-plugin.git
claude --plugin-dir ./loma-plugin
```

---

## Quick Start

### Initialize a New Project

```
/loma:init
```

This creates the `loma/` folder structure with starter templates.

### Available Commands

| Command | Description |
|---------|-------------|
| `/loma` | Show all available Loma commands |
| `/loma:init` | Initialize `loma/` structure in a new project |
| `/loma:audit` | Audit existing `loma/` for correctness |
| `/loma:handover` | Create session handover document |
| `/loma:update-map` | Regenerate `loma-map.md` index |
| `/loma:maintain` | Run weekly maintenance checklist |

---

## What is Loma?

Loma is a documentation methodology designed for AI-assisted development. It creates a structured knowledge base that:

1. **Persists across sessions** - AI assistants read the loma at session start
2. **Stays current** - Updated after every significant change
3. **Documents the "why"** - Captures rationale, not just facts
4. **Mirrors code structure** - Domain folders match source code organization

### Core Files

Every Loma-enabled project has these files:

```
loma/
├── loma-map.md        # Index of all documentation
├── summary.md         # Project overview
├── terminology.md     # Domain vocabulary
├── practices.md       # Development conventions
├── agents.md          # AI interaction guidelines
├── plans/             # Roadmaps and TODOs
└── tmp/               # Git-ignored session scraps
```

### Domain Folders

As your project grows, add domain-specific folders:

```
loma/
├── api/
│   └── summary.md     # API integration docs
├── data/
│   └── summary.md     # Data layer docs
└── auth/
    └── summary.md     # Authentication docs
```

---

## Core Philosophy

**Division of Responsibility:**
- **Human**: Owns the code, makes final decisions
- **AI**: Memory keeper and high-speed executor

**Golden Rule:** Anything worth implementing is worth permanently recording in the Loma.

---

## AI Agent Workflow

### At Session Start

1. Read `loma/loma-map.md` - the documentation index
2. Read `loma/terminology.md` and `loma/summary.md`
3. Demonstrate domain knowledge before coding

### During Session

1. **Chat-mode first** - explore and design before coding
2. **Check loma-map** before searching the codebase
3. **Implement only after clear decision**

### After Changes

When work is confirmed ("looks good", "ship it"):

1. Update the corresponding loma entries
2. Verify loma structure mirrors codebase
3. Refactor loma organization if needed

---

## File Quality Standards

Every loma file should:

1. Cover **exactly one topic**
2. Contain **concrete examples** (code snippets, Mermaid diagrams)
3. **Link to related files** using relative paths
4. Document **invariants and rationale**
5. Stay **under 250 lines**

---

## Session Handovers

Use `/loma:handover` to create continuity documents with:

- Current task state
- Decisions made
- Approaches tried (successes and failures)
- Blockers encountered
- Clear next steps

Handover files are saved to `loma/tmp/` (git-ignored).

---

## Weekly Maintenance

Run `/loma:maintain` to check:

- Documentation currency vs code changes
- Stale TODO/FIXME markers
- Orphaned files not in the index
- Missing documentation for new modules

---

## Contributing

Contributions welcome! Please:

1. Fork the repository
2. Create a feature branch
3. Submit a pull request

---

## License

MIT License - see [LICENSE](LICENSE) for details.

---

## Credits

Based on the [Lode Coding](https://github.com/fjzeit/lode) methodology by [@fjzeit](https://github.com/fjzeit).
