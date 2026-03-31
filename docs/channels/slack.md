# Setting Up Slack

Connect CrossKlaw to Slack so your AI assistant is available in your workspace.

## What You Need

- A Slack workspace you can install apps to
- 5 minutes

## Step-by-Step

### 1. Create a Slack App

1. Go to https://api.slack.com/apps
2. Click **"Create New App"**
3. Choose **"From scratch"**
4. Name it (e.g. "CrossKlaw") and pick your workspace
5. Click **Create App**

### 2. Set Permissions

1. Click **"OAuth & Permissions"** on the left
2. Scroll to **"Scopes" > "Bot Token Scopes"**
3. Add these scopes:
   - `chat:write` — lets the bot send messages
   - `app_mentions:read` — lets the bot see when it's mentioned
   - `im:history` — lets the bot read DMs
   - `im:read` — lets the bot see DM channels

### 3. Enable Socket Mode

1. Click **"Socket Mode"** on the left
2. Toggle it **ON**
3. It asks you to create an **App-Level Token** — name it anything (e.g. "crossklaw-socket")
4. Add the scope `connections:write`
5. Click **Generate** — copy the token (starts with `xapp-`)

### 4. Enable Events

1. Click **"Event Subscriptions"** on the left
2. Toggle **ON**
3. Under "Subscribe to bot events", add:
   - `message.im` — DM messages
   - `app_mention` — @mentions in channels
4. Click **Save Changes**

### 5. Install to Workspace

1. Click **"Install App"** on the left
2. Click **"Install to Workspace"**
3. Authorise the app
4. Copy the **Bot User OAuth Token** (starts with `xoxb-`)

### 6. Add Tokens to CrossKlaw

Edit `~/.crossklaw/crossklaw.yaml`:

```yaml
channels:
  slack:
    enabled: true
    bot_token: "xoxb-your-bot-token"
    app_token: "xapp-your-app-token"
```

### 7. Start CrossKlaw

```bash
crossklaw run
```

### 8. Message the Bot

DM the bot in Slack or @mention it in a channel. CrossKlaw responds.

## Voice Messages

If Whisper is enabled, Slack voice messages (huddle clips) will be transcribed automatically.

## Troubleshooting

| Problem | Solution |
|---|---|
| Bot doesn't respond to DMs | Check `im:history` and `im:read` scopes are added |
| Bot doesn't respond to @mentions | Check `app_mentions:read` scope and `app_mention` event subscription |
| "invalid_auth" error | Check both tokens are correct — bot token (xoxb) AND app token (xapp) |
| Socket Mode not connecting | Check Socket Mode is enabled and app token has `connections:write` scope |
