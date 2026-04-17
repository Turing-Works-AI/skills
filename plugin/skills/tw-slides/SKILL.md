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

## Relationship to `anthropic-skills:pptx`

`anthropic-skills:pptx` owns the **mechanics of the `.pptx` file**: pptxgenjs scaffolding, reading existing decks (`markitdown`), editing via unpack/pack, conversion to JPGs, and the visual-QA subagent loop.

This skill owns the **content and design**: brand standards, writing rules, deck spine, content patterns, and the Turing Works slide-type layouts.

Division of labour:

- **Always render through `slide-types/*.md`.** Those layouts, plus the matching `*-example.pptx` and `*-example.pdf` reference files, are the source of truth for what a Turing Works slide looks like. Never substitute the generic palettes, fonts, or layouts in `anthropic-skills:pptx` — those are explicitly overridden by `brand.md` and the slide-type templates here.
- **Default build path = template duplication.** When the slide type has a `*-example.pptx`, use the `anthropic-skills:pptx` editing workflow (`editing.md`) to unpack it, duplicate the relevant slide, swap the text, clean and repack. This preserves brand fidelity and avoids code drift.
- **Fallback = code generation.** If the slide type has no example file, or the requested variant is structurally outside what the example covers (e.g. 5 cards when the example has 3), fall back to the `pptxgenjs` code template at the bottom of the slide-type file.
- **Visual QA is mandatory.** After build, always run the `anthropic-skills:pptx` visual-QA loop: render slides to JPGs (`soffice` + `pdftoppm`), have a subagent inspect them, fix issues, re-verify.

---

## Working pattern

For every slide task:

1. **Plan** — read `deck-playbook.md` to orient the slide within the deck.
2. **Decide content** — consult `content.md` for the pattern and the slide type it suggests.
3. **Write** — apply `writing-rules.md` to every line of copy.
4. **Render** — open `slide-types/{type}.md`. If a `*-example.pptx` exists, duplicate the matching slide via the `anthropic-skills:pptx` editing flow (unpack → `add_slide.py` → swap text → `clean.py` → `pack.py`). Otherwise use the `pptxgenjs` code template in the slide-type file. Apply `brand.md` for any shared constants either way.
5. **Finish** — run the Pre-Flight checklist and Toothbrush Test in `deck-playbook.md`, then run the visual-QA loop from `anthropic-skills:pptx` (render to JPGs, subagent review, fix and re-verify). Do not declare done until at least one fix-and-verify cycle has passed cleanly.

---

## Layout improvement and tidying

When asked to "improve the layout", "tidy the slide", "align boxes", or make other cosmetic improvements to an existing PPTX:

1. **Unpack the slide** using `anthropic-skills:pptx` (`unpack.py`).
2. **Read the slide XML** and map every shape's position (`<a:off x="" y=""/>`) and size (`<a:ext cx="" cy=""/>`).
3. **Identify alignment issues** — compare shapes that should be in the same row or column. Look for:
   - Boxes that should share the same `y` value but don't (horizontal misalignment)
   - Boxes that should share the same `x` value but don't (vertical misalignment)
   - Inconsistent gaps between elements (one gap is 47 EMU, the next is 120 EMU)
   - Row labels not vertically centred against their content cells
   - Uneven row heights or column widths for elements that should match
4. **Fix positions directly in the XML** — adjust `<a:off>` and `<a:ext>` values to align elements. Use the first element in a row/column as the reference and snap others to match.
5. **Apply `brand.md` spacing rules** — minimum 0.5" margins from slide edges, 0.3-0.5" between content blocks, consistent gaps throughout.
6. **Clean, pack, and visually verify** using the `anthropic-skills:pptx` workflow (`clean.py` → `pack.py` → render → subagent QA).

Layout improvements are only made when explicitly requested — e.g. "tidy the layout", "align boxes", "improve the design". Do not make layout changes as part of a content-only edit unless asked.

---

## Integration with `client-wiki`

When building decks for a specific client, source material lives in the `client-wiki` repo at `clients/{name}/`. The `presentation-creator` agent in that repo is responsible for gathering the right inputs from the hub page, use cases, meetings, and research — this skill governs how those inputs are turned into on-brand slides.
