---
name: status
description: Show project overview — PRD, roadmap progress, tools, active task, and research
---

# Project Status

Read the project files and present an organized overview.

## What to show

### 1. Project
Read `project/prd.md` and summarize:
- Client and project name
- Objective in one sentence
- Top priorities
- Latest recorded decisions

### 2. Roadmap
Read `project/roadmap.md` and show:
- Progress: X of Y tasks completed
- Current phase
- Next pending tasks
- Any blockers

### 3. Active Task
Check `project/tasks/` for any task with status `in_progress`:
- What's being worked on
- Which tools are involved
- What's been done so far

### 4. Tools
List all files in `project/tools/` and show for each:
- Name and purpose
- Credential status (configured/pending)
- Plugin/MCP status

### 5. Research
Check `project/research/` and list:
- API research docs (in `project/research/apis/`)
- Technical notes (in `project/research/notes/`)

### 6. Workflows
Check `project/workflows/` and list:
- Existing workflows
- Status of each (if documented)

## Output format

Present everything in a compact, actionable view. Example:

```
## Project: {name}
**Client**: {type — name}
**Objective**: {1-sentence summary}

## Roadmap: {X}/{Y} tasks completed
**Phase**: {current phase name}
- [x] Completed task 1
- [x] Completed task 2
- [ ] **Next**: Pending task 3
- [ ] Pending task 4

## Active Task: {title or "None"}
{brief description of what's in progress}

## Tools ({n})
| Tool | Credentials | Plugin | Research |
|------|-------------|--------|----------|
| n8n | configured | n8n-skills | done |
| Supabase | pending | MCP | done |

## Research ({n} docs)
- zendesk-api.md — Zendesk REST API documentation

## Workflows ({n})
- webhook-processor.json
```

If the project files don't exist or are empty, suggest running `/setup`.
