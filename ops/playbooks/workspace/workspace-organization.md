# Workspace Organization

## Objective

Any file created in this workspace can be found by a human or AI in under 30 seconds by drilling into logical categories — without scanning flat lists or relying on memory.

## Scope

Applies to every file created or moved in this workspace.

## Roles

| Role | Person | Responsibility |
|------|--------|----------------|
| **Architect** | [AGENT_SLUG] | Creates and updates this playbook; makes structural decisions |
| **Executor** | [AGENT_SLUG] / [HUMAN_SLUG] | Files every new document in the correct location at time of creation |
| **Reviewer** | [HUMAN_SLUG] + [AGENT_SLUG] | Weekly audit against success criteria during planning session |

## Core Philosophy

Everything has a place. No clutter, no mess. The structure follows a logic that eliminates decision fatigue — when you create a file, where it goes should be obvious. When you need a file, finding it should take seconds, not searching.

A clean workspace is readable by both humans and LLMs. Flat folders, vague names, and orphaned files cost time every single day. The structure is the system — maintain it and it maintains you.

---

## Three-Tier Structure

The workspace is organized around three distinct concerns:

```
workspace/
├── memory/     ← what happened    (state, logs, daily records, task tracking)
├── docs/       ← what we know     (research, projects, content, drafts, security)
└── ops/        ← how we work      (playbooks, SOPs, agenda, operational docs)
```

**When in doubt:** Is it a record of events? → `memory/`. Is it knowledge or research? → `docs/`. Is it process, protocol, or operations? → `ops/`.

---

## Folder Taxonomy

### `memory/` — What Happened

| Path | Contents |
|------|----------|
| `memory/YYYY-MM-DD.md` | Daily logs |
| `memory/active-tasks.md` | Current task state — crash recovery |
| `memory/lessons-learned.md` | Extracted lessons from failures/wins |
| `memory/mindset/` | Journal, identity, weekly postmortems |

### `docs/` — What We Know

| Path | Contents |
|------|----------|
| `docs/research/` | 1-3-1 analyses, deep dives, corpus queries |
| `docs/projects/` | One folder per project |
| `docs/drafts/` | WIP, subagent output pending review |
| `docs/content/` | Content pieces, Nostr drafts |
| `docs/security/` | Security audits, access logs |
| `docs/reference/` | Reference material (not process) |
| `docs/deliverables/` | Things built for [HUMAN_SLUG] — visualizations, HTMLs, PDFs, charts, written pieces |
| `docs/INDEX.md` | Workspace navigation index |

### `ops/` — How We Work

| Path | Contents |
|------|----------|
| `ops/playbooks/` | Domain playbooks and SOPs |
| `ops/agenda/` | Weekly agenda files |
| `ops/decisions/` | Decision ledger, archive, directive tracking |
| `ops/continuous-improvement/` | Regressions, personality changelog, learnings index, capability gaps, retrospectives |
| `ops/remediation/` | Active operational debt: incident trackers, bug investigations, outage write-ups, postmortems, hacks/workarounds, upstream watches, fixes awaiting verification |
| `ops/operational-sops.md` | Node exec rules, config SOPs |
| `ops/cron-roster.md` | Scheduled jobs |
| `ops/live-ops-guardrails.md` | Guardrails for live production changes |
| *(other ops docs)* | Operational state, rosters, registries |

#### Playbook Structure (within `ops/playbooks/`)

| Type | What It Is | Where |
|------|-----------|-------|
| **Playbook** | Domain-level guide. How we think. Frameworks, philosophy, anti-patterns. | `ops/playbooks/<category>/<name>.md` |
| **SOP** | Step-by-step procedure for one repeatable task. | `ops/playbooks/<category>/sops/<name>.md` |

Playbook categories: `decisions/`, `delegation/`, `planning/`, `playbook-creation/`, `safety/`, `knowledge/`, `tools/`, `workspace/`

### `logs/` — Ephemeral Working Data (gitignored)

| Path | Contents |
|------|----------|
| `logs/` | Active trawl working files, runtime output — ephemeral by default |
| `logs/archive/` | Gateway logs, conversation extracts, completed logs worth keeping for diagnosis |

### `workbenches/` — Tooling Garages / Local Dev Sandboxes

| Path | Contents |
|------|----------|
| `workbenches/<bench-name>/` | Local tooling scaffolds, package manifests, dev environments, reusable tool-specific code, and sandbox setup for making future work easier |

**Workbench rule:** `workbenches/` is for the tool itself — scripts, package manifests, configs, local dev envs, and setup notes. It is **not** the default home for final project outputs, large media exports, frame dumps, downloaded source clips, or long-lived render intermediates.

**Avoid semantic confusion:** `workbenches/` is a filesystem category for local sandboxes. `TOOLS.md` is the registry/index of documented capabilities and SOPs.

**Output routing rule:**
- Final creative/project outputs → `docs/projects/<project>/` or `docs/deliverables/`
- Short-lived render intermediates / temporary assets → `tmp/` (or project-local temp path that gets cleaned)
- Durable reusable helper scripts extracted from a workbench → `scripts/` or the canonical project folder

### `scripts/` — Utility Scripts

| Path | Contents |
|------|----------|
| `scripts/` | Reusable shell scripts, automation tools |
| `scripts/dan-martell/` | Mighty Networks download/extraction scripts |

### `tmp/` — Build Staging (gitignored)

| Path | Contents |
|------|----------|
| `tmp/` | Skill packaging, disposable build artifacts, short-lived test outputs — trash after publish. Not storage. |

**Important:** macOS system temp paths (`/tmp` and `/private/tmp`) are not workspace storage.
Anything important must be routed into `docs/`, `ops/`, `memory/`, `scripts/`, or `logs/archive/` before reboot.

### Durable Local Code / Build Rule

If we run software from source ahead of a packaged release:

- **Clone to a durable path** — never `/tmp` or `/private/tmp`
- **Run from a durable path** — not `.../tmp/<repo>/dist`
- **Any symlink, LaunchAgent, wrapper script, or PATH entry must target a durable path**
- **If the build matters after reboot, it is not allowed to live in system temp**

Default durable homes:
- workspace-adjacent repo clone outside system temp
- workspace `tmp/` only for disposable intermediates, never the canonical runtime path
- packaged install location managed by the tool's normal installer

Practical rule: if losing the folder on reboot would break a command, service, or feature we care about, that folder does **not** belong in system temp.

---

## Document Types

### Analysis & Research → `docs/research/`

| Type | Where |
|------|-------|
| 1-3-1 analysis | `docs/research/<name>.md` |
| Deep dive / corpus query | `docs/research/<name>.md` |
| Decision backing research | `docs/research/<name>.md` |

### Project Files → `docs/projects/`

| Type | Where |
|------|-------|
| Transcripts | `docs/projects/<name>/transcripts/` |
| Project docs | `docs/projects/<name>/` |

### Filing a New Document

For the step-by-step routing procedure, naming conventions, edge cases, and common pitfalls, see **[File Routing SOP](sops/file-routing.md)**.

---

### Linked SOPs

- [File Routing](sops/file-routing.md)

## Success Criteria

| # | Criterion | 1 (Failing) | 5 (Excellent) |
|---|-----------|-------------|---------------|
| 1 | Every new file is in the correct tier at creation | Files dumped in wrong spots | Zero misplaced files |
| 2 | A stranger can find any doc from folder structure alone | Needs author guidance | Self-navigable by drilling down |
| 3 | No folder has >15 files without subcategories | Flat dumps everywhere | Clean hierarchy, logical grouping |
| 4 | Drafts cleared within 7 days | 10+ stale drafts | Zero stale drafts |
| 5 | File naming is consistent | Mixed case, dates in names, abbreviations | 100% lowercase-hyphen, descriptive |

## Review Cadence

- **On every new file:** Executor files in the correct tier at time of creation
- **Weekly:** [HUMAN_SLUG] + [AGENT_SLUG] review against the 5 success criteria during weekly planning
- **On structural change:** Update this playbook in the same commit

### Naming Conventions

- Lowercase, hyphens: `weekly-planning.md`
- Descriptive: `delegation-checklist.md`, not `dc-v2.md`
- No dates in filenames unless it's a log or archive

## Outcome

The workspace operates as a retrievable, navigable knowledge system. Any file created today is findable in six months without relying on memory, chat history, or search. A new executor can onboard in under 30 minutes by reading this playbook and browsing the folder structure.

---

## Changelog

| Version | Date | Change |
|---------|------|--------|
| 1.0 | YYYY-MM-DD | Initial public starter version. Replace this row with your first real change. |
