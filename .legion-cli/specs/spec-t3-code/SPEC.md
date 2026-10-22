---
schemaVersion: legion-cli-spec/v1
id: spec-t3-code
title: T3 Code
problem: Users need to configure and select API-backed coding models in T3 Code, including Xiaomi MiMo Token Plan, while retaining the existing coding-thread lifecycle and destination-environment ownership.
status: frozen
mustBeTrue:
  - Provide reusable Chat Completions-compatible API-key setup through a distinct MiMo-Code provider integration, with MiMo Token Plan as the first preset and a user-installed MiMo-Code CLI on the destination server host. Require no separate OpenCode installation; qualify the MiMo release and integration before implementation.
  - Configure a named provider instance with a stable identity, preset region or custom base URL, secret API credential and explicit supported model IDs. Validate configuration and expose the owning instance and models in the existing coding-thread picker, distinguishing saved settings, runtime/model availability and live coding verification.
  - Support setup and use through existing web and desktop provider surfaces and equivalent mobile setup. The selected destination environment owns configuration, secrets and execution for local and remote clients; enforce authorization there through typed, permission-guarded service calls.
  - Preserve streamed coding work, tools, approvals, permissions, cancellation, checkpoints, reconnection and saved-thread continuity through the qualified MiMo-Code runtime and existing orchestration. Preserve catalog-based command palette, keybinding, agent and scheduled/delegated execution paths where applicable.
  - Support edit, disable, re-enable and removal with actionable authentication, quota, network and configuration feedback. Reject disruptive API configuration, credential, disable and remove changes at the server while affected work is active; serialize mutation with work admission. Rebuild only the owning instance after work settles or explicit cancellation completes, preserving saved threads without silent provider reassignment.
  - Focused fixtures must demonstrate both the MiMo Token Plan preset and a separately configured non-preset Chat Completions endpoint with its own model ID and credential, using the same reusable setup path. Verify independent configuration and secrets for two instances, catalog refresh, streamed tool-capable turns, approval round-trips, completed cancellation and saved-session continuation. Web, desktop and mobile must address the selected destination environment with server-side authorization. Treat saved settings, runtime/model availability and live coding verification as distinct states; later authorized live qualification is required before claiming MiMo interoperability.
mustNotChange:
  - Preserve existing providers, authentication, saved threads, model selection, permissions, cancellation, checkpoints and local/remote behavior.
  - Keep credentials environment-owned, isolated per provider instance and absent from logs, exports and client projections except for redacted presence/state.
  - Preserve existing Codex managed configuration and externally hosted OpenCode connections, including their host-owned setup.
  - Preserve unrelated global/project configuration and live T3 userdata; never write user-global MiMo-Code or OpenCode configuration.
  - Keep provider-specific protocols at the adapter boundary, orchestration pure, transports thin and destination-environment authorization authoritative.
  - Use focused verification. This spec job does not authorize implementation, browser/device verification, live provider calls, publishing or spec approval.
  - "Use a distinct MiMo-Code provider with a user-installed CLI on the destination server host and no separate OpenCode installation. Preserve existing providers, Codex managed authentication, external OpenCode connections, T3 orchestration, permissions, checkpoints and local/remote behavior. Qualify MiMo's own release, headless protocol and per-instance/thread isolation before sharing adapter code. Reuse typed environment-owned secret settings and guarded service/RPC boundaries; never write live T3 userdata or user-global provider configuration. V0 covers API-key Chat Completions setup only: no new agent loop, native OAuth UX, runtime redistribution, desktop embedding or automatic external-server configuration. Keep sandbox policy unchanged, tests focused and live-provider/browser/device qualification separately authorized. Specification review does not authorize implementation, publishing or spec approval."
outOfScope:
  - Building a new coding-agent loop or replacing T3 orchestration.
  - Compatibility with every API, additional API protocol families or native OAuth setup in v0.
  - Automatic reconfiguration of independently hosted runtime services.
  - Non-coding audio/video services and unrelated MiMo-Code memory, workflow or multimedia features.
  - Automatic fallback from Token Plan to pay-as-you-go billing or automatic changes to region, account or billing route.
  - Bundling, redistributing or forking MiMo-Code, embedding its desktop UI, or requiring a separate OpenCode installation.
acceptance:
  - id: AC-P0-01
    statement: Provide reusable Chat Completions-compatible API-key setup through a distinct MiMo-Code provider integration, with MiMo Token Plan as the first preset and a user-installed MiMo-Code CLI on the destination server host. Require no separate OpenCode installation; qualify the MiMo release and integration before implementation.
    kind: behavior
    priority: P0
  - id: AC-P0-02
    statement: Configure a named provider instance with a stable identity, preset region or custom base URL, secret API credential and explicit supported model IDs. Validate configuration and expose the owning instance and models in the existing coding-thread picker, distinguishing saved settings, runtime/model availability and live coding verification.
    kind: behavior
    priority: P0
  - id: AC-P0-03
    statement: Support setup and use through existing web and desktop provider surfaces and equivalent mobile setup. The selected destination environment owns configuration, secrets and execution for local and remote clients; enforce authorization there through typed, permission-guarded service calls.
    kind: behavior
    priority: P0
  - id: AC-P0-04
    statement: Preserve streamed coding work, tools, approvals, permissions, cancellation, checkpoints, reconnection and saved-thread continuity through the qualified MiMo-Code runtime and existing orchestration. Preserve catalog-based command palette, keybinding, agent and scheduled/delegated execution paths where applicable.
    kind: behavior
    priority: P0
  - id: AC-P0-05
    statement: Support edit, disable, re-enable and removal with actionable authentication, quota, network and configuration feedback. Reject disruptive API configuration, credential, disable and remove changes at the server while affected work is active; serialize mutation with work admission. Rebuild only the owning instance after work settles or explicit cancellation completes, preserving saved threads without silent provider reassignment.
    kind: behavior
    priority: P0
  - id: AC-P1-01
    statement: Report invalid or expired API credentials with actionable, redacted feedback and explicit replace and clear actions. Do not expose stored credential values to clients.
    kind: behavior
    priority: P1
  - id: AC-P1-02
    statement: Offer China, Singapore and Europe MiMo Token Plan presets using release-verified regional endpoint and coding-model metadata. Require the account's matching Token Plan endpoint and credential; validate region/endpoint consistency and never change region, account or billing route automatically.
    kind: behavior
    priority: P1
  - id: AC-P1-03
    statement: Use explicit model IDs and the supported Chat Completions route; validate configuration and coding capabilities before advertising availability. Refresh only the owning instance catalog after configuration changes. Automatic remote model discovery is optional, and background status must not start coding or login or imply live coding verification.
    kind: behavior
    priority: P1
  - id: AC-P1-04
    statement: Pin and verify a supported MiMo-Code CLI release independently of OpenCode version numbers. Report a missing or unsupported runtime, failed version probe or unavailable headless service with an actionable destination-host setup path.
    kind: behavior
    priority: P1
  - id: AC-P1-05
    statement: Report rate limits and exhausted Token Plan quota without silently changing models, account, region or billing route, including fallback to pay-as-you-go billing.
    kind: behavior
    priority: P1
  - id: AC-P1-06
    statement: Handle network loss, reconnection and cancellation with truthful run state and redacted errors. A cancellation request alone must not permit a disruptive instance mutation before affected work has settled.
    kind: behavior
    priority: P1
  - id: AC-P1-07
    statement: Use the destination environment's typed secret settings and existing secret store. Isolate configuration, credentials and runtime state by stable instance identity; inject secrets only into the owning managed runtime and keep logs, exports and client projections redacted. Preserve unrelated global/project configuration, never write user-global MiMo-Code or OpenCode configuration, and qualify thread-specific T3 MCP and permission isolation.
    kind: behavior
    priority: P1
  - id: AC-P1-08
    statement: Qualify the pinned MiMo-Code headless transport, readiness, authentication, configuration injection, streamed output and tool-call/reasoning metadata. Reuse OpenCode adapter code only where compatibility is demonstrated; fork ancestry is not evidence.
    kind: behavior
    priority: P1
  - id: AC-P1-09
    statement: Verify permissions, cancellation and saved-session continuity across reconnect, runtime rebuild and restart/resume independently of a simple API text completion. Keep fixture results separate from explicitly authorized live coding qualification; preserve saved threads and report unavailable continuation without silent reassignment.
    kind: behavior
    priority: P1
  - id: AC-CH-01
    statement: Focused fixtures must demonstrate both the MiMo Token Plan preset and a separately configured non-preset Chat Completions endpoint with its own model ID and credential, using the same reusable setup path. Verify independent configuration and secrets for two instances, catalog refresh, streamed tool-capable turns, approval round-trips, completed cancellation and saved-session continuation. Web, desktop and mobile must address the selected destination environment with server-side authorization. Treat saved settings, runtime/model availability and live coding verification as distinct states; later authorized live qualification is required before claiming MiMo interoperability.
    kind: behavior
    priority: P0
personas:
  - T3 Code users who want additional coding model providers, including API-accessible subscriptions such as Xiaomi MiMo Token Plan.
happyPath: 1) In the selected destination environment's existing provider settings or onboarding, create a named MiMo-Code instance and choose MiMo Token Plan or supported custom Chat Completions setup. 2) Choose the Token Plan region or custom base URL, enter the matching secret API credential and explicit model IDs, then save. Show saved configuration separately from runtime/model availability and live coding verification. 3) After prerequisite and availability checks, select that instance and model in the existing coding-thread picker and submit a coding request through the destination environment. 4) Use streamed output, tools, approvals and cancellation through the existing thread lifecycle. Reconnect or return from another authorized client to the same environment and saved thread. 5) Edit, disable, re-enable or remove the instance through existing provider settings. If affected work is active, explain the server rejection and let the user wait or explicitly cancel; apply disruptive changes only after that work settles.
failureCases:
  - Reject invalid endpoint/protocol/model settings with actionable feedback. Missing or unsupported MiMo-Code releases must identify the prerequisite on the destination host; do not infer compatibility from an OpenCode version.
  - Keep authentication failures and expired credentials redacted, with explicit replace and clear actions. Validate the selected Token Plan region and endpoint; do not silently send a credential to a different regional service.
  - Report network failures, rate limits and exhausted Token Plan quota truthfully without automatic region, account or billing changes.
  - Reject disruptive instance changes at the server while affected work is active, including work admitted concurrently with a mutation. A requested cancellation is not proof that the runtime has stopped.
  - Preserve saved thread identity and history when an instance is disabled, removed or cannot resume. Explain unavailability and never silently assign a different provider.
  - Keep one instance's settings, secrets, runtime rebuild and catalog refresh from affecting other instances or unrelated global/project configuration; qualify thread-specific T3 MCP and permissions.
  - Do not report saved settings, model listing or a simple API completion as verified coding integration. Background status must not trigger coding or login; authorized live checks remain a separate evidence gate.
  - Missing or unsupported MiMo-Code versions, invalid credentials or regions, unsupported models, quota exhaustion and network failures must produce actionable redacted status without starting coding or login during background checks. Never change provider, model, account, region or billing route automatically. Reject disruptive settings, credential, disable and removal mutations while work is active, serialize them with work admission, and require cancellation to settle before rebuilding only the owning instance. Preserve saved threads and truthful run state; report unavailable continuation without silent reassignment or credential leakage.
stories: null
wireframesIndex: null
frozenAt: 2026-10-22T01:00:17.476Z
frozenBy: user
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

# T3 Code: MiMo-Code API providers

## Problem

Users need to configure and select API-backed coding models in T3 Code, including Xiaomi MiMo Token Plan, while retaining the existing coding-thread lifecycle and destination-environment ownership.

The recorded decisions select a distinct MiMo-Code provider for v0. MiMo-Code compatibility is still unqualified: this draft does not assert a supported release, endpoint value, model catalog or successful live coding run. The spec remains a draft; accepted decisions are not spec approval.

## Success criteria

- Provide reusable Chat Completions-compatible API-key setup through a distinct MiMo-Code provider integration, with MiMo Token Plan as the first preset and a user-installed MiMo-Code CLI on the destination server host. Require no separate OpenCode installation; qualify the MiMo release and integration before implementation.
- Configure a named provider instance with a stable identity, preset region or custom base URL, secret API credential and explicit supported model IDs. Validate configuration and expose the owning instance and models in the existing coding-thread picker, distinguishing saved settings, runtime/model availability and live coding verification.
- Support setup and use through existing web and desktop provider surfaces and equivalent mobile setup. The selected destination environment owns configuration, secrets and execution for local and remote clients; enforce authorization there through typed, permission-guarded service calls.
- Preserve streamed coding work, tools, approvals, permissions, cancellation, checkpoints, reconnection and saved-thread continuity through the qualified MiMo-Code runtime and existing orchestration. Preserve catalog-based command palette, keybinding, agent and scheduled/delegated execution paths where applicable.
- Support edit, disable, re-enable and removal with actionable authentication, quota, network and configuration feedback. Reject disruptive API configuration, credential, disable and remove changes at the server while affected work is active; serialize mutation with work admission. Rebuild only the owning instance after work settles or explicit cancellation completes, preserving saved threads without silent provider reassignment.

## Must not change

- Preserve existing providers, authentication, saved threads, model selection, permissions, cancellation, checkpoints and local/remote behavior.
- Keep credentials environment-owned, isolated per provider instance and absent from logs, exports and client projections except for redacted presence/state.
- Preserve existing Codex managed configuration and externally hosted OpenCode connections, including their host-owned setup.
- Preserve unrelated global/project configuration and live T3 userdata; never write user-global MiMo-Code or OpenCode configuration.
- Keep provider-specific protocols at the adapter boundary, orchestration pure, transports thin and destination-environment authorization authoritative.
- Use focused verification. This spec job does not authorize implementation, browser/device verification, live provider calls, publishing or spec approval.

## Out of scope

- Building a new coding-agent loop or replacing T3 orchestration.
- Compatibility with every API, additional API protocol families or native OAuth setup in v0.
- Automatic reconfiguration of independently hosted runtime services.
- Non-coding audio/video services and unrelated MiMo-Code memory, workflow or multimedia features.
- Automatic fallback from Token Plan to pay-as-you-go billing or automatic changes to region, account or billing route.
- Bundling, redistributing or forking MiMo-Code, embedding its desktop UI, or requiring a separate OpenCode installation.

## Happy path

1. In the selected destination environment's existing provider settings or onboarding, create a named MiMo-Code instance and choose MiMo Token Plan or supported custom Chat Completions setup.
2. Choose the Token Plan region or custom base URL, enter the matching secret API credential and explicit model IDs, then save. Show saved configuration separately from runtime/model availability and live coding verification.
3. After prerequisite and availability checks, select that instance and model in the existing coding-thread picker and submit a coding request through the destination environment.
4. Use streamed output, tools, approvals and cancellation through the existing thread lifecycle. Reconnect or return from another authorized client to the same environment and saved thread.
5. Edit, disable, re-enable or remove the instance through existing provider settings. If affected work is active, explain the server rejection and let the user wait or explicitly cancel; apply disruptive changes only after that work settles.

## Setup and availability

Use the existing provider-instance settings and secret controls. Keep runtime prerequisites and the supported API type understandable in product-facing setup, and add concise user guidance for setup and recovery during implementation.

| State shown to the user | What it establishes |
| --- | --- |
| Configuration saved | The named instance's validated settings were stored in the selected environment. It does not establish API access or coding capability. |
| Runtime/model available | The supported runtime and configured model have passed the applicable availability checks. Report missing, unsupported or failed prerequisites separately. |
| Live coding verified | An explicitly initiated coding run demonstrated the required behavior for the tested configuration. Saving settings or listing models cannot grant this status. |

These are distinctions the UI must convey, not a prescribed new status schema. Remote model discovery is optional. Background status must not initiate coding or login. Configuration changes refresh the owning catalog and must not leave stale availability or verification claims for the changed configuration.

Disable must have a corresponding re-enable path. Disabled or removed instances leave saved threads visible with an accurate unavailable state; re-enable permits new work only when prerequisites and availability checks pass. Removal must not silently remap those threads.

## Existing surfaces and ownership

| Surface or boundary | Required behavior |
| --- | --- |
| Hosted and locally served web | Extend existing provider onboarding/settings, model picker and thread error/status surfaces. |
| Desktop | Use the same client setup flow; execution and credentials belong to the selected environment, whether bundled or remote. |
| Mobile | Provide equivalent destination-environment setup, secret replacement/clear, lifecycle controls, picker and error feedback. |
| Shared clients and RPC | Use typed, permission-guarded environment commands; authorize mutations at the destination server. Preserve command palette and keybinding entry points where they use the provider catalog. |
| Agent and scheduled/delegated work | Expose the configured instance through existing provider services/catalogs; work admission must obey the same permissions and lifecycle rules. |
| Provider/orchestration boundary | Keep the MiMo-Code integration distinct. Share OpenCode adapter code only after compatibility evidence; preserve existing provider, checkpoint and conversation behavior. |

Local, LAN/Tailscale/SSH and T3 Connect routes retain destination ownership. Different clients and environments must not confuse identically named instances or expose each other's credentials. Runtime support targets the existing Windows, macOS and Linux server environments; initial local evidence is Windows-first and is not cross-platform qualification.

## Failure cases

- Reject invalid endpoint/protocol/model settings with actionable feedback. Missing or unsupported MiMo-Code releases must identify the prerequisite on the destination host; do not infer compatibility from an OpenCode version.
- Keep authentication failures and expired credentials redacted, with explicit replace and clear actions. Validate the selected Token Plan region and endpoint; do not silently send a credential to a different regional service.
- Report network failures, rate limits and exhausted Token Plan quota truthfully without automatic region, account or billing changes.
- Reject disruptive instance changes at the server while affected work is active, including work admitted concurrently with a mutation. A requested cancellation is not proof that the runtime has stopped.
- Preserve saved thread identity and history when an instance is disabled, removed or cannot resume. Explain unavailability and never silently assign a different provider.
- Keep one instance's settings, secrets, runtime rebuild and catalog refresh from affecting other instances or unrelated global/project configuration; qualify thread-specific T3 MCP and permissions.
- Do not report saved settings, model listing or a simple API completion as verified coding integration. Background status must not trigger coding or login; authorized live checks remain a separate evidence gate.

## Acceptance

- AC-P0-01 (P0): Provide reusable Chat Completions-compatible API-key setup through a distinct MiMo-Code provider integration, with MiMo Token Plan as the first preset and a user-installed MiMo-Code CLI on the destination server host. Require no separate OpenCode installation; qualify the MiMo release and integration before implementation.
- AC-P0-02 (P0): Configure a named provider instance with a stable identity, preset region or custom base URL, secret API credential and explicit supported model IDs. Validate configuration and expose the owning instance and models in the existing coding-thread picker, distinguishing saved settings, runtime/model availability and live coding verification.
- AC-P0-03 (P0): Support setup and use through existing web and desktop provider surfaces and equivalent mobile setup. The selected destination environment owns configuration, secrets and execution for local and remote clients; enforce authorization there through typed, permission-guarded service calls.
- AC-P0-04 (P0): Preserve streamed coding work, tools, approvals, permissions, cancellation, checkpoints, reconnection and saved-thread continuity through the qualified MiMo-Code runtime and existing orchestration. Preserve catalog-based command palette, keybinding, agent and scheduled/delegated execution paths where applicable.
- AC-P0-05 (P0): Support edit, disable, re-enable and removal with actionable authentication, quota, network and configuration feedback. Reject disruptive API configuration, credential, disable and remove changes at the server while affected work is active; serialize mutation with work admission. Rebuild only the owning instance after work settles or explicit cancellation completes, preserving saved threads without silent provider reassignment.
- AC-P1-01 (P1): Report invalid or expired API credentials with actionable, redacted feedback and explicit replace and clear actions. Do not expose stored credential values to clients.
- AC-P1-02 (P1): Offer China, Singapore and Europe MiMo Token Plan presets using release-verified regional endpoint and coding-model metadata. Require the account's matching Token Plan endpoint and credential; validate region/endpoint consistency and never change region, account or billing route automatically.
- AC-P1-03 (P1): Use explicit model IDs and the supported Chat Completions route; validate configuration and coding capabilities before advertising availability. Refresh only the owning instance catalog after configuration changes. Automatic remote model discovery is optional, and background status must not start coding or login or imply live coding verification.
- AC-P1-04 (P1): Pin and verify a supported MiMo-Code CLI release independently of OpenCode version numbers. Report a missing or unsupported runtime, failed version probe or unavailable headless service with an actionable destination-host setup path.
- AC-P1-05 (P1): Report rate limits and exhausted Token Plan quota without silently changing models, account, region or billing route, including fallback to pay-as-you-go billing.
- AC-P1-06 (P1): Handle network loss, reconnection and cancellation with truthful run state and redacted errors. A cancellation request alone must not permit a disruptive instance mutation before affected work has settled.
- AC-P1-07 (P1): Use the destination environment's typed secret settings and existing secret store. Isolate configuration, credentials and runtime state by stable instance identity; inject secrets only into the owning managed runtime and keep logs, exports and client projections redacted. Preserve unrelated global/project configuration, never write user-global MiMo-Code or OpenCode configuration, and qualify thread-specific T3 MCP and permission isolation.
- AC-P1-08 (P1): Qualify the pinned MiMo-Code headless transport, readiness, authentication, configuration injection, streamed output and tool-call/reasoning metadata. Reuse OpenCode adapter code only where compatibility is demonstrated; fork ancestry is not evidence.
- AC-P1-09 (P1): Verify permissions, cancellation and saved-session continuity across reconnect, runtime rebuild and restart/resume independently of a simple API text completion. Keep fixture results separate from explicitly authorized live coding qualification; preserve saved threads and report unavailable continuation without silent reassignment.

## Blocking qualification assumptions

All five assumptions from the SessionBrief remain unresolved. They block proceeding as though the runtime integration were qualified; qualification must precede implementation. Do not infer resolution from these requirements, the repository map, fork ancestry or a successful API text completion.

| ID | Required qualification | Acceptance coverage |
| --- | --- | --- |
| ASM-0010 | Qualify MiMo-Code headless protocol, version probing, readiness, authentication, configuration injection, permissions, cancellation and session continuity before implementation. | AC-P0-01, AC-P0-04, AC-P1-04, AC-P1-08, AC-P1-09 |
| ASM-0011 | Pin and verify a supported MiMo-Code release independently of OpenCode version numbers; reject unsupported versions with actionable feedback. | AC-P0-01, AC-P1-04 |
| ASM-0012 | Verify per-instance configuration isolation and preservation of unrelated global provider configuration. | AC-P0-02, AC-P0-05, AC-P1-07 |
| ASM-0013 | Verify secret injection, persistence and redaction using the existing environment-owned secret mechanism. | AC-P1-01, AC-P1-07 |
| ASM-0014 | Verify model/catalog refresh and restart/resume behavior; use the documented MiMo OpenAI-compatible route for v0. | AC-P1-03, AC-P1-08, AC-P1-09 |

The qualification evidence must identify the tested MiMo-Code release and host/platform, demonstrated protocol behavior and limitations. It must cover per-instance and thread-specific T3 MCP/permission isolation, secret persistence/redaction, owning-instance refresh/rebuild and saved-session continuation. A failed capability remains a blocker; this draft authorizes neither a substitute runtime nor weakened permissions.

Actual regional endpoint values, supported model IDs and CLI version pins remain qualification outputs. No credentials, Token Plan entitlement, network access or live integration result are established by this spec.

## Verification boundaries

This run checks document structure, consistency with the recorded intent/decisions, preservation of acceptance identities and allowed-file scope. It does not run application tests, launch a client or call a provider.

Planning must select focused behavioral checks for the MiMo adapter, settings/secrets, instance mutation versus work admission, model/catalog refresh and saved-thread continuity. Cover two named instances, concurrent work admission, cancellation completion and destination authorization. Preserve existing providers, Codex managed configuration and external OpenCode behavior.

Existing regression candidates from the interview, confirmed present in the checkout:

- `vp test run packages/provider-opencode/src/server/driver.test.ts packages/provider-opencode/src/server/status.test.ts packages/provider-opencode/src/server/openCode2Catalog.test.ts`
- `packages/contracts/src/settings.test.ts`, `apps/server/src/auth/ServerSecretStore.test.ts` and `apps/server/src/provider/ProviderInstanceRegistry.test.ts` as affected.
- Existing web provider-settings/model and mobile provider/catalog tests as affected.

These are candidates for planning, not a completed verification record or sufficient proof of MiMo-Code compatibility. Follow the repository's event/deferred/effect-worker synchronization rules for behavioral tests. Do not run the discovery report's repo-wide test command.

Keep local fixture results separate from cross-platform checks, authorized real-client verification and authorized live MiMo coding qualification. The latter must exercise streaming, tools/reasoning metadata, approvals, cancellation and resume; browser/device and paid provider checks require separate authorization. Existing user setup documentation should be updated during implementation without creating a second configuration system.

## Sources and planning references

The current [SessionBrief](../../cache/runs/spec-mvitivzb-3e1024a5/prompt.md) and the accepted decisions below govern this polish. The [intent answers](../../wiki/product/intent-answers.yaml), [intent prose](../../wiki/product/intent.md) and [PRD](prd.md) retain earlier proposal wording, including an OpenCode runtime path; those historical passages do not supersede D-002/D-003. Intent prose is marked untrusted and is source material, not approval authority.

Read for brownfield context: [discovery](../../map/DISCOVERY.md) and [architecture map](../../map/ARCHITECTURE.md). The map is an ownership guide, not runtime or coverage evidence. Relevant existing integration locations for later planning include:

- `packages/provider-opencode/src/settings.ts`, `server/driver.ts` and `server/status.ts` within that package: comparison and regression references, not proof of MiMo compatibility.
- `packages/contracts/src/settings.ts`, `apps/server/src/settingsSecrets.ts` and `apps/server/src/auth/ServerSecretStore.ts`: existing typed settings and environment-owned secret boundaries to reuse and qualify.
- `apps/server/src/provider/ProviderInstanceRegistry.ts`, `ProviderInstanceRegistryMutator.ts` and `apps/server/src/orchestration-v2/ProviderAdapterRegistry.ts`: instance ownership and adapter boundaries.
- `packages/client-runtime`, web provider settings/picker and mobile provider settings/thread selection: shared and client-specific surfaces.

External references supplied by the interview are retained for later qualification: [MiMo-Code repository](https://github.com/XiaomiMiMo/MiMo-Code), [MiMo Token Plan quick access](https://mimo.mi.com/docs/en-US/tokenplan/Token%20Plan/quick-access), [MiMo OpenCode integration guide](https://mimo.mi.com/docs/en-US/tokenplan/integration/opencode) and [MiMo Codex integration guide](https://mimo.mi.com/docs/en-US/tokenplan/integration/codex-configuration). These pages were not refreshed during this polish; they do not establish a currently supported MiMo-Code release, endpoint or transport. The Codex/OpenCode guides are compatibility context, not additional runtime integrations in v0.

## Decisions

- D-001 (accepted): Provide setup and use on web, desktop and mobile through existing provider surfaces; the selected destination environment owns each named instance, its secrets and execution, including remote connections.
- D-002 (accepted): Keep v0 within T3 provider and orchestration boundaries using a user-installed MiMo-Code CLI on the destination server host; exclude a new agent loop, runtime redistribution, desktop UI embedding, automatic external-server reconfiguration, additional API protocol families, native OAuth setup, non-coding audio/video and automatic billing fallback.
- D-003 (accepted): Use a distinct MiMo-Code provider integration for reusable Chat Completions-compatible API-key setup, with MiMo Token Plan first and no separate OpenCode install; qualify a MiMo release and its transport, permissions, cancellation and session continuity before implementation, and share OpenCode adapter code only where compatibility is demonstrated.
- D-004 (accepted): Use stable provider instance identities with isolated MiMo configuration, credentials and runtime state; preserve unrelated global/project configuration, qualify thread-specific T3 MCP and permission isolation, and never write user-global MiMo-Code or OpenCode configuration.
- D-005 (accepted): Register API credentials as typed secret settings in the destination environment's existing secret store, inject them only into the owning managed runtime, and expose redacted configuration with explicit replace and clear actions.
- D-006 (accepted): Make MiMo Token Plan a regional preset using the account's documented Token Plan endpoint and credential; offer China, Singapore and Europe choices, seed documented coding models, and never change region, account or billing route automatically.
- D-007 (accepted): Use explicit model IDs and release-verified preset metadata for setup, refresh the owning instance catalog after configuration changes, and distinguish saved configuration, runtime/model availability and live coding verification; automatic remote model discovery is optional and background status must not trigger coding or login.
- D-008 (accepted): For MiMo instances, reject disruptive API configuration, credential, disable and remove changes at the server while affected work is active; serialize mutation with work admission, rebuild only the owning instance after work settles or explicit cancellation completes, and preserve saved threads without silent provider reassignment.

## Wireframes

Skipped for this run; no wireframes were requested or generated.

<!-- legion-cli:spec-challenge:start -->
## Challenge clarifications

- **mustBeTrue:** Focused fixtures must demonstrate both the MiMo Token Plan preset and a separately configured non-preset Chat Completions endpoint with its own model ID and credential, using the same reusable setup path. Verify independent configuration and secrets for two instances, catalog refresh, streamed tool-capable turns, approval round-trips, completed cancellation and saved-session continuation. Web, desktop and mobile must address the selected destination environment with server-side authorization. Treat saved settings, runtime/model availability and live coding verification as distinct states; later authorized live qualification is required before claiming MiMo interoperability.
- **acceptance AC-CH-01:** Focused fixtures must demonstrate both the MiMo Token Plan preset and a separately configured non-preset Chat Completions endpoint with its own model ID and credential, using the same reusable setup path. Verify independent configuration and secrets for two instances, catalog refresh, streamed tool-capable turns, approval round-trips, completed cancellation and saved-session continuation. Web, desktop and mobile must address the selected destination environment with server-side authorization. Treat saved settings, runtime/model availability and live coding verification as distinct states; later authorized live qualification is required before claiming MiMo interoperability.
- **failureCases:** Missing or unsupported MiMo-Code versions, invalid credentials or regions, unsupported models, quota exhaustion and network failures must produce actionable redacted status without starting coding or login during background checks. Never change provider, model, account, region or billing route automatically. Reject disruptive settings, credential, disable and removal mutations while work is active, serialize them with work admission, and require cancellation to settle before rebuilding only the owning instance. Preserve saved threads and truthful run state; report unavailable continuation without silent reassignment or credential leakage.
- **mustNotChange:** Use a distinct MiMo-Code provider with a user-installed CLI on the destination server host and no separate OpenCode installation. Preserve existing providers, Codex managed authentication, external OpenCode connections, T3 orchestration, permissions, checkpoints and local/remote behavior. Qualify MiMo's own release, headless protocol and per-instance/thread isolation before sharing adapter code. Reuse typed environment-owned secret settings and guarded service/RPC boundaries; never write live T3 userdata or user-global provider configuration. V0 covers API-key Chat Completions setup only: no new agent loop, native OAuth UX, runtime redistribution, desktop embedding or automatic external-server configuration. Keep sandbox policy unchanged, tests focused and live-provider/browser/device qualification separately authorized. Specification review does not authorize implementation, publishing or spec approval.
<!-- legion-cli:spec-challenge:end -->
