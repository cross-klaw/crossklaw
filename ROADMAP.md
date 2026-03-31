# CrossKlaw Roadmap

## v0.2.0-beta (current)
- [x] 14 channels (CLI, TUI, Telegram, Discord, Slack, WhatsApp, Signal, Matrix, Email, WebChat, MQTT, Webhook, Dashboard, Teams)
- [x] 11 LLM providers with intelligent routing and failover
- [x] A2A protocol server (v1.0) with security hardening
- [x] MCP client and server
- [x] WASM skill sandboxing (wazero)
- [x] Multi-agent delegation with per-role tool restrictions
- [x] IoT bridge (MQTT, Home Assistant, GPIO, time-series, anomaly detection)
- [x] Config encryption (AES-256-GCM, ENC: prefix)
- [x] Voice input (Whisper) on dashboard, webchat, and 4 messaging channels
- [x] 19 bundled skills, 10 sector templates
- [x] Logo in dashboard and webchat
- [x] Interactive setup wizard
- [x] Plaintext API key warning

## v0.2.0 (release)
- [ ] Embed logo in TUI startup
- [ ] GoReleaser for multi-platform binaries
- [ ] README that sells (hero image, feature grid, quickstart, comparison table)
- [ ] LICENSE file (free personal, commercial requires license)
- [ ] CHANGELOG for v0.2.0

## v0.3.0 (planned)
- [ ] Interactive channel management (`crossklaw channel enable telegram` prompts for token)
- [ ] Voice output / text-to-speech (browser speechSynthesis + optional API TTS)
- [ ] OpenTelemetry trace export (spans per tool call, LLM call, skill invocation)
- [ ] Skill registry with `crossklaw skill install` (signed, community skills)
- [ ] OpenClaw skill compatibility (import OpenClaw SKILL.md format)
- [ ] Built-in eval/regression harness (`crossklaw eval`)
- [ ] Human-in-the-loop approval workflows (pause on high-stakes actions)
- [ ] Provider cost/latency dashboard (makes intelligent routing visible)

## v0.4.0 (planned)
- [ ] More channels: Google Chat, Mattermost, Rocket.Chat, LINE, SMS/Twilio, IRC
- [ ] More LLM providers: AWS Bedrock, Vertex AI, Cohere
- [ ] Desktop app with system tray (cross-platform)
- [ ] Signed Agent Cards (JWS/RFC 7515) for A2A
- [ ] A2A client mode (CrossKlaw delegates to remote agents)
- [ ] A2A streaming (SSE)

## Future
- [ ] Open core: public source for core engine, proprietary sector templates and advanced features
- [ ] Plugin marketplace with WASM isolation
- [ ] Multi-tenant mode (multiple users, API key management)
- [ ] SSO/LDAP enterprise identity
- [ ] Checkpoint and replay for multi-agent workflows
- [ ] Formal verification of security components
