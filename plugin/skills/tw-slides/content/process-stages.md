# Content Guide: Process Stages Slide

What to write on a process stages slide. For visual placement, see `components/process-stages/spec.md`.

---

## When to use

Use this layout when presenting a phased approach — typically a sprint, engagement plan, or improvement programme — where each stage has distinct activities and a clear deliverable.

---

## Action title

A conclusion statement summarising the overall approach, not a topic label.

| Pattern | Example |
|---------|---------|
| `A [method] will [action] to [outcome]` | "A process improvement sprint will identify root causes and implement fixes to improve target P2P metrics" |
| `[N]-stage approach to [outcome]` | "Three-stage approach to reduce invoice exception rate below 15%" |

The action title should make the overall programme logic clear in one sentence.

## Subtitle

An optional supporting line beneath the title. Used to add timing context, conditions, or a bridging statement.

| Pattern | Example |
|---------|---------|
| `Based on [input], [implication]` | "Based on week 1 findings, several fixes can be initiated immediately" |
| `[Timeframe] engagement starting [date]` | "Two-week engagement starting 7 April 2026" |

Written in teal (`#518C94`), smaller than the title. Keep to one line.

---

## Stage names

Each chevron header follows the pattern `Stage N | {{verb}}`.

**Naming rules:**
- Use a single imperative verb or short verb phrase: Diagnose, Plan, Implement, Validate, Measure
- The verb should describe what happens in that stage, not what it produces
- Keep consistent tense across all stages (all imperative)
- Maximum 2 words per stage name

| Good | Bad |
|------|-----|
| Diagnose | Understanding the issues |
| Plan | Solution design phase |
| Implement | Making changes |

---

## Activity box content

### Title
A short noun phrase naming the type of work (2-4 words). Bold, sentence case.

| Good | Bad |
|------|-----|
| Problem-solving sessions | Stage 1 activities |
| Form hypotheses | Hypothesis formation and prioritisation |

### Bullets
Concrete actions, not vague descriptions. Each bullet should answer "what will we actually do?"

**Writing rules:**
- Start each bullet with a verb (analyse, map, configure, track, propose)
- Be specific: name the tools, teams, data sources, and artefacts involved
- 2-3 bullets per stage — if you need more, the stage is too broad
- Minimum font size: 11pt — if text overflows, cut words rather than shrinking text

| Good | Bad |
|------|-----|
| "Whiteboard workshops with AP team to develop hypothesis on poor metric performance" | "Conduct workshops" |
| "Configure tool and process changes (Zudello workflows, PO policy, approval workflows)" | "Make necessary system changes" |

---

## Output box content

The "Output" label is always present in teal bold. Below it, state the concrete deliverable — not a description of work, but the artefact or outcome that the stage produces.

**Writing rules:**
- Name a tangible thing: a document, a register, a dashboard, a configured system
- Keep to one line where possible
- No verbs — this is a noun phrase (the thing produced, not the action)

| Good | Bad |
|------|-----|
| Validated issue hypotheses | We will have validated the issues |
| Prioritised improvement roadmap | A roadmap will be created |
| Implemented tool and workflow fixes | Changes implemented and tracked |

---

## Content flow

The three stages should form a logical progression:

1. **Understand** — diagnose, discover, map, assess
2. **Design** — hypothesise, plan, prioritise, scope
3. **Execute** — implement, configure, track, measure

Each stage's output feeds into the next stage's input. The output of the final stage should connect back to the metric or outcome named in the action title.
