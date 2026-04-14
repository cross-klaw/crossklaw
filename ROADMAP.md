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

## v0.2.0 (release — shipped as v0.2.0-beta)
- [x] LICENSE file (free personal, commercial requires license)
- [x] CHANGELOG for v0.2.0
- [x] README (live, feature grid, quickstart)
- [ ] Embed logo in TUI startup (nice-to-have)
- [ ] GoReleaser for multi-platform binaries (nice-to-have — manual build works)
- [ ] README polish: feature comparison table, better hero section

## v0.3.0 (planned)
- [x] Interactive channel management (`crossklaw channel list/enable/disable` with guided prompts)
- [x] Voice output / text-to-speech (browser speechSynthesis + optional API TTS)
- [x] OpenTelemetry trace export (spans per tool call, LLM call, skill invocation)
- [x] Skill registry with `crossklaw skill install` (signed, community skills)
- [x] OpenClaw skill compatibility (import OpenClaw SKILL.md format)
- [x] Built-in eval/regression harness (`crossklaw eval`)
- [x] Human-in-the-loop approval workflows (pause on high-stakes actions)
- [x] Provider cost/latency dashboard (makes intelligent routing visible)

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
