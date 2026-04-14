# Changelog

## v0.3.0 — 2026-04-11

### Highlights
- **Interactive channel management** — `crossklaw channel list/enable/disable` with guided setup prompts per channel
- **OpenTelemetry tracing** — native OTLP export with spans for every LLM call, tool execution, and skill invocation; compatible with Jaeger, Grafana Tempo, Datadog, Honeycomb, AWS X-Ray
- **Human-in-the-loop approval** — configurable high-stake tools pause and ask the user for confirmation via their messaging channel before executing; timeout with auto-deny
- **Provider cost/latency dashboard** — per-provider metrics with avg/p95 latency, token counts, cost estimates, success rates, and fallback tracking
- **Voice output / TTS** — browser speechSynthesis (free, zero config) + optional OpenAI API TTS for natural-sounding voice; speaker toggle in dashboard
- **Eval/regression harness** — `crossklaw eval suite.yaml` runs test cases against the agent with keyword, regex, and length assertions
- **OpenClaw skill compatibility** — auto-detects and adapts OpenClaw SKILL.md format with 20+ tool name mappings
- **Skill registry** — `crossklaw skill install owner/repo` installs skills from GitHub with content security scanning

### New CLI Commands
- `crossklaw channel list` — show all channels with enabled/disabled status
- `crossklaw channel enable <name>` — interactive guided setup for a channel
- `crossklaw channel disable <name>` — disable a channel and save config
- `crossklaw eval <suite.yaml>` — run eval/regression test suite

### New Config Sections
- `approval` — human-in-the-loop tool approval (enabled, high_stake_tools, timeout_seconds)
- `telemetry` — OpenTelemetry tracing (enabled, otlp_endpoint, service_name)
- `voice.tts` — text-to-speech output (enabled, provider, api_key, model, voice)

### New Dashboard Endpoints
- `GET /api/provider-metrics` — per-provider cost/latency aggregation
- `GET /api/traces` — recent OpenTelemetry span history
- `POST /api/voice/synthesize` — text-to-speech audio generation

### Security
- Human-in-the-loop approval works across all messaging channels (Telegram, Discord, Slack, Matrix, Email, Teams)
- Approval responses intercepted before reaching the agent
- High-stake tool list is configurable per deployment

## v0.2.0-beta — 2026-03-27

### Highlights
- **14 communication channels** — CLI, TUI, Telegram, Discord, Slack, WhatsApp, Signal, Matrix, Email, WebChat, MQTT, Webhook, Microsoft Teams, Dashboard
- **11 LLM providers** — Anthropic, OpenAI, Gemini, DeepSeek, Groq, OpenRouter, Ollama, Mistral, Azure OpenAI, Cerebras, Together AI
- **A2A protocol server** — Google Agent-to-Agent v1.0 with full security hardening
- **MCP client + server** — Use external tools AND expose CrossKlaw as MCP tools
- **Intelligent model routing** — Routes simple queries to fast/cheap models, complex to powerful
- **WASM skill sandboxing** — Secure code execution via wazero (pure Go, zero CGO)
- **Interactive setup wizard** — `crossklaw setup` gets you running in 2 minutes

### Security
- Injection detection on every channel, A2A, and MCP endpoint
- Ed25519 skill signing and verification
- AES-256-GCM config encryption with Argon2id key derivation
- Per-IP rate limiting on webhook and A2A endpoints
- Output sanitisation on all responses
- Full audit logging with parent traceability for delegated sub-agents
- Per-role tool restrictions for multi-agent delegation
- WASM sandbox: memory limits, execution timeouts, no filesystem/network access
- Pen tested: 22 automated security checks across 9 attack categories (run `bash tests/pentest.sh`)
- Plaintext API key warning at startup and after setup

### IoT
- MQTT bridge with pub/sub
- Home Assistant integration
- GPIO pin control with allowlisting
- Time-series storage with automatic rollups
- EWMA anomaly detection with configurable alerts

### Agent
- Multi-agent delegation with specialist personas
- 19 bundled skills
- 10 sector templates (healthcare, manufacturing, agriculture, energy, etc.)
- Document RAG pipeline with vector search
- Persistent memory with cross-session recall
- Voice transcription (Whisper) on 6 channels
- Voice input microphone button in dashboard and webchat (ghosted with setup instructions when disabled)
- Scheduler with cron jobs

### Developer Experience
- Single binary, zero dependencies (46MB)
- Runs offline with Ollama on a Raspberry Pi
- `crossklaw setup` — interactive first-run wizard
- `crossklaw doctor` — diagnostic health checks for all providers and channels
- `crossklaw config encrypt` — encrypt API keys in config file
- Active model visible in TUI status bar
- Step-by-step channel setup instructions in example config
- CrossKlaw logo embedded in dashboard and webchat
- Welcome screen with logo in dashboard and webchat chat views
- Comprehensive brochure updated with all v0.2.0-beta features

## v0.1.0 — 2026-02-23

- Initial internal release
