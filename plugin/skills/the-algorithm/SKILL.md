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

## Step 1 — Question the requirement (first principles)

Musk's framing: *requirements are always wrong, no matter how smart the source.* Your job before accepting the request is to force the user to reason from first principles — name the goal, name the gap, name the primitives on the critical path — and only *then* decide whether this request moves an actual primitive.

**Primitives** are the atomic, irreducible building blocks of the system at the relevant abstraction layer — things that cannot be decomposed further without changing what the system is. Examples: the data structure a feature needs, the network hop it depends on, the human step that can't be skipped. Everything else is composition and can be re-derived.

Run these in sequence. Stop as soon as a "don't do" or "record" verdict triggers.

### Q1.1 — What is the goal?

Free-text. Force a single clear sentence. If the user says "to fix X", push back: "*Fixing X* is a task, not a goal. What does fixing X enable?" Goals describe an end-state, not a task list.

### Q1.2 — What is the current state, and what's the gap to the goal?

Free-text. Two sentences: where things are now, and the specific gap between now and the goal. Not "it's broken" — *what exactly is missing or misaligned?*

### Q1.3 — What primitives sit on the critical path from current state → goal?

Free-text; ask for a short list (3–7 items). Prompt the user with: *"What are the irreducible building blocks that have to work for the goal to be reached? Strip away everything derivative."* Offer examples if they stall — a data model, a network call, a consent step, a UI primitive like a button. These are the things you will NOT delete in Step 2.

### Q1.4 — Does the request in front of us move one of those critical-path primitives?

`AskUserQuestion`:
- **A.** Now — it unblocks a primitive that is currently blocking progress
- **B.** Later — it's downstream of an on-path primitive but not blocking yet
- **C.** Off-path — it's adjacent / nice-to-have / not tied to any primitive in Q1.3
- **D.** Not sure

Branch:
- **A** → ask Q1.5
- **B** → **Verdict: Record for later.** "It's on-path but not blocking. Log in the backlog; revisit when an earlier primitive is unblocked."
- **C** → **Verdict: Don't do.** "Off-path work is the definition of scope creep — if it doesn't map to a primitive you named, deleting the request costs nothing." Skip to Conclusion.
- **D** → tell the user the skill cannot proceed until the primitive list in Q1.3 is sharp enough to map this request against. Loop back to Q1.3.

### Q1.5 — How often does this blocker actually hit?

`AskUserQuestion`:
- **A.** Common — daily or every user hits it
- **B.** Occasional — weekly or a subset of users
- **C.** Rare — a few times total, or one user
- **D.** One-time incident

Branch:
- **A / B** → proceed to Step 2
- **C / D** → **Verdict: Record for later.** "Rare problems don't justify permanent code/process, even when they are on-path. Log and revisit if it recurs."

---

## Step 2 — Delete

Before adding anything, look for something to remove. Musk's rule of thumb: *if you never have to add ~10% of what you delete back later, you weren't aggressive enough.* But there is a floor — **never delete a primitive you named in Q1.3.** Those are load-bearing. Delete the bloat that sits on top of them.

### Q2.1 — What existing thing, if removed, would make this problem disappear?

Ask as free-text (no options — this is open-ended). Push for aggressive candidates.

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
- **A / B** → ask Q2.3 (guard against deleting a primitive)
- **C** → proceed to Step 3 (delete didn't help; the request stays)
- **D** → push back once: "Are you sure nothing upstream could be removed? Re-read your Q1.3 list — anything composed *on top of* those primitives is a candidate." Ask Q2.1 again. If still D → proceed to Step 3.

### Q2.3 — Does the candidate break any primitive from Q1.3?

`AskUserQuestion`:
- **A.** No — the candidate is pure overhead sitting on top of the primitives
- **B.** Partially — it supports a primitive but isn't the primitive itself
- **C.** Yes — deleting it removes something you listed in Q1.3

Branch:
- **A** → **Verdict: Delete, don't add.** Safe aggressive delete. Skip Step 3.
- **B** → **Verdict: Delete with a restoration note.** Propose the deletion AND flag explicitly: "This may need a ~10% re-add later if the primitive it supports starts misbehaving. That's expected — Musk's 10% rule." Skip Step 3.
- **C** → **Stop.** You're about to delete the thing, not the bloat. Loop back to Q2.1 and find a different candidate. Never delete a primitive.

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

## Steps 4–5 — hard-gated on order

**Ordering is enforced, not advisory.** Steps 4 and 5 run ONLY if this conversation has user-confirmed answers for Steps 1, 2, AND 3. Musk's most-cited anti-pattern is reversing this order — automating or accelerating an un-simplified process compounds bugs and cost at scale. If the user invokes the skill asking to "optimise" or "automate" without running Steps 1–3 first, refuse and loop back to Step 1. Do not accept *"I already did those steps mentally"* — if the answers aren't in the conversation, they didn't happen for this decision.

Before running Step 4 or Step 5, verify internally: *"Do I have this user's answers to Q1.1–Q1.5, Q2.1–Q2.3 (or justified skip), and Q3.1 (plus Q3.2/Q3.3 if required) in this conversation?"* If no → loop back.

### Step 4 — Accelerate

Only if Steps 1–3 are complete AND the surviving plan is on a hot critical path (user-visible latency, paid per-invocation cost, or blocking another system). `AskUserQuestion`:
- **A.** Yes, it's critical-path — optimise now
- **B.** No, ship the simple version first

If B: skip.

### Step 5 — Automate

Only if Steps 1–3 are complete AND the user has run the manual version ≥3 times without surprise.
- **A.** Yes, I've done it manually ≥3 times and it's stable
- **B.** No, this would be my first or second run

If B: **do not automate.** Run it manually a few more times first. Automation of an un-validated process multiplies the bugs.

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
