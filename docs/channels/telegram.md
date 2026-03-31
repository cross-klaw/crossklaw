# Setting Up Telegram

Connect CrossKlaw to Telegram so you can chat with your AI assistant from your phone or desktop.

## What You Need

- A Telegram account (phone app or desktop app)
- 2 minutes

## Step-by-Step

### 1. Create a bot with BotFather

1. Open Telegram and search for **@BotFather** (look for the verified blue tick)
2. Start a chat and send `/newbot`
3. BotFather asks for a **name** — this is the display name (e.g. "My CrossKlaw")
4. BotFather asks for a **username** — must end in `bot` (e.g. `my_crossklaw_bot`)
5. BotFather replies with your **bot token** — a string like `123456789:ABCdefGHI...`

**Keep this token secret.** Anyone with it can control your bot.

### 2. Add the token to CrossKlaw

Edit `~/.crossklaw/crossklaw.yaml`:

```yaml
channels:
  telegram:
    enabled: true
    bot_token: "123456789:ABCdefGHI..."
```

### 3. Start CrossKlaw

```bash
crossklaw run
```

You should see in the logs:

```
{"level":"info","message":"telegram bot started"}
```

### 4. Message your bot

Open Telegram, search for your bot's username, and send it a message. CrossKlaw responds.

## Optional: Restrict Access

By default, anyone who finds your bot can message it. To restrict access to specific users:

1. Find your Telegram user ID (message @userinfobot in Telegram)
2. Add it to your config:

```yaml
channels:
  telegram:
    enabled: true
    bot_token: "123456789:ABCdefGHI..."
    allowed_users: [123456789]
```

Only users in the list can interact with the bot. Everyone else is ignored.

## Voice Messages

If you have Whisper enabled (`voice.enabled: true`), you can send voice messages to your Telegram bot and CrossKlaw will transcribe and respond to them.

## Troubleshooting

| Problem | Solution |
|---|---|
| Bot doesn't respond | Check `crossklaw doctor` — is the provider connected? |
| "401 Unauthorized" in logs | Bot token is wrong — re-copy from BotFather |
| Bot responds to strangers | Add `allowed_users` to restrict access |
