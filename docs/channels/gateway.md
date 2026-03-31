# Setting Up the Gateway API

The gateway is CrossKlaw's HTTP and WebSocket API. Use it to integrate CrossKlaw into your own applications, scripts, or automation workflows.

## What You Need

- CrossKlaw running
- A tool to make HTTP requests (curl, PowerShell, Python, etc.)

## Step-by-Step

### 1. Start CrossKlaw

```bash
crossklaw run
```

The gateway starts on port 18800 by default.

### 2. Send a Message (HTTP)

```bash
curl -X POST http://localhost:18800/api/v1/chat \
  -H "Content-Type: application/json" \
  -d '{"content": "hello", "from": "user", "channel": "api"}'
```

Response:

```json
{
  "id": "resp-...",
  "content": "Hey! I'm CrossKlaw...",
  "from": "agent",
  "timestamp": "2026-03-28T10:00:00Z"
}
```

### 3. WebSocket (Streaming)

Connect to `ws://localhost:18800/ws` for real-time bidirectional chat:

```javascript
const ws = new WebSocket('ws://localhost:18800/ws');
ws.onmessage = (e) => console.log(JSON.parse(e.data));
ws.send(JSON.stringify({
  content: "what tools do you have?",
  from: "user",
  channel: "websocket"
}));
```

## Available Endpoints

| Endpoint | Method | Description |
|---|---|---|
| `/api/v1/health` | GET | Health check |
| `/api/v1/chat` | POST | Send message, get response |
| `/ws` | GET | WebSocket chat |
| `/api/v1/scan` | POST | Injection detection scan (requires auth) |
| `/api/v1/sanitise` | POST | Output sanitisation (requires auth) |
| `/dashboard/` | GET | Web dashboard UI |
| `/.well-known/agent-card.json` | GET | A2A Agent Card (if enabled) |
| `/a2a` | POST | A2A JSON-RPC endpoint (if enabled) |
| `/mcp` | POST | MCP server endpoint (if enabled) |

## Authentication

When `auth.enabled: true`, all API requests require a Bearer token:

```bash
# Create a key
crossklaw auth create --name "my-app"

# Use it
curl -H "Authorization: Bearer ck_..." http://localhost:18800/api/v1/chat ...
```

When auth is disabled (default), no authentication is needed — suitable for local use.

## Remote Access

To make the gateway accessible from other machines:

```yaml
gateway:
  host: "0.0.0.0"
  port: 18800
```

**Security warning:** Only expose the gateway to the internet behind a reverse proxy (nginx, Caddy) with TLS. Never expose an unauthenticated gateway to the public internet.
