# Setting Up WebChat

CrossKlaw includes a built-in browser chat UI. No external services needed.

## What You Need

- CrossKlaw running
- A web browser
- 30 seconds

## Step-by-Step

### 1. Enable WebChat

Edit `~/.crossklaw/crossklaw.yaml`:

```yaml
channels:
  webchat:
    enabled: true
    port: 18801
```

### 2. Start CrossKlaw

```bash
crossklaw run
```

### 3. Open in Browser

Go to http://localhost:18801

That's it. You're chatting.

## Features

- **Real-time chat** via WebSocket — no page refreshes
- **Voice input** — microphone button (requires Whisper enabled)
- **CrossKlaw logo** — welcome screen disappears on first message
- **Auto-reconnect** — reconnects if the connection drops

## Remote Access

By default, WebChat binds to all interfaces (`0.0.0.0`), so it's accessible from other devices on your network at `http://<your-ip>:18801`.

To restrict to localhost only:

```yaml
channels:
  webchat:
    enabled: true
    port: 18801
```

The gateway (`port: 18800`) respects the `gateway.host` setting — set it to `0.0.0.0` for remote access or `127.0.0.1` for local only.

## Dashboard vs WebChat

CrossKlaw has two web interfaces:

| | WebChat | Dashboard |
|---|---|---|
| URL | http://localhost:18801 | http://localhost:18800/dashboard/ |
| Purpose | Simple chat interface | Full management UI |
| Features | Chat only | Chat + channels + skills + memory + security + IoT + settings |
| Voice input | Yes (if Whisper enabled) | Yes (if Whisper enabled) |

Both connect to the same agent. Use WebChat for a clean chat experience, Dashboard for administration.
