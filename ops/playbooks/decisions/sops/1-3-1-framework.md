# 1-3-1 Decision Framework

**Objective:** Structure any non-trivial decision so the decision-maker gets one clear problem, three real options with tradeoffs, and one recommendation — in under 15 minutes.

**Prerequisites:** A decision that's worth more than 5 minutes of thought (if it's not, just decide)

**Owner:** [AGENT_SLUG]

---

## Procedure

### 1. Name the problem in one sentence

Not the background. Not the context. The actual fork in the road.

Bad: "We've been thinking about how to handle the expert knowledge base and there are a lot of transcripts and we could do vector search or grep or..."
Good: "How should we make 272 expert transcripts queryable?"

If you can't get it to one sentence, you're combining multiple decisions. Split them.

### 2. Generate three real options

Each option must be genuinely viable — something a reasonable person could choose. The test: if you can't make a case for each option with a straight face, it's not a real option.

**What "real" means:**
- Each has different tradeoffs, not just different levels of effort
- None is a strawman designed to make another look good
- "Do nothing" counts as a real option only if inaction has a genuine case (not as filler)

**For each option, write:**
- What it is (one sentence)
- Pros
- Cons
- Cost/effort

**Anti-pattern:** "Option A: the good one. Option B: obviously bad. Option C: absurdly bad." That's theater. If you catch yourself doing this, you haven't explored the problem space enough.

### 3. Pick one and say why

The person structuring the decision (not the decision-maker) makes a recommendation. One paragraph max. The recommendation should reference the tradeoffs — not just "I like A" but "A because [specific tradeoff] matters more than [other tradeoff] here."

This is the part people skip. Don't. The recommendation forces the structurer to have skin in the game.

**The hidden purpose of 1-3-1:** The goal isn't just a faster decision — it's training the person structuring it to think through problems completely. [SOURCE_TEACHER_SLUG] says "98% of the time I go, 'Sounds good. Do that.'" The framework works because by the time you've written three real options and a recommendation, you've often already found the obvious answer. If that happens — good. Decide and move. You don't need to present a 1-3-1 nobody needs to see. The thinking was the point.

### 4. Route it

Check the Autonomy Ladder in the Decision Making playbook (`ops/playbooks/decisions/decision-making.md`):
- **Within your autonomy?** Decide, log it, inform the other person after.
- **Above your autonomy?** Present the 1-3-1 to the decision-maker. They pick, you log.

### 5. Log the outcome

Every decision gets logged in the decision ledger with the date, what was decided, and why (one line). Strategic decisions also keep their full 1-3-1 file.

---

## Templates

### Full 1-3-1 file (for strategic decisions)

```markdown
# 1-3-1: [Decision Title]

**Date:** YYYY-MM-DD
**Owner:** [who's deciding]
**Status:** [Open / Decided / Archived]

## Problem
[One sentence]

## Options

### Option A: [Name]
- Pros:
- Cons:
- Cost/effort:

### Option B: [Name]
- Pros:
- Cons:
- Cost/effort:

### Option C: [Name]
- Pros:
- Cons:
- Cost/effort:

## Recommendation
[Which option and why — one paragraph max]

## Decision
[Filled in after decision-maker decides]
```

### Quick 1-3-1 (for tactical decisions — verbal, chat, or ledger entry)

```
Problem: [one sentence]
A: [option] — [key tradeoff]
B: [option] — [key tradeoff]
C: [option] — [key tradeoff]
Rec: [which and why]
```

This format works in Slack, Telegram, or spoken aloud. The full file isn't always necessary — the framework is.

---

## Quality Check

- [ ] Problem is one sentence — not background, not multiple decisions bundled
- [ ] All three options are genuinely viable (could you argue for each with a straight face?)
- [ ] Each option has different tradeoffs, not just different effort levels
- [ ] Recommendation exists and references specific tradeoffs
- [ ] Outcome logged in decision ledger with reasoning

---

## Changelog

| Version | Date | Change |
|---------|------|--------|
| 1.0 | YYYY-MM-DD | Initial public example version. Replace this row with your first real change. |
