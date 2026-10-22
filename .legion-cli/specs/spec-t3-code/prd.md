# PRD

## Problem
They want to select and use those providers within T3 Code; the existing configuration and integration gaps are being checked against the repository before choosing an implementation.

## Persona
T3 Code users who want additional coding model providers, including API-accessible subscriptions such as Xiaomi MiMo Token Plan.

## Must be true
- Provide reusable OpenAI-compatible API-provider setup with Xiaomi MiMo Token Plan as the first preset; propose the existing MiMo-Code runtime as the first integration, with no separate OpenCode installation requirement and compatibility qualified before implementation.
- Configure a named provider instance with an endpoint or region, secret credential and supported model choices; validate setup and expose the provider in the existing coding-thread model picker.
- Support setup and use from web, desktop and mobile while the destination environment owns configuration, credentials and execution.
- Preserve streamed coding work, tool use, approvals, cancellation, reconnection and saved-thread behavior through the integrated coding-agent runtime.
- Provide edit, disable and removal behavior plus actionable authentication, quota, network and configuration errors.

## Must not change
- Preserve existing providers, authentication, saved threads, model selection, permissions, cancellation, checkpoints and local/remote behavior.
- Keep credentials environment-owned, isolated per provider instance and absent from logs, exports and client projections.
- Preserve the existing Codex managed configuration and externally hosted OpenCode connection behavior.
- Follow AGENTS.md; preserve live T3 userdata and unrelated global provider configuration.
- Use focused verification. Browser verification, live provider calls, implementation and publishing require their separate authorization.

## Out of scope
- Writing a new coding-agent loop or replacing T3 orchestration; integrating the existing MiMo-Code runtime through a provider adapter is in the proposed scope.
- Compatibility with every API or support for additional API protocol families in v0.
- Automatic reconfiguration of independently hosted runtime services; preserve existing external OpenCode connections and their host-owned setup.
- Non-coding audio or video services.
- Automatic fallback from Token Plan billing to pay-as-you-go billing.
- Bundling or forking MiMo-Code source, embedding its desktop UI, or implementing its unrelated memory, workflow and multimedia features in T3.

## Happy path
1) In the destination environment's provider settings, choose the MiMo Token Plan preset or supported custom API setup. 2) Supply the region/base URL, secret API credential and model selection or discovery settings, and receive clear validation feedback. 3) Select the configured provider and model in a new coding thread. 4) Submit a coding request and interact with streamed progress, tools and approvals using the compatible existing harness. 5) Return to the thread or reconnect from another client, then edit, disable or remove the configuration using existing provider lifecycle rules without corrupting saved work.

## Screens
- Existing provider settings/onboarding on web and desktop.
- Equivalent destination-environment provider setup on mobile.
- MiMo preset and custom API setup with secret entry, validation feedback and edit/disable/remove controls.
- Existing shared provider/model picker and coding-thread status/error surfaces.
- Existing agent orchestration catalog and scheduled/delegated execution integrations.
- Concise user setup documentation.
