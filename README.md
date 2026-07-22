I build AI-assistant systems: agent frameworks, MCP servers, and the
guardrails that make them safe to trust with real information.

The repos here are working samples extracted from a private setup I run daily,
rebuilt as deploy-your-own templates. The private versions live on a Gitea
server I self-host on my own hardware and reach over a WireGuard VPN I also
run; nothing in the originals touches a public cloud.

- **mcp-knowledge-connector**: a fail-closed MCP knowledge server. A build-time
  allowlist pipeline with five independent gates decides what a phone-facing
  Claude connector is allowed to know, and a secret tripwire aborts any build
  that would leak. OAuth-gated Cloudflare Worker on the serving side.
- **assistant-os**: a file-based operating system for an AI assistant.
  Session modes, an approval gate with a deliberate asymmetry (new obligations
  wait for a yes; plain facts land immediately), zero-question capture for
  notes dropped from a phone, and a recall index that learns from its own
  misses, all in plain markdown plus hooks, shipped as a worked example with a
  fictional life preloaded. v2 makes it teach itself: a first-run walkthrough
  sets up the private vault, the secrets folder, and the one-word launcher
  with you; a restraint tripwire enforces in code that an outside party's
  rules get reported to the owner, never silently adopted; and a secrets
  guard blocks any command or write that would move a private credential into
  the repo. The private version is the system that actually runs my day.
- **unslop**: a mechanical tripwire for AI writing tells, plus a register-aware
  catalog of which tells are actually worth removing.
- **perch**: a wall-mounted "now showing" display for a
  backyard bird-listening station, with lull-time shows built from the day's
  detections.
- **edgar-quickstart**: a setup guide addressed to your AI agent instead of to
  you. Hand the link to a Claude and it installs the open-source edgartools
  library, asks you for the identity the SEC requires rather than inventing
  one, and already knows the gotchas that only show up in live use.

Everything published here went through a fail-closed leak gate before its
first push, which is why each repo's history starts at the public cut.
