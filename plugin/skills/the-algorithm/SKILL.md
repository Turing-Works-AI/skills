---
name: the-algorithm
description: Interactive decision framework based on Elon Musk's five-step method. Walks you through discrete AskUserQuestion prompts — one at a time — to find the real bottleneck, decide whether to act, what to delete instead, and the simplest reliable approach. Use BEFORE acting on any non-trivial decision — feature request, refactor, migration, new tool/vendor/hire, process change, meeting, policy, roadmap item. Skip for single-line typos or when the user has given explicit "just do it" instructions. Prevents over-engineering and scope creep by gating action behind deliberate questioning. Five steps — 1) Question need 2) Delete unnecessary 3) Simplify 4) Accelerate 5) Automate — most decisions end at Step 3.
---

# Bottleneck Remover Algorithm

A gated decision framework adapted from Elon Musk's five-step production method. Instead of synthesizing an answer immediately, walk the user through **one discrete question at a time** using the `AskUserQuestion` tool. Each answer determines whether to proceed to the next step or cut to the conclusion.

Default bias: **most decisions end at Step 3.** Steps 4–5 are rare.

The five steps that remove the bottleneck:
1. **Question** the requirement — is it actually broken?
2. **Delete** anything unnecessary — can the problem disappear instead?
3. **Simplify** what remains — find the minimum reliable solution
4. **Accelerate** cycle time — only after Steps 1–3
5. **Automate** — only after the manual version is validated

## When to invoke

| Trigger | Run it? |
|---|---|
| Feature / product request, refactor proposal, "should we migrate" | **Yes** |
| Bug fix >10 lines, process or workflow change | **Yes** |
| New tool, vendor, hire, meeting, policy, roadmap item | **Yes** |
| Multiple feedback points arriving together | **Yes — batch mode** |
| Single-line typo, obvious fix, user said "just do it" | **Skip** |

## Operating rules

- **One question per turn.** Never list all questions up front. Fire one `AskUserQuestion`, read the answer, decide whether to ask the next one or jump to the conclusion.
- **Branch aggressively.** If Step 1 returns "don't do", don't ask Step 2 or 3.
- **Free-text when needed.** Some questions (e.g., "what could you delete?") don't have preset options. Ask in plain text — don't force multiple-choice when the answer space is open.
- **Never answer for the user.** If you find yourself guessing their answer, stop and ask.
- **Restate answers back.** After each question, echo the answer in one line so the user can correct a misread before the next question.

---

## Step 1 — Question the requirement

Run these in sequence. Stop as soon as a "don't do" verdict triggers.

### Q1.1 — Is this actually broken right now?

Use `AskUserQuestion`:
- **A.** Yes — there's a concrete failure I can point to
- **B.** Maybe — it *feels* wrong but nothing's failing
- **C.** No — it's hypothetical / for the future

Branch:
- **A** → ask Q1.2
- **B** → **Verdict: Don't do.** "Feelings aren't failures. Revisit when there's a concrete incident." Skip to Conclusion.
- **C** → **Verdict: Record for later.** Write a one-line note to a backlog file (`~/.notes/backlog.md` or the project's issues). Skip to Conclusion.

### Q1.2 — How often does this happen?

`AskUserQuestion`:
- **A.** Common — daily, or every user hits it
- **B.** Occasional — weekly, or a subset of users
- **C.** Rare — a few times total, or one user
- **D.** One-time incident

Branch:
- **A / B** → ask Q1.3
- **C / D** → **Verdict: Record for later.** "Rare problems don't justify permanent code/process. Log it; revisit if it recurs."

### Q1.3 — Who benefits if you ship this?

`AskUserQuestion`:
- **A.** Many users or the whole team
- **B.** A specific named user or small group
- **C.** Just me
- **D.** No one specific — it's a gut refactor

Branch:
- **A / B** → proceed to Step 2
- **C** → flag it: "Solo benefit is fine for personal projects. For shared code, require an external ask." Proceed to Step 2 only if user confirms.
- **D** → **Verdict: Don't do.** "Gut refactors without a beneficiary are scope creep." Skip to Conclusion.

---

## Step 2 — Delete

Before adding anything, look for something to remove.

### Q2.1 — What existing thing, if removed, would make this problem disappear?

Ask as free-text (no options — this is open-ended).

Examples of framings to offer if the user is stuck:
- A fallback, a legacy code path, an auto-detection routine
- A config option nobody uses, a feature flag that's permanently on/off
- A process step, a meeting, an approval gate
- A vendor or tool that's only used for one corner case

### Q2.2 — If you delete that thing, does the original problem still need solving?

`AskUserQuestion`:
- **A.** No — deleting solves it entirely
- **B.** Partially — it shrinks the problem but doesn't remove it
- **C.** Yes — the problem remains even without that thing
- **D.** I can't think of anything to delete

Branch:
- **A** → **Verdict: Delete, don't add.** Propose the deletion. Skip Step 3.
- **B / C / D** → proceed to Step 3

---

## Step 3 — Simplify

Find the minimum reliable solution for what survived.

### Q3.1 — What's the simplest version that works?

`AskUserQuestion`:
- **A.** One config line / env var / flag flip
- **B.** A small function (<30 lines) in an existing file
- **C.** A new file or module in an existing service
- **D.** A new service, platform, or major refactor
- **E.** Not sure yet

Branch:
- **A** → good. Propose it in Conclusion.
- **B** → good, proceed to Conclusion.
- **C** → ask Q3.2 before accepting
- **D** → ask Q3.2 and Q3.3 — strong pressure to reduce scope
- **E** → ask the user to spend 5 minutes sketching, then retry

### Q3.2 — Would you accept one tradeoff to shrink this to A or B?

Free-text. Offer common tradeoffs as prompts:
- "Pick one case instead of handling both"
- "Require the user to edit a config line instead of auto-detecting"
- "Ship it as manual-run and only automate if it proves valuable"
- "Write an error message instead of a fallback"

If the user accepts a tradeoff, update the chosen approach before Conclusion.

### Q3.3 — (scope-reduction only) What are you *not* going to do?

Free-text. Force the user to name at least one thing being cut. If they can't, the scope is still too big — loop back.

---

## Steps 4–5 (rare; only when clearly warranted)

### Step 4 — Accelerate

Only if the surviving plan is on a hot critical path (user-visible latency, paid per-invocation cost, or blocking another system). `AskUserQuestion`:
- **A.** Yes, it's critical-path — optimise now
- **B.** No, ship the simple version first

If B: skip.

### Step 5 — Automate

Only if the user has run the manual version ≥3 times without surprise.
- **A.** Yes, I've done it manually and it's stable
- **B.** No, this would be my first run

If B: **do not automate.** Run it manually first. Automation of an un-validated process multiplies the bugs.

---

## Conclusion format

Always end with exactly this block:

```markdown
### Decision
[Do | Don't do | Delete instead | Record for later]

### Why (one sentence)
...

### Next action (concrete, one or two bullets)
- ...
```

---

## Feedback batch mode

Trigger when the user pastes ≥3 feedback points at once.

1. **Number the points.** Echo them back as a numbered list so the user can correct misreads.
2. **For each point, run Q1.1 + Q1.2 only** (one `AskUserQuestion` per point, or batched into one question if they're short and similar — user's call).
3. **Build a verdict table:**

   ```
   | # | Point | Verdict | Why |
   |---|-------|---------|-----|
   | 1 | ...   | Do      | ... |
   | 2 | ...   | Don't   | ... |
   ```

4. Only points with verdict **Do** continue to Steps 2–3 (sequentially, still one question at a time).
5. Typical result: 5 points → 1–2 actionable.

---

## Anti-patterns to flag during questioning

If the user's free-text answers include any of these, surface them:

| Pattern in their answer | Flag |
|---|---|
| "Just in case…" / "for future flexibility" | "No one has asked for this yet — Step 1 verdict should be *Record*, not *Do*." |
| "We need to auto-detect…" | "One config line almost always beats detection. Revisit Step 3." |
| "Add a review/approval step…" | "Reacting to one incident with permanent process. Ask Q1.2 again." |
| "Hire a new role to handle X…" | "Ask Step 3 first — can the work be simplified so it doesn't need a role?" |
| "Switch from Tool A to Tool B…" | "Fix Tool A's config before migrating. Migration cost is almost always underestimated." |

---

## Example session (abbreviated)

> User: *"Should we add a caching layer to the API?"*
>
> Skill → Q1.1: `Is this actually broken right now?` → **A. Yes**
> Skill → Q1.2: `How often?` → **A. Common**
> Skill → Q1.3: `Who benefits?` → **A. Many users**
> Skill → Q2.1: `What could you delete to make this disappear?` → *"We're fetching the same data on every render."*
> Skill → Q2.2: `If you fix that, does the original problem still need solving?` → **A. No**
>
> **Conclusion:** Delete the redundant fetches. Don't add caching.

---

## Pre-Action Checklist (the skill has done its job if all are true)

- [ ] Step 1 ran — the user confirmed failure, frequency, and beneficiary
- [ ] Step 2 ran — a deletion candidate was genuinely considered
- [ ] Step 3 picked the smallest option the user would accept
- [ ] Final Conclusion block is present with Decision, Why, Next action
- [ ] No question was batched, no answer was guessed
