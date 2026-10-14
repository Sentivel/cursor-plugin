# Sentivel for Cursor

Manage [Sentivel](https://www.sentivel.com) from Cursor. Ask the agent to add monitors for the app you have open, build a status page, link the providers you depend on, or open and update an incident.

## What's included

- **MCP server**: the hosted Sentivel server at `https://mcp.sentivel.com/mcp`. You sign in with your Sentivel account the first time a tool runs. There is no API key to paste.
- **Skills**: `set-up-monitoring` reads your project and proposes monitors, components and a status page. `run-an-incident` checks monitors, upstream providers and recent commits, and drafts status page updates for you to approve.
- **Commands**: `/sentivel-setup` and `/sentivel-status`.
- **Rule**: guidance the agent follows when it uses Sentivel tools, such as asking before it deletes anything or posts a public update.

## Install

Install **Sentivel** from the Cursor Marketplace, then run `/sentivel-setup` in the agent chat.

To use only the MCP server, add this to `.cursor/mcp.json`:

```json
{
  "mcpServers": {
    "sentivel": { "url": "https://mcp.sentivel.com/mcp" }
  }
}
```

## Permissions

The agent can do what your role in the workspace allows. The server checks every call. Member invites, role changes and billing stay in the Sentivel dashboard.

## Docs

- Sentivel docs: https://docs.sentivel.com
- Support: jenson@sentivel.com

## Develop

```bash
node scripts/validate-template.mjs
```

## License

MIT
