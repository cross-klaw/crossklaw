# Setting Up Discord

Connect CrossKlaw to Discord so your AI assistant is available in your server.

## What You Need

- A Discord account
- A Discord server you manage (or create a test one)
- 5 minutes

## Step-by-Step

### 1. Create a Discord Application

1. Go to https://discord.com/developers/applications
2. Click **"New Application"**
3. Name it (e.g. "CrossKlaw") and click **Create**

### 2. Create the Bot

1. In your application, click **"Bot"** on the left sidebar
2. Click **"Reset Token"** — copy the token that appears
3. Scroll down to **"Privileged Gateway Intents"**
4. Toggle ON **"Message Content Intent"** — this lets the bot read messages
5. Click **Save Changes**

**Keep the token secret.** Anyone with it can control your bot.

### 3. Invite the Bot to Your Server

1. Click **"OAuth2"** on the left sidebar
2. Click **"URL Generator"**
3. Under **Scopes**, tick **"bot"**
4. Under **Bot Permissions**, tick:
   - Send Messages
   - Read Message History
5. Copy the generated URL at the bottom
6. Open it in your browser
7. Select your server and click **Authorise**

The bot appears in your server's member list.

### 4. Add the Token to CrossKlaw

Edit `~/.crossklaw/crossklaw.yaml`:

```yaml
channels:
  discord:
    enabled: true
    bot_token: "your-bot-token-here"
```

### 5. Start CrossKlaw

```bash
crossklaw run
```

### 6. Message the Bot

In any channel in your Discord server, mention the bot or send it a DM. CrossKlaw responds.

## Optional: Restrict to Specific Servers

```yaml
channels:
  discord:
    enabled: true
    bot_token: "your-bot-token-here"
    allowed_guilds: [123456789012345678]
```

## Voice Messages

If Whisper is enabled, you can send voice messages in Discord DMs and CrossKlaw will transcribe them.

## Troubleshooting

| Problem | Solution |
|---|---|
| Bot doesn't respond | Check "Message Content Intent" is enabled in developer portal |
| Bot is offline in server | Check `crossklaw run` logs for errors |
| "Invalid token" error | Re-copy the token from Bot settings (Reset Token) |
| Bot responds in wrong channels | Use `allowed_guilds` to restrict |
