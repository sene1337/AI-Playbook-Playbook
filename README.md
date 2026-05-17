# AI Playbook Playbook

A starter repo for building an AI-agent operating system around playbooks, SOPs, tool SOPs, file routing, and agent boot instructions.

This is intentionally small and practical. The goal is not "documentation for documentation's sake". The goal is that a human or AI agent can pick up a process after context loss and execute it without the original author present.

## What is included

```text
ops/playbooks/playbook-creation/playbook-creation.md
ops/playbooks/playbook-creation/sops/sop-creation.md
ops/playbooks/playbook-creation/sops/sop-templates.md
ops/playbooks/workspace/workspace-organization.md
ops/playbooks/workspace/sops/file-routing.md
examples/agent-setup/AGENTS.md
examples/agent-setup/TOOLS.md
```

## Where these files should live

Recommended workspace layout:

```text
workspace/
├── memory/     # what happened: daily logs, active tasks, state
├── docs/       # what you know: projects, research, drafts, deliverables
├── ops/        # how you work: playbooks, SOPs, decisions, operating rules
├── scripts/    # reusable helper scripts
└── workbenches/# local dev/tooling sandboxes
```

Recommended playbook/SOP paths:

```text
ops/playbooks/<category>/<playbook-name>.md
ops/playbooks/<category>/sops/<sop-name>.md
ops/playbooks/tools/sops/<tool-name>.md
```

Example:

```text
ops/playbooks/playbook-creation/playbook-creation.md
ops/playbooks/playbook-creation/sops/sop-creation.md
ops/playbooks/playbook-creation/sops/sop-templates.md
ops/playbooks/workspace/workspace-organization.md
ops/playbooks/workspace/sops/file-routing.md
```

## How we route files

The routing model is three-tier:

- `memory/` = what happened
- `docs/` = what we know
- `ops/` = how we work

New SOPs go here:

```text
ops/playbooks/<category>/sops/<name>.md
```

New playbooks go here:

```text
ops/playbooks/<category>/<name>.md
```

Tool SOPs go here:

```text
ops/playbooks/tools/sops/<tool-name>.md
```

Reusable scripts go here:

```text
scripts/<name>.sh
scripts/<name>.py
```

Local build sandboxes go here:

```text
workbenches/<bench-name>/
```

The included workspace docs explain the full routing rules:

- `ops/playbooks/workspace/workspace-organization.md`
- `ops/playbooks/workspace/sops/file-routing.md`

## How to create a new SOP

1. Read the parent playbook.
2. Read `ops/playbooks/playbook-creation/sops/sop-creation.md`.
3. Pick a template from `ops/playbooks/playbook-creation/sops/sop-templates.md`.
4. Write the SOP to `ops/playbooks/<category>/sops/<name>.md`.
5. Link it from the parent playbook's Linked SOPs section.
6. If it is a tool SOP, add it to your tool index.
7. Commit the change.

## How the agent knows to use playbooks and SOPs

The pattern is:

1. Put agent boot rules in a root file such as `AGENTS.md`.
2. Put the tool/SOP index in a root file such as `TOOLS.md`.
3. Tell the agent to check `TOOLS.md` before using tools or inventing workflows.
4. Tell the agent to route repeatable processes through `ops/playbooks/`.
5. Tell the agent to write durable learnings to files, not just chat.

Included examples:

```text
examples/agent-setup/AGENTS.md
examples/agent-setup/TOOLS.md
```

These are sanitized examples with placeholder slugs:

- `[HUMAN_SLUG]`
- `[AGENT_SLUG]`
- `[LOCAL_MACHINE_SLUG]`
- `[LOCATION_SLUG]`
- `[HUMAN_HANDLE_SLUG]`

Replace those with your own names, handles, machine names, and operating constraints.

## Tool SOPs

A Tool SOP is for any capability where usage patterns and failure modes matter.

Recommended location:

```text
ops/playbooks/tools/sops/<tool-name>.md
```

Recommended template:

```text
ops/playbooks/playbook-creation/sops/sop-templates.md
```

A good Tool SOP includes:

- quick reference
- when to use it vs alternatives
- usage patterns
- gotchas and lessons
- changelog

## Important customization step

Before using this repo as-is, search for placeholder slugs and replace them:

```bash
grep -R "\[.*_SLUG\]" -n .
```

Then update the changelogs as you make real changes.
