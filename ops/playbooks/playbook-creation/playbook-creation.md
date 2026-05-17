## 1. Playbook Creation

**Objective:** Every playbook and SOP is structured so someone new (or a post-compaction agent) can pick it up and execute without the author present. The system stays lightweight to avoid documentation overhead killing velocity.
**Owner:** [AGENT_SLUG] — creates and maintains this playbook
**Reviewer:** [HUMAN_SLUG] — validates playbooks/SOPs meet the standard
**Review:** Weekly

---

## 2. North Star Principles

1. **Day One Ready.** Any new human or post-compaction agent picks up a playbook and executes on day one with zero questions.

2. **Learn Once, Capture Forever.** A wise man learns from the mistakes of others, a fool learns from his own. Every process worth repeating gets captured.

3. **Ship Fast, Polish Later.** Documentation accelerates velocity, not kills it. Rapid capture and iterative polish beat perfectionism and heavy process.

4. **Inspection Is the Standard.** A playbook that isn't reviewed on cadence isn't a playbook — it's a wish. Nobody will respect what you don't inspect & you must inspect what you expect.

---

## 3. The Playbook

### A. Playbook Format (4 sections + changelog)

#### 1. Header

Top of every playbook (just like at the top of this playbook).

```
# [Playbook Name]

**Objective:** [One sentence. What does this playbook achieve?]
**Owner:** [Who maintains it]
**Reviewer:** [Who inspects outcomes]
**Review:** [Frequency — quarterly minimum]
```

**Roles:**

Three roles max:
- **Owner** — maintains the playbook, improves it
- **Executor** (optional) — runs the process, reports gaps. Skip if Owner is also Executor.
- **Reviewer** — inspects outcomes ("inspect what you expect")

#### 2. Principles

The soul of the playbook. 3–5 North Star statements that resist change as processes evolve. *(Situationally optional.)*

Start by asking: **"What problem are we solving? What outcome are we after? What does success look like?"** The answer becomes your principles.

Dan Martell calls these "North Star Principles." Each one is a sentence + a one-liner explanation. Examples from Dan's EA Playbook:

- **Prioritize Revenue:** Order tasks based on what will generate the biggest outcome to support revenue. Profit solves all problems.
- **Guard the Calendar:** CEO's time is the most valuable asset. Protect it like your job depends on it — because it does.

**For v1.0:** You may mark Principles "TBD — refine after first 3 executions" if domain understanding is still forming.

#### 3. The Play

The meat of the playbook — what gets done, in what rhythm/flow, with what frameworks. Use judgment for how to structure this based on the domain:

- **Cadence-based** (operational/recurring): Daily → Weekly → Monthly → Quarterly → Annual. *Example: EA Playbook, House Manager.*
- **Flow-based** (sequential process): Stage 1 → Stage 2 → ... → Close. *Example: Sell By Chat, Delegation.*
- **Framework-based** (branching decisions): If X → do Y, with named decision tools. *Example: Decision Architecture.*

This is where scripts, templates, checklists, and named frameworks live. If the executor can't copy-paste something, the playbook is incomplete.

#### 4. Failure Modes

What goes wrong and the fix. 3+ entries minimum. Name the failure, name the fix.

After Failure Modes, include a **Linked SOPs** subsection listing all SOPs that belong to this playbook. If none exist yet, write "None yet."

#### 5. Changelog

Bottom of every playbook. Append-only — never delete or modify previous entries.

```
## Changelog

| Version | Date | Change |
|---------|------|--------|
| 1.0 | YYYY-MM-DD | Initial public starter version. Replace this row with your first real change. |
