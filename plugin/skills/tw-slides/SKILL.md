---
name: tw-slides
description: Master skill for creating, editing, or reviewing Turing Works slide decks and client presentations. Combines Turing Works brand standards (colours, typography, layouts) with consulting-grade slide craft (MBB structure, action titles, vertical/horizontal flow, MECE reasoning). Use this skill whenever Alasdair asks to create a Turing Works presentation, client proposal, pitch deck, workshop deck, or any branded output. Also trigger when the user says "make it on-brand", "use our brand colours", "Turing Works style", "ghost deck", "action title", or references building slides for a client. This skill supersedes all generic design and slide defaults — always consult it before generating branded content.
---

# TW Slides — Turing Works Slide Craft & Brand Skill

This skill governs all Turing Works slide creation. It is split into focused files. Read the files relevant to the task — do not read everything upfront.

---

## Files

| File | When to read |
|------|--------------|
| `brand.md` | Any time you're placing or styling visual elements — colours, typography, layout patterns, grid, shapes, shared constants |
| `writing-rules.md` | Any time you're writing or editing slide copy — action titles, UK/AUS spelling, GMAT grammar, concision, tone, bullet punctuation |
| `deck-playbook.md` | When planning or finishing a deck — 5-section spine, Ghost Deck, horizontal flow, Pre-Flight checklist, Toothbrush Test |
| `content.md` | When deciding *what* to put on a slide — content patterns per deck section, each naming the slide type to render it on |
| `slide-types/*.md` | When building a specific slide — one file per slide type with exact visual placement, element inventory, and code template |
| `slide-types/brief-template.yaml` | Copy-paste briefing format for a single slide |

---

## Working pattern

For every slide task:

1. **Plan** — read `deck-playbook.md` to orient the slide within the deck.
2. **Decide content** — consult `content.md` for the pattern and the slide type it suggests.
3. **Write** — apply `writing-rules.md` to every line of copy.
4. **Render** — open `slide-types/{type}.md` for exact placement and the code template; apply `brand.md` for any shared constants.
5. **Finish** — run the Pre-Flight checklist and Toothbrush Test in `deck-playbook.md`.

---

## Integration with `client-wiki`

When building decks for a specific client, source material lives in the `client-wiki` repo at `clients/{name}/`. The `presentation-creator` agent in that repo is responsible for gathering the right inputs from the hub page, use cases, meetings, and research — this skill governs how those inputs are turned into on-brand slides.
