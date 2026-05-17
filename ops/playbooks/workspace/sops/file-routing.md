# File Routing SOP

**Objective:** Route every new file to the correct location at time of creation — zero misplaced files, zero "I'll file it later."

**Scope:** Every file created or moved in the workspace.

**Responsibilities:**

| Role | Person | Responsibility |
|------|--------|----------------|
| Executor | [AGENT_SLUG] / [HUMAN_SLUG] | Follows this SOP for every new file |
| Architect | [AGENT_SLUG] | Updates this SOP when folder structure changes |

---

## Materials / Prerequisites

- Access to `ops/playbooks/workspace/workspace-organization.md` (folder structure map)
- The three-tier model: **memory/** (what happened) · **docs/** (what we know) · **ops/** (how we work)

---

## Procedure

### 1. Identify the Tier First

Ask: **Which tier does this belong to?**

| If it records... | Tier |
|-----------------|------|
| Events, logs, daily records, task state | **memory/** |
| Knowledge, research, projects, content | **docs/** |
| Process, protocol, operations, schedules | **ops/** |

### 2. Identify the Document Type

| If it's... | Then it's a... |
|-----------|----------------|
| Domain guide, frameworks, philosophy, anti-patterns | **Playbook** |
| Step-by-step repeatable procedure | **SOP** |
| 1-3-1, deep dive, corpus query, decision analysis | **Research** |
| Project-specific (transcripts, plans, merge docs) | **Project file** |
| Daily log, weekly plan, task state, journal | **Memory file** |
| Subagent output pending review, WIP | **Draft** |
| Live state tracker (cron roster, phone numbers, decision archive) | **Ops doc** |
| Items needing someone else's input, sync prep, weekly plans | **Agenda** |

### 3. Route to the Correct Folder

| Document Type | Destination |
|--------------|-------------|
| Playbook | `ops/playbooks/<category>/<name>.md` |
| SOP | `ops/playbooks/<category>/sops/<name>.md` |
| Research / 1-3-1 | `docs/research/<name>.md` |
| Project file | `docs/projects/<project-name>/` |
| Daily log | `memory/YYYY-MM-DD.md` |
| Weekly plan | `ops/agenda/weekly/YYYY-MM-DD.md` |
| Running agenda | `ops/agenda/<owner>-agenda.md` |
| Active tasks | `memory/active-tasks.md` |
| Journal / mindset | `memory/mindset/` |
| SELF growth journal | `memory/mindset/SELF.md` |
| [HUMAN_SLUG] personal reference docs (health notes, vision, profile docs) | `memory/[human-slug]/<name>.md` |
| Draft / WIP | `docs/drafts/<name>.md` |
| Ops state doc (rosters, registries, trackers) | `ops/<name>.md` |
| Decision artifacts (ledger, archive, directive tracking, decision experiments) | `ops/decisions/` |
| Continuous-improvement artifacts (regressions, learnings, capability gaps, behavior changelog, retrospectives) | `ops/continuous-improvement/` |
| Incident tracker / bug investigation / outage write-up / agent or coding-agent postmortem | `ops/remediation/incidents/<name>.md` |
| Remediation board / active ops debt queue | `ops/remediation/` |
| Hack/workaround log | `ops/remediation/hacks.md` (legacy: `ops/hack-audit-log.md`) |
| Team record | `docs/team/<name>.md` |
| Event supplement | `memory/YYYY-MM-DD-<event>.md` (same date as parent log) |
| HTML render | Alongside its `.md` source |
| Utility script | `scripts/<name>.sh` or `scripts/<project>/` |
| Workbench / local dev scaffold | `workbenches/<bench-name>/` — for the tool itself, not final outputs |
| Screenshots (task/debug) | Trash after use — they served their purpose. If a screenshot is a deliverable for [HUMAN_SLUG], it goes in `docs/deliverables/` |
| Deliverables for [HUMAN_SLUG] (HTML, PDF, charts, written pieces) | `docs/deliverables/` |
| Skill build artifacts (.skill, staging dirs) | `tmp/` during build → trash after publish |
| Removed/archived skills | Trash (recoverable from git history or GitHub) |
| Skill-generated research (trawl reports, etc.) | `docs/research/<slug>.md` — same as any research |
| Project-specific logs (transcription, batch, download) | `docs/projects/<project>/logs/` — keeps context with the project |
| General completed logs (not project-specific) | `logs/archive/` — historical, useful for diagnosis |
| Conversation extracts (session mining) | `logs/archive/` — raw session data for future analysis |
| OpenClaw gateway logs (archived) | `logs/archive/` — saved from `/tmp/openclaw/` before rotation |
| Durable source checkouts / local repo clones used beyond one shell | outside system temp; durable project path only — never `/tmp` or `/private/tmp` |
| Local dev builds that may be re-run after reboot | durable repo/build path only — never system temp |
| PATH wrappers / symlinks / LaunchAgents pointing to local source builds | durable target only — never system temp |
| OpenClaw module/symlink targets (e.g., `~/.openclaw/lib/node_modules/openclaw`) | must resolve to durable path (workspace-dev or other persistent location), never `/tmp`/`/private/tmp` |
| Running OpenClaw gateway process origin (command/cwd/module path) | must not originate from system temp; if any live process references `/tmp`/`/private/tmp`, treat as P0 drift and rotate to durable runtime |
| **OpenClaw extensions/plugins** | `~/.openclaw/extensions/<plugin-id>/` — canonical location. Never `workspace/.openclaw/extensions/` (accidental discovery, no provenance). Never `~/` root or `~/plugin-name/` (orphan). |
| **Skill source repos** | `workspace/skills/<name>/` with `.git` + GitHub remote — same location OpenClaw loads from. Never standalone dirs in `~/`. |
| **Session history (JSONL)** | `~/.openclaw/agents/main/sessions/` — biographical data, powers memory search. Always migrate. |
| **Memory files (daily logs, mindset, tasks)** | `memory/` — core continuity. Always migrate. |
| **Identity files (SOUL, IDENTITY)** | Workspace root — who I am. Always migrate. |
| **SELF growth journal** | `memory/mindset/SELF.md` — identity-growth history. Always migrate. |
| **Boot files (AGENTS, MEMORY, TOOLS, USER)** | Workspace root — operational identity. Always migrate. |
| **Git history** | `.git/` — full version history of every decision. Always migrate (bundle + restore). |
| **Large media (audio, video, raw downloads)** | iCloud Drive or external — NOT in workspace. Symlink if workspace needs to reference. |
| **OpenClaw internal state (auth, restart sentinels)** | Do NOT migrate — fresh install regenerates. |
| **Gateway logs (corrupted/bloated)** | Archive compressed copy, do NOT restore as active. |
| **Config (openclaw.json)** | Copy + patch paths. Do NOT copy verbatim if usernames/paths differ. |

### 4. Apply Naming Conventions

- **Lowercase, hyphens only:** `weekly-planning.md`, not `WeeklyPlanning.md`
- **Descriptive:** `delegation-checklist.md`, not `dc-v2.md`
- **No dates in filenames** unless it's a log or archive
- **Format for dated files:** `<subject>-<descriptor>-YYYY-MM-DD.<ext>` (e.g., `bitcoin-treasury-analysis-2026-02-26.md`)
- **Scripts:** no date needed (e.g., `dan-martell-qa-extract.py`)
- **Banned suffixes:** Never use `v2`, `v3`, `final`, `improved`, `new`, `old` in filenames. Use git history for versions.
- **Draft exception:** Active drafts under review in `docs/drafts/` CAN use `-v1`, `-v2` etc. while iterating with [HUMAN_SLUG]. Winner gets clean name and routes to final home. Losers get trashed.
- **Draft SOP/Playbook clarity rule:** If a draft must temporarily live in a canonical SOP/playbook folder, filename MUST include `-DRAFT` before `.md` (example: `communication-DRAFT.md`). Never leave draft docs with canonical names in canonical folders.
- **Origin story required:** Every new standalone file (logs, registries, trackers, playbooks, SOPs, protocols, research docs) gets a one-line blockquote at the top stating when it was created, who made it, and why.
- **Parent process link required:** If a file is created by or output from a process that has an SOP or playbook as its parent, the Origin block MUST link to that parent process. This gives any human reader instant context on *why this file exists and what system produces it.*
- **Changelog required:** Every new standalone file also gets a `## Changelog` section at the bottom with a `v1.0` row describing the creation context.
- **Exemptions:** Daily logs (`memory/YYYY-MM-DD.md`), generated artifacts/exports, and temporary files in `tmp/`.

Example (standalone):
```
> **Origin:** Created Feb 13, 2026 by [AGENT_SLUG]. "Save game" file
> for crash recovery after compaction kept wiping task context.
```

Example (process output with parent link):
```
> **Origin:** Generated by the Decision Session Miner (nightly
> cron). Parent process: [Decision Session Mining SOP](
> ops/playbooks/decisions/sops/decision-session-mining.md).
> Append-only — new proposals added nightly, cleared after
> morning review.
```

Changelog template:
```
## Changelog

| Version | Date | Change |
|---------|------|--------|
| 1.0 | YYYY-MM-DD | Initial public starter version. Replace this row with your first real change. |
