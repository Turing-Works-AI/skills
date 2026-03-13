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

---

## How to install

Skills are installed via the Claude Code plugin system. Do this once — it persists across all sessions.

### Step 1 — Open the plugin manager

In Claude Code (VSCode extension), open the command palette and search for **Manage Plugins**, or click the plugin icon in the Claude Code sidebar.

### Step 2 — Add the marketplace

Go to the **Marketplaces** tab and enter:

```
Turing-Works-AI/skills
```

Click **Add**. Claude Code will pull the marketplace definition from this GitHub repo.

### Step 3 — Install the plugin

Go to the **Plugins** tab. You should now see **turing-works-skills** listed under the Turing Works marketplace. Click **Install**.

### Step 4 — Done

Skills activate automatically based on context in every future session. No slash command needed.

---

## Adding new skills

1. Create a new folder under `plugin/skills/your-skill-name/`
2. Add a `SKILL.md` file — this is the skill content Claude receives when triggered
3. The frontmatter at the top of `SKILL.md` must include `name` and `description` fields; the `description` controls when the skill auto-triggers
4. Commit and push — installed users will get the update on next sync
