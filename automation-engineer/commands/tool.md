---
name: tool
description: Manage project tools — list, add, or inspect tools with credentials and research
---

# Tool Management

Manage the tools and services used in the project.

## Usage

- `/tool` — List all project tools and their status
- `/tool add [name]` — Add a new tool to the project
- `/tool [name]` — Show details of a specific tool

---

## `/tool` (no arguments)

1. List all files in `project/tools/`
2. For each tool, show:
   - Name and purpose
   - Credential status (configured/pending)
   - Plugin/MCP status (installed/available/none)
   - Research status (done/pending)
3. If no tools exist, suggest running `/setup`

Format:
```
## Project Tools

| Tool | Purpose | Credentials | Plugin/MCP | Research |
|------|---------|-------------|------------|----------|
| n8n | Workflow orchestration | configured | n8n-skills | done |
| Supabase | Database | pending | MCP available | pending |
| Zendesk | Support platform | pending | none | pending |
```

---

## `/tool add [name]`

### 1. Collect information
If the user provided a name, use it. Otherwise, ask:
- What tool are you adding?
- What's its purpose in this project?
- What credentials does it need?
- How is the project organized inside this tool? (folders, groups, etc.)

### 2. Create tool file
Create `project/tools/{name}.md` following the template from `project-context`.

Fill in all sections with the information collected.

### 3. Research (ask user)
Ask: "Do you want me to research plugins/MCP and API documentation for {name} now, or mark it as pending?"

- If **now**: Use the `tool-research` skill
  - Search for Claude Code plugins or MCP servers
  - Find API documentation
  - Document findings in `project/research/apis/{name}-api.md`
  - Update the tool file with research results
- If **later**: Mark Plugin/MCP and API Research sections as "Pending research"

### 4. Update PRD
Add the new tool to the tools table in `project/prd.md`.

### 5. Confirm
Show what was created and any pending actions (credentials to configure, research to do).

---

## `/tool [name]`

1. Read `project/tools/{name}.md`
2. Show all details: purpose, credentials, organization, plugin status, research
3. If research exists, also read and summarize `project/research/apis/{name}-api.md`
4. Suggest actions if anything is pending (credentials, research, plugin installation)

---

## Security rules

- NEVER store secrets, tokens, passwords, or API keys in project files
- Only record what's needed, where to configure it, and the status
- Guide the user to use environment variables or secret vaults
- If the user pastes a secret in the chat, warn them immediately not to do that
