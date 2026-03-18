
description: "Agentbot MCP Server for AI agents"

# MCP Server

Connect AI agents to Agentbot using the Model Context Protocol (MCP).

## Server Configuration

```json
{
  "server": {
    "name": "Agentbot",
    "version": "1.0.0",
    "transport": "http"
  },
  "capabilities": {
    "tools": {
      "search_agentbot": {
        "name": "search_agentbot",
        "description": "Search across the Agentbot knowledge base to find relevant information, code examples, API references, and guides.",
        "inputSchema": {
          "type": "object",
          "properties": {
            "query": {
              "type": "string",
              "description": "A query to search the content with."
            }
          },
          "required": ["query"]
        }
      }
    }
  }
}
```

## Setup

### Claude Desktop

Add to your `claude_desktop_config.json`:

```json
{
  "mcpServers": {
    "agentbot": {
      "command": "npx",
      "args": ["-y", "@agentbot/mcp-server"],
      "env": {
        "AGENTBOT_API_KEY": "your-api-key"
      }
    }
  }
}
```

### Cursor

Add to your `.cursor/mcp.json`:

```json
{
  "mcpServers": {
    "agentbot": {
      "command": "npx",
      "args": ["-y", "@agentbot/mcp-server"],
      "env": {
        "AGENTBOT_API_KEY": "your-api-key"
      }
    }
  }
}
```

## Environment Variables

| Variable | Description |
|----------|-------------|
| `AGENTBOT_API_KEY` | Your Agentbot API key |
| `AGENTBOT_BASE_URL` | Base URL (default: https://api.agentbot.raveculture.xyz) |
