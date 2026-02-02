# tap-ads

Agent skill for advertising campaign planning, media buying, and inventory search using the Tap platform.

## Installation

```bash
npx skills add tap-co/tap-ads
```

## What it does

This skill teaches AI agents how to:

- **Search inventory** - Find advertising platforms across radio, TV, podcasts, and digital
- **Plan campaigns** - Build optimized media plans with budget allocation
- **Analyze economics** - Calculate ROI, CPM efficiency, and reach metrics

## Supported Agents

Works with any agent that supports the [Agent Skills](https://agentskills.io) standard:

- Claude Code
- Cursor
- GitHub Copilot
- Cline
- OpenAI Codex
- Windsurf
- And 15+ more

## Example Prompts

Once installed, try asking your agent:

- "Find radio stations in Chicago reaching women 25-54"
- "Create a $50,000 awareness campaign for a product launch"
- "What podcast advertising options are available in the tech category?"
- "Help me plan a multi-channel campaign with TV and digital"

## MCP Integration

For real-time data access, configure the [Tap MCP server](https://docs.tap.co/mcp):

```json
{
  "mcpServers": {
    "tap": {
      "url": "https://mcp.tap.co",
      "transport": "sse"
    }
  }
}
```

## Links

- [Tap API Documentation](https://docs.tap.co/api)
- [MCP Server](https://docs.tap.co/mcp)
- [Agent Skills Spec](https://agentskills.io)

## License

MIT
