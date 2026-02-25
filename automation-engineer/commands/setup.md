---
description: Initialize a project — collect information, create PRD, document tools, build action plan
---

# Project Setup

Initialize a new automation project. The folder structure already exists in `project/`. Your job is to collect information and populate the files.

## Step 1 — Collect project information

Have a conversation with the user to understand the project. Ask about:

1. **Project type**: Is this an internal project or for a client?
2. **Client**: If external — who is the client? Brief description.
3. **Project name**: What do we call this project?
4. **Objective**: What are we building? What's the goal?
5. **Problem**: What pain or problem are we solving?
6. **Priorities**: What are the top 3 priorities? What matters most?
7. **Tools**: Which tools and services will we use? (n8n, Supabase, Zendesk, APIs, etc.)
8. **Initial plan**: What are the first steps? Where do we start?

Collect everything conversationally. Don't dump all questions at once — guide the user through them naturally.

## Step 2 — Create the PRD

Use the collected information to create `project/prd.md`. Follow the template from the `project-context` skill.

The PRD should include:
- Client information
- Objective and problem
- Priorities (numbered)
- Tools table (linking to each tool's file)
- Scope (in/out)
- Empty decisions table (will be filled as project progresses)

## Step 3 — Document each tool

For each tool the user mentioned:

1. Create `project/tools/{name}.md` following the template from `project-context`
2. Fill in: purpose in the project, what credentials are needed, how the project is organized inside the tool
3. **Ask the user**: "Do you want me to research plugins/MCP and API documentation for {tool} now, or should I mark it as pending for later?"
   - If **now**: Use the `tool-research` skill to search for plugins/MCP, find API docs, and document findings
   - If **later**: Mark the Plugin/MCP and API Research sections as "Pending research"

## Step 4 — Build the action plan

Create `project/roadmap.md` with an initial action plan:

1. Based on the priorities and tools discussed, break the project into phases
2. Each phase has concrete tasks
3. Follow the format from the `task-planning` skill
4. Include a validation phase

## Step 5 — Confirm setup

Present a summary of everything that was created:

```
## Setup complete

**Project**: {name}
**Client**: {type — name}
**Objective**: {1-sentence summary}
**Tools**: {list}
**Credentials pending**: {list of what needs to be configured}
**Research pending**: {list of tools that need API research}

Project structure:
project/
├── prd.md              ← filled
├── roadmap.md          ← filled with {n} tasks in {n} phases
├── tools/              ← {n} tool files created
├── research/           ← ready for research
├── tasks/              ← ready for daily tasks
├── workflows/          ← ready for workflows
├── scripts/            ← ready for scripts
└── memory/             ← ready for session context

Next steps:
1. {first actionable item from roadmap}
2. {second item}
3. {third item}
```

Ask if anything is missing or needs to be adjusted.
