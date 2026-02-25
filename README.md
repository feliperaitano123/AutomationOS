# AutomationOS

Operating system for automation projects with Claude Code.

## Quick start

```bash
# 1. Create a new project from this template
gh repo create my-project --template feliperaitano123/AutomationOS --clone --private
cd my-project
git submodule update --init

# 2. Open in Claude Code
claude

# 3. Initialize the project
/setup
```

That's it. The Automation Engineer will guide you through creating a PRD, documenting tools, and building an action plan.

> **Note**: You need [GitHub CLI](https://cli.github.com/) (`gh`) and [Claude Code](https://claude.ai/claude-code) installed.

## Available commands

| Command | What it does |
|---------|-------------|
| `/setup` | Initialize project — create PRD, document tools, build action plan |
| `/task` | Manage daily tasks — start, check status, or close tasks |
| `/status` | Project overview — PRD, roadmap progress, tools, active task |
| `/tool` | Manage tools — list, add, or inspect tools with credentials and research |

## Project lifecycle

```
/setup          → Create PRD, document tools, build roadmap
    ↓
/task start     → Open a daily task, load context, start working
    ↓
/task done      → Close task, record results, update roadmap
    ↓
/status         → Check progress at any time
    ↓
/tool add       → Add new tools as the project grows
```

## Structure

```
AutomationOS/
├── .claude/
│   └── settings.json                ← Enabled plugins (project-local)
├── .claude-plugin/
│   └── marketplace.json             ← Plugin catalog
│
├── automation-engineer/             ← Plugin: the automation engineer
│   ├── agents/
│   │   └── automation-engineer.md
│   ├── commands/
│   │   ├── setup.md
│   │   ├── task.md
│   │   ├── status.md
│   │   └── tool.md
│   └── skills/
│       ├── project-context/
│       ├── task-planning/
│       └── tool-research/
│
├── n8n-skills/                      ← Plugin: specialized n8n skills
│   └── skills/ (7 skills)
│
├── project/                         ← Project data (isolated)
│   ├── prd.md                       ← Project Requirements Document
│   ├── roadmap.md                   ← Roadmap and progress tracking
│   ├── tools/                       ← One file per tool
│   ├── tasks/                       ← Daily task logs
│   ├── research/
│   │   ├── apis/                    ← API research
│   │   └── notes/                   ← Technical notes
│   ├── workflows/                   ← Exported n8n workflows
│   ├── scripts/                     ← Helper scripts
│   └── memory/                      ← Cross-session context
│
├── .gitignore
└── README.md
```

## Included plugins

| Plugin | Description |
|--------|------------|
| `automation-engineer` | PRD-driven project management, daily tasks, tool research, progress tracking |
| `n8n-skills` | 7 specialized skills for n8n workflow development |

## Isolation principle

Each project is an independent clone of AutomationOS. This guarantees:

- Credentials never mix between projects
- Claude's context is always project-specific
- Each project can evolve independently
- Nothing is installed globally in Claude Code
