---
name: tool-research
description: Researches tools, plugins, MCPs, and APIs — documents findings for project use
---

# Tool Research

Research skill for discovering and documenting tools, plugins, and APIs. Auto-activates when the user mentions a new tool, asks about integrations, or needs API documentation.

## When to activate

- User mentions a tool/service not yet in `project/tools/`
- Questions about "how to connect X", "is there a plugin for Y"
- Requests to research an API or service documentation
- Adding a new tool to the project
- Looking for MCP servers or Claude Code plugins for a specific service

## How it works

### 1. Check existing knowledge

Before researching, check:
- Does `project/tools/{name}.md` already exist?
- Is there research in `project/research/apis/{name}-api.md`?
- Is this tool already in the PRD (`project/prd.md`)?

If it exists, use it as base and only research what's missing.

### 2. Research the tool

For each tool, investigate in this order:

**a) Plugin/MCP discovery**
- Search for Claude Code plugins or MCP servers for the tool
- Check if the tool has an official MCP integration
- Use WebSearch: "{tool name} claude code plugin" or "{tool name} MCP server"
- Document what's available, how to install, and how to use

**b) API documentation**
- Find the official API documentation URL
- Identify authentication method (API key, OAuth, token, etc.)
- List the most relevant endpoints for the project's use case
- Note rate limits, pricing tiers, and important restrictions

**c) Integration patterns**
- How does this tool connect with the existing stack?
- If using n8n: does n8n have a native node for this tool?
- What credentials are needed and where to get them?

### 3. Document findings

Save research results in two places:

**Detailed research** → `project/research/apis/{name}-api.md`:
```markdown
# {Tool Name} — API Research

## Documentation
- **Official docs**: {URL}
- **API base URL**: {URL}
- **Authentication**: {method and details}

## Key endpoints
| Endpoint | Method | Purpose |
|----------|--------|---------|
| /api/v2/tickets | GET | List tickets |

## Authentication setup
{Step-by-step how to get credentials}

## Rate limits
{Limits and considerations}

## Integration with project
{How this tool connects with our stack}

## Notes
{Observations, gotchas, useful tips}
```

**Tool summary** → `project/tools/{name}.md` (update Plugin/MCP and API Research sections)

### 4. Recommend next steps

After research, suggest:
- Install plugin/MCP if available
- Configure credentials
- Create a task in the roadmap for integration work

## Known automation ecosystem

**Workflow orchestration**: n8n (self-hosted/cloud), Make (Integromat), Zapier
**Database and backend**: Supabase, Firebase, PlanetScale
**APIs and integrations**: Webhook.site (testing), Postman (docs/testing), RapidAPI
**AI and LLMs**: Claude API, OpenAI API, Groq
**Communication**: Slack, Discord, Telegram, SendGrid, Resend, Twilio
**Support**: Zendesk, Intercom, Freshdesk
**CRM**: HubSpot, Salesforce, Pipedrive
**Payments**: Stripe, Mercado Pago

## Rules

- Always check if research already exists before starting from scratch
- Prefer official documentation over third-party sources
- Save detailed research in `research/apis/`, summaries in `tools/`
- Note when information might be outdated and suggest re-research
- All research files live inside `project/`
