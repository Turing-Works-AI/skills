# Turing Works — Claude Code Skills

Custom skills plugin for Claude Code, used across Turing Works projects.

## Structure

```
skills/
├── .claude-plugin/
│   └── marketplace.json      # Marketplace definition (points to plugin/)
└── plugin/
    ├── .claude-plugin/
    │   └── plugin.json       # Plugin metadata
    └── skills/
        └── tw-slides/
            └── SKILL.md      # Turing Works slide craft & brand standards
```

## Skills

| Skill | Triggers when… |
|-------|----------------|
| `tw-slides` | Creating, editing, or reviewing Turing Works slide decks, proposals, pitch decks, or any branded output. Also triggers on "make it on-brand", "Turing Works style", "ghost deck", "action title". |
| `polish-linkedin-post` | Refining a LinkedIn post or professional content — strengthens hooks, checks credibility, flags LLM-isms, improves flow. |
| `loom-to-notion` | Converting a Loom video transcript into a structured "How To" Notion page. |

---

## How to install (local)

Installing locally is the recommended approach. It points Claude Code directly at your cloned copy of this repo, so you control when updates apply.

### Step 1 — Clone the repo

```bash
git clone https://github.com/Turing-Works-AI/skills.git ~/path/to/skills
```

Skip this if you already have it cloned.

### Step 2 — Add the plugin

Run this in your terminal, pointing to the `plugin/` subdirectory:

```bash
claude plugin add ~/path/to/skills/plugin
```

Replace `~/path/to/skills` with your actual local path.

### Step 3 — Done

Skills activate automatically based on context in every future session. No slash command needed.

---

> **Note on new skills:** Claude Code scans the plugin directory at install time. If a new skill is added to the repo after you installed, you need to reinstall the plugin to pick it up:
> ```bash
> claude plugin remove turing-works-skills
> claude plugin add ~/path/to/skills/plugin
> ```

---

## Adding new skills

1. Create a new folder under `plugin/skills/your-skill-name/`
2. Add a `SKILL.md` file — this is the skill content Claude receives when triggered
3. The frontmatter at the top of `SKILL.md` must include `name` and `description` fields; the `description` controls when the skill auto-triggers
4. Anyone who has the plugin installed will need to reinstall it to pick up the new skill (see note above)
