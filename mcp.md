---
title: "MCP Server"
description: "Agentbot MCP Server for AI agents"
---

# MCP Server

Connect AI agents to Agentbot using the Model Context Protocol (MCP).

## Overview

The Agentbot MCP server allows AI agents to interact with your deployed agents programmatically.

## Setup

### Installation

```bash
npm install @agentbot/mcp-server
```

### Configuration

```json
{
  "mcpServers": {
    "agentbot": {
      "command": "npx",
      "args": ["-y", "@agentbot/mcp-server"],
      "env": {
        "AGENTBOT_API_KEY": "your-api-key",
        "AGENTBOT_BASE_URL": "https://api.agentbot.raveculture.xyz"
      }
    }
  }
}
```

## Available Tools

### chat

Send a message to an agent and get a response.

```typescript
const response = await agentbot.chat({
  agentId: "agent_123",
  message: "Hello!",
  platform: "telegram"
});
```

### listAgents

List all your deployed agents.

```typescript
const agents = await agentbot.listAgents();
```

### getAgentStatus

Check if an agent is running.

```typescript
const status = await agentbot.getAgentStatus({
  agentId: "agent_123"
});
```

### createAgent

Create a new agent.

```typescript
const agent = await agentbot.createAgent({
  name: "My Agent",
  model: "anthropic/claude-3-opus",
  instructions: "You are a helpful assistant..."
});
```

## Environment Variables

| Variable | Description |
|----------|-------------|
| `AGENTBOT_API_KEY` | Your Agentbot API key |
| `AGENTBOT_BASE_URL` | Base URL (default: https://api.agentbot.raveculture.xyz) |

## Example

```typescript
import { AgentbotClient } from '@agentbot/mcp-server';

const client = new AgentbotClient({
  apiKey: process.env.AGENTBOT_API_KEY
});

// List agents
const agents = await client.listAgents();
console.log(agents);

// Chat with agent
const response = await client.chat({
  agentId: agents[0].id,
  message: "What can you do?"
});
```
