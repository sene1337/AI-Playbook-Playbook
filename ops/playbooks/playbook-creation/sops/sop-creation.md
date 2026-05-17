# Creating SOPs

**Objective:** Repeatable process for turning knowledge into durable SOPs.

**Prerequisites:** Read the Playbook Creation playbook (format specs + principles).

**Owner:** [AGENT_SLUG]

---

## Procedure

### Step 1: Identify the source

Where is the knowledge coming from?

| Source | Method |
|--------|--------|
| You already do it but keep forgetting | **Capture Method** — document what exists before you forget again |
| Someone else knows how | **Interview Method** — they explain, you explore and document |
| Nobody's done it yet | **Camcorder/Black Box Method** — do it once, record every step, extract the SOP. Tool: QuickTime screen recording → transcribe with Whisper → extract steps. See `sops/camcorder-method.md` when available. |

Most SOPs come from the first two — something already works, it just isn't written down.

### Step 2: Explore before writing

Don't assume you know how it works. For agents, look at the actual state:

```bash
find /path -name "*keyword*"
ls -la /path/
cat /path/file
```

The inbox SOP failed its first draft because the author assumed it was email — it was files in folders. Assume nothing.

### Step 3: Pick a template

Grab a skeleton from `sops/sop-templates.md` — standard, tool, or lightweight. Use judgment. If none fit, start blank using the format spec from the playbook.

### Step 4: Draft it

Write to `ops/playbooks/<category>/sops/<name>.md`.

Rules:
- Start at version 1.0
- Changelog is append-only
- Fold everything into the defined sections — no extras
- If something doesn't fit, add it but flag the reviewer — log the change in the changelog and add an item to your agenda doc to discuss the change with the reviewer
- **Name for the general case** — e.g. `workspace-inbox.md` not `claude-cowork-inbox.md`. Pressure-test: "Would this name still work if the tool changed, the team doubled, or the use case expanded?"

### Step 5: Review

Run the Review Protocol (`sops/review-protocol.md`). For lightweight/fast-track SOPs, the quick self-checklist is enough for v1.0.

### Step 6: Link and commit

- Link from the parent playbook's "Linked SOPs" section
- If it's a tool SOP, add a row to TOOLS.md
- Commit everything in one shot

### Step 7: Feed back

Did you learn a new pattern, failure mode, or quality bar during this build? Update the parent playbook — not just the SOP. Learnings in the playbook help every future SOP.

If nothing new was learned, skip this step.

---

## Quality Check

- [ ] Matches the correct format for its type
- [ ] A stranger (or post-compaction agent) can execute without asking questions
- [ ] Name is general enough to survive scope changes
- [ ] Linked from parent playbook
- [ ] Parent playbook's "Linked SOPs" section includes this SOP
- [ ] Review protocol completed (full or lightweight as appropriate)

---

## Changelog

| Version | Date | Change |
|---------|------|--------|
| 1.0 | YYYY-MM-DD | Initial public starter version. Replace this row with your first real change. |
