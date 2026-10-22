---
schemaVersion: legion-cli-discuss/v1
decisions:
  - id: D-001
    statement: Provide setup and use on web, desktop and mobile through existing provider surfaces; the selected destination environment owns each named instance, its secrets and execution, including remote connections.
    status: accepted
  - id: D-002
    statement: Keep v0 within T3 provider and orchestration boundaries using a user-installed MiMo-Code CLI on the destination server host; exclude a new agent loop, runtime redistribution, desktop UI embedding, automatic external-server reconfiguration, additional API protocol families, native OAuth setup, non-coding audio/video and automatic billing fallback.
    status: accepted
  - id: D-003
    statement: Use a distinct MiMo-Code provider integration for reusable Chat Completions-compatible API-key setup, with MiMo Token Plan first and no separate OpenCode install; qualify a MiMo release and its transport, permissions, cancellation and session continuity before implementation, and share OpenCode adapter code only where compatibility is demonstrated.
    status: accepted
  - id: D-004
    statement: Use stable provider instance identities with isolated MiMo configuration, credentials and runtime state; preserve unrelated global/project configuration, qualify thread-specific T3 MCP and permission isolation, and never write user-global MiMo-Code or OpenCode configuration.
    status: accepted
  - id: D-005
    statement: Register API credentials as typed secret settings in the destination environment's existing secret store, inject them only into the owning managed runtime, and expose redacted configuration with explicit replace and clear actions.
    status: accepted
  - id: D-006
    statement: Make MiMo Token Plan a regional preset using the account's documented Token Plan endpoint and credential; offer China, Singapore and Europe choices, seed documented coding models, and never change region, account or billing route automatically.
    status: accepted
  - id: D-007
    statement: Use explicit model IDs and release-verified preset metadata for setup, refresh the owning instance catalog after configuration changes, and distinguish saved configuration, runtime/model availability and live coding verification; automatic remote model discovery is optional and background status must not trigger coding or login.
    status: accepted
  - id: D-008
    statement: For MiMo instances, reject disruptive API configuration, credential, disable and remove changes at the server while affected work is active; serialize mutation with work admission, rebuild only the owning instance after work settles or explicit cancellation completes, and preserve saved threads without silent provider reassignment.
    status: accepted
---

Decisions captured before planning.
