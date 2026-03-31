# CrossKlaw Quick Start

## 1. Extract and run setup

**macOS:**
```bash
tar xzf crossklaw-v0.2.0-beta-darwin-arm64.tar.gz
cd crossklaw-v0.2.0-beta-darwin-arm64
xattr -d com.apple.quarantine crossklaw
./crossklaw setup
```

**Linux:**
```bash
tar xzf crossklaw-v0.2.0-beta-linux-amd64.tar.gz
cd crossklaw-v0.2.0-beta-linux-amd64
chmod +x crossklaw
./crossklaw setup
```

**Windows:**
Extract the zip, open PowerShell in the folder, and run:
```powershell
.\crossklaw.exe setup
```

## 2. Setup wizard

The wizard asks 3 things:
1. **LLM Provider** — pick your provider and enter your API key
2. **Channel** — start with "CLI only" (option 1) for the quickest test
3. **Agent identity** — press Enter to accept the default

## 3. Start chatting

```bash
./crossklaw chat
```

That's it. You're talking to CrossKlaw.

## 4. Try the web dashboard

Edit `~/.crossklaw/crossklaw.yaml` and set:
```yaml
channels:
  webchat:
    enabled: true
```

Then run:
```bash
./crossklaw run
```

Open http://localhost:18800/dashboard/ in your browser.

## 5. Health check

```bash
./crossklaw doctor
```

Shows all providers, channels, and system status.

## Need help?

Email: crossklaw@blackstick.co.uk
