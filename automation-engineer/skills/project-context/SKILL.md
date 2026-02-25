---
name: project-context
description: Reads and maintains project context — PRD, roadmap, tools, tasks, and decisions
---

# Project Context

Context management skill. Auto-activates when the user talks about the project, its tools, credentials, or configuration.

## When to activate

- Start of session on an automation project
- Questions about "what are we building", "what's the goal", "which tools"
- References to credentials, APIs, services
- Technical decisions that need to be recorded

## How it works

### 1. Find existing context

When starting work on a project, look for these files:

- `project/prd.md` — Objective, client, scope, priorities, decisions
- `project/roadmap.md` — Task phases, progress, what's done and pending
- `project/tools/*.md` — One file per tool with purpose, credentials, organization
- `project/tasks/` — Daily task logs (latest for current context)
- `project/research/apis/` — API research documentation
- `project/research/notes/` — Technical notes and insights
- `project/memory/` — Previous session context

If found, read and use as base. If not found, suggest running `/setup`.

### 2. Keep context updated

When there are new decisions or changes:

- Record in `project/prd.md` in the decisions table
- Create/update `project/tools/{name}.md` if new tools are added
- Save API research in `project/research/apis/`
- Save technical notes in `project/research/notes/`
- Update `project/roadmap.md` when tasks are completed or priorities change

### 3. Document templates

**project/prd.md**:
```markdown
# {Project Name}

## Client
- **Type**: Internal / External
- **Client**: {name or description}
- **Contact**: {if applicable}

## Objective
What we're building and why.

## Problem
What problem or pain we're solving.

## Priorities
1. {priority 1 — most important}
2. {priority 2}
3. {priority 3}

## Tools
| Tool | Purpose | File |
|------|---------|------|
| n8n | Workflow orchestration | tools/n8n.md |

## Scope
### In scope
- ...

### Out of scope
- ...

## Decisions
| Date | Decision | Reason |
|------|----------|--------|
```

**project/tools/{name}.md**:
```markdown
# {Tool Name}

## Purpose
Why we use this tool in the project.

## Credentials
| Type | Status | Where to configure |
|------|--------|--------------------|
| API Key | pending/configured | {link to dashboard} |

> NEVER store secrets, tokens, or passwords in this file.
> Only record what is needed and where to configure it.

## Organization
{How the project is organized inside this tool}
{Ex: folders in n8n, tables in Supabase, etc.}

## Plugin/MCP
- **Available**: yes/no
- **Installed**: yes/no
- **Details**: {plugin name, how to use}

## API Research
- **Documentation**: {link}
- **Research file**: research/apis/{name}-api.md
- **Key endpoints**: {list}

## Notes
{Observations, limitations, tips}
```

**project/roadmap.md**:
```markdown
# Roadmap — {Project Name}

## Overview
{one sentence project summary}

## Progress
- Total tasks: {n}
- Completed: {n}
- In progress: {n}
- Pending: {n}

## Phase 1: {name}
- [x] Task 1 — description (tasks/2026-02-25-slug.md)
- [ ] Task 2 — description
- [ ] Task 3 — description

## Phase 2: {name}
- [ ] Task 4 — description (depends on: Task 2)
- [ ] Task 5 — description

## Phase 3: Validation
- [ ] Task 6 — test complete flow
```

**project/tasks/{YYYY-MM-DD}-{slug}.md**:
```markdown
# Task: {title}

- **Date**: {YYYY-MM-DD}
- **Status**: in_progress / completed / partial
- **Roadmap phase**: Phase {n}

## Objective
What we're doing in this task.

## Tools
- {tool 1} (tools/{name}.md)
- {tool 2}

## Execution
{What was done, step by step}

## Result
{What was delivered/produced}

## Pending
{What's left for the next task}

## Suggested next task
{What comes next based on the roadmap}
```

**project/memory/session-{YYYY-MM-DD}.md**:
```markdown
# Session {YYYY-MM-DD}

## Context
{What was worked on in this session}

## Decisions made
- {decision 1}
- {decision 2}

## Files modified
- {list}

## Current state
{Summary of project state at end of session}
```

## Rules

- Never store secrets, tokens, or passwords in any file
- Always ask before making decisions that change project scope
- Keep docs simple — they're quick reference, not exhaustive documentation
- All project files live inside `project/` — never at the root
