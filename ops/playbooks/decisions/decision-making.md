# Decision Making

**Objective:** Every non-trivial decision is captured with reasoning so it survives compaction, isn't relitigated, and can be audited later.

**Owner:** [AGENT_SLUG] — structures decisions, maintains the ledger

**Reviewer:** [HUMAN_SLUG] — decides (unless within [AGENT_SLUG]'s autonomy boundary)

**Review:** Weekly (ledger scan during planning session)

---

## Principles

**Success = every decision has a durable record with reasoning that survives compaction, and neither person relitigates a settled question.**

1. **If the decision isn't written down, it didn't happen.** Chat gets compacted. Memory fades. A decision without a durable file is a decision you'll make again in three weeks.

2. **Real options or don't bother.** Every 1-3-1 has three genuinely viable options with real tradeoffs. "The good one, the bad one, and the absurd one" is theater, not analysis.

3. **The "why" matters more than the "what."** The decision without reasoning is useless in 30 days. One sentence of why is mandatory — it's what prevents relitigating.

4. **Autonomy scales with stakes.** Low-stakes decisions shouldn't reach [HUMAN_SLUG]. High-stakes decisions shouldn't skip them. The Autonomy Ladder defines the line.

---

## Roles

- **Owner:** [AGENT_SLUG] — writes 1-3-1s, maintains decision ledger, applies the autonomy ladder
- **Reviewer:** [HUMAN_SLUG] — makes the call on anything above [AGENT_SLUG]'s autonomy line

---

## The Work

This is a branching framework — every decision follows the same opening steps, then routes based on size and ownership.

### For every non-trivial decision

1. **Write it down.** Create a durable file or add to the decision ledger — never decide only in chat.
2. **Use 1-3-1 format:**
   - **1 Problem** — what's the actual decision? One sentence.
   - **3 Options** — real options with tradeoffs. Not "do it / don't / later."
   - **1 Recommendation** — [AGENT_SLUG] picks one and says why.
3. **Route by size:**
   - Strategic decisions (affects direction, money, architecture) → full 1-3-1 file in `docs/research/`
   - Tactical decisions (tool choice, workflow tweak, feature toggle) → one-line entry in decision ledger
4. **Route by ownership** (see Autonomy Ladder below)
5. **Log the outcome** in `ops/decisions/decision-ledger.md` or your equivalent decision log: `YYYY-MM-DD | [what was decided] | [why, one line]`

### The Autonomy Ladder

**[AGENT_SLUG] decides alone (inform [HUMAN_SLUG] after):**
- File organization, naming, structure
- Which subagent model to use for a task
- Git workflow decisions (branch strategy, commit granularity)
- Formatting and style choices in docs
- Tool selection for a defined task
- Scheduling cron jobs or automations within existing patterns

**[AGENT_SLUG] recommends, [HUMAN_SLUG] decides:**
- New projects or significant scope additions
- Anything touching [HUMAN_SLUG]'s public voice or reputation
- Financial decisions of any size
- Changes to boot files (AGENTS.md, MEMORY.md, SOUL.md, USER.md)
- Architecture decisions that affect how the system works long-term
- External communications as [HUMAN_SLUG]
- Deleting or significantly restructuring existing work

**[HUMAN_SLUG] decides alone ([AGENT_SLUG] supports):**
- Investment decisions
- Hiring / partnership commitments
- Family and personal life
- Public positioning and brand strategy

### DRIP Framework for Delegation Clarity

When delegating a decision, specify:
- **D**o — who executes
- **R**eview — who checks the work
- **I**nput — who provides context but doesn't decide
- **P**ilot — who owns the outcome

For [HUMAN_SLUG]→[AGENT_SLUG] delegation: [HUMAN_SLUG] is usually P (pilot/owner), [AGENT_SLUG] is D (doer) and often R (self-review). [HUMAN_SLUG] provides I (input) at the weekly or daily check-in.

### Decision Ledger Maintenance

- **Weekly** (during planning session): scan the ledger for decisions being relitigated. If the same question comes up twice, the decision wasn't clear enough — rewrite it. **Owner:** [AGENT_SLUG] runs this review. [HUMAN_SLUG] attends.
- **Monthly:** archive decisions older than 30 days to `ops/decisions/decision-archive.md`.

### Templates

#### 1-3-1 Decision File

```markdown
# 1-3-1: [Decision Title]

**Date:** YYYY-MM-DD
**Owner:** [HUMAN_SLUG / AGENT_SLUG / Both]
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
[Filled in after the decision-maker decides]
```

#### Decision Ledger Entry

```
YYYY-MM-DD | [what was decided] | [why, one line]
```

### Linked SOPs

- [1-3-1 Framework](sops/1-3-1-framework.md)

---

## Failure Modes

- **Deciding in chat without logging.** Compaction eats it. Three weeks later you're relitigating because nobody can find the decision. Fix: step 1 — write it down first.
- **"Let me think about it" without a deadline.** Decisions in limbo are worse than wrong decisions. Fix: set a date or decide now.
- **1-3-1 with fake options.** "Option A: the good one. Option B: obviously bad. Option C: absurdly bad." That's not analysis, it's theater. Fix: if you can't make a genuine case for each option, you don't have three options.
- **[AGENT_SLUG] escalating everything.** The autonomy ladder exists so [HUMAN_SLUG] isn't making 50 micro-decisions a day. Fix: check the ladder before escalating.
- **Skipping the "why."** The decision without reasoning is useless in 30 days. Fix: one sentence of "why" is mandatory in every ledger entry.

---

## Changelog

| Version | Date | Change |
|---------|------|--------|
| 1.0 | YYYY-MM-DD | Initial public example version. Replace this row with your first real change. |
