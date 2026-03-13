# Turing Works — Claude Code Skills

Custom skills plugin for Claude Code, used across Turing Works projects.

## Structure

```
skills/
├── .claude-plugin/
│   └── plugin.json       # Plugin metadata
└── skills/
    └── tw-slides/
        └── SKILL.md      # Turing Works slide craft & brand standards
```

## Skills

| Skill | Trigger |
|-------|---------|
| `tw-slides` | Creating, editing, or reviewing Turing Works slide decks and client presentations. Covers brand standards (colours, typography, layouts) and MBB-standard slide craft. |

## Installation

Install as a Claude Code plugin from this repo:

```
/install-plugin github:Turing-Works-AI/skills
```

Once installed, skills activate automatically based on context — no slash command needed.
