---
schemaVersion: legion-cli-context/v1
standingInstructions: |
  Follow AGENTS.md and preserve existing work. Keep web, desktop, mobile, providers, contracts, and local/remote connection modes in scope when relevant. Never write to the live T3 userdata directory or bake localhost origins into client builds. Plan focused verification before editing; do not run repo-wide checks. Ask before browser or computer-use verification. Do not commit, push, create PRs, or perform destructive actions without explicit authorization.
  Constraint or design input: Follow AGENTS.md, docs/internals/overview.md, docs/internals/providers.md, docs/internals/remote.md and docs/internals/effect-services.md. Source review identifies packages/provider-opencode/src/settings.ts and server/driver.ts/status.ts as the smallest existing harness path; current customModels only enrich the picker and do not configure an API backend. Reuse existing secret settings (packages/contracts/src/settings.ts; apps/server/src/settingsSecrets.ts) and provider-instance ownership. Proposed v0 supports OpenAI-compatible API services via T3-managed OpenCode, isolated per instance, with MiMo Token Plan regional presets and current documented coding models. Preserve externally hosted OpenCode connections but require configuration on their host; do not imply local environment variables reconfigure an external server. Existing Codex managed configuration remains unchanged. Product-facing setup should make the runtime prerequisite and supported API type clear without exposing internal implementation details.
platforms:
  - phone
  - desktop
---

T3 Code is a multi-surface client for environment-owned coding agents.

Start with [AGENTS.md](../AGENTS.md), the [architecture overview](../docs/internals/overview.md),
and the [repository map](map/ARCHITECTURE.md). Shared client behavior lives in
`packages/client-runtime`; wire contracts live in `packages/contracts`; the
server owns provider processes, workspace operations, and durable orchestration.

This onboarding establishes brownfield audit context. No implementation spec,
plan, or delivery approval has been created.
