# MiMo-Code provider plan

Spec: `spec-t3-code`. Planning only; proposed risk-first strategy with balanced granularity. The active frozen spec and SessionBrief require qualification before implementation. No human strategy selection or plan approval is invented.

## Gate and task board

ASM-0010 through ASM-0014 are unresolved. TSK-0002 is the sole dependency root for qualification. All task statuses remain engine-owned; open blocking assumptions currently prevent automatic readiness. Plan approval and qualification remain separate from implementation and live paid calls. All implementation depends transitively on its successful evidence gate. A failed/unavailable capability leaves dependent tasks blocked. Exact release, regional endpoints/model IDs and protocol/isolation decisions are qualification outputs.

| Task | Outcome | Initial status | Blocked by |
| --- | --- | --- | --- |
| [TSK-0002](../tasks/TSK-0002.md) | Qualify the MiMo release and isolated headless protocol before implementation | todo (qualification root; assumptions open) | None |
| [TSK-0001](../tasks/TSK-0001.md) | Register the mobile setup interaction test in the React/jsdom project | todo | TSK-0002 |
| [TSK-0003](../tasks/TSK-0003.md) | Define reusable MiMo instance settings, presets and destination permission guards | todo | TSK-0002 |
| [TSK-0004](../tasks/TSK-0004.md) | Implement the qualified MiMo runtime adapter and independent instance catalog | todo | TSK-0003 |
| [TSK-0005](../tasks/TSK-0005.md) | Enforce atomic instance mutation, secret ownership and work settlement on the server | todo | TSK-0004 |
| [TSK-0006](../tasks/TSK-0006.md) | Expose MiMo setup and truthful availability through web and desktop provider surfaces | todo | TSK-0005 |
| [TSK-0007](../tasks/TSK-0007.md) | Provide equivalent MiMo instance setup and lifecycle controls on mobile | todo | TSK-0005, TSK-0001 |
| [TSK-0008](../tasks/TSK-0008.md) | Verify integrated coding lifecycle and document destination-host setup and recovery | todo | TSK-0006, TSK-0007 |

TSK-0006 and TSK-0007 can proceed in parallel after the complete server boundary; mobile also depends on TSK-0001 test-project registration. All other ordering follows explicit blockedBy dependencies. Whole-file ownership is exclusive: TSK-0001 owns apps/mobile/vite.config.ts; TSK-0003 owns all package manifests/lockfile, TSK-0004 provider runtime files, TSK-0005 the inseparable server/settings/admission files, TSK-0006 web, TSK-0007 mobile, TSK-0008 the new integrated test/docs/evidence. Dependencies never permit shared ownership. Do not widen a task; additional work requires the run-cache extra.json path and an approved amendment/new increment.

Independent review identified apps/mobile/vite.config.ts as required to register the proposed screen interaction test in its explicit React test allowlist. TSK-0001 now exclusively owns that configuration and is an explicit dependency of TSK-0007. C-MOBILE-HARNESS checks the configuration diff; C-MOBILE runs the actual mounted screen and Settings-route interaction once after registration. The existing Settings route logic test alone does not prove navigation. The review finding is incorporated into the draft plan; qualification assumptions and execution authorization remain open.

Read [design.md](spec-t3-code/design.md) before task execution. There is no adapter frontmatter override: product use of MiMo-Code does not select Legion's coding CLI. Product tasks correspond to frozen P0 outcomes; the bounded mobile harness follow-up retains its engine-assigned P2 priority. Task status changes and readiness promotions belong to the engine.

## Observable outcomes

- **OUT-01**: A supported isolated MiMo runtime has demonstrated prerequisites before product work. Tasks: TSK-0002. Acceptance: AC-P0-01, AC-P1-04, AC-P1-08.
- **OUT-02**: Users configure independent preset/custom instances with destination-owned secrets and guarded setup. Tasks: TSK-0001, TSK-0003, TSK-0006, TSK-0007. Acceptance: AC-P0-02, AC-P0-03, AC-P1-01, AC-P1-02, AC-P1-03, AC-P1-07.
- **OUT-03**: Coding, cancellation and instance changes preserve identity, permissions and settled work. Tasks: TSK-0004, TSK-0005. Acceptance: AC-P0-04, AC-P0-05, AC-P1-05, AC-P1-06, AC-P1-09.
- **OUT-04**: Integrated evidence and operator guidance distinguish fixtures from real interoperability. Tasks: TSK-0008. Acceptance: AC-CH-01.

## Planned automated checks

Run from the repository root. These are future checks, not results from this planning run. Test paths for the new MiMo package, lifecycle service, mobile setup screen and integrated scenario are proposed files owned by their task; other named test paths are present. Q-CLI is a proposed qualification harness and must execute the actual pinned CLI against isolated loopback fixtures, not just inspect files. No `vp check`, recursive test/typecheck, `npx tsc`, browser, live provider or device command is part of this automated set.

- **C-MOBILE-HARNESS** (TSK-0001): `git diff --check -- apps/mobile/vite.config.ts` (configuration check; meaningful interaction coverage runs once in C-MOBILE).
- **Q-CLI** (TSK-0002): `node --test packages/provider-mimo/qualification/cli.test.mjs`
- **C-CONFIG** (TSK-0003): `vp test run packages/provider-mimo/src/settings.test.ts packages/provider-mimo/src/presets.test.ts packages/contracts/src/settings.test.ts packages/client-runtime/src/state/commandPermissions.test.ts`
- **C-RUNTIME** (TSK-0004): `vp test run packages/provider-mimo/src/server/versionProbe.test.ts packages/provider-mimo/src/server/status.test.ts packages/provider-mimo/src/server/driver.test.ts packages/provider-mimo/src/server/MiMoRuntime.test.ts packages/provider-mimo/src/server/adapter.test.ts packages/provider-mimo/src/server/catalog.test.ts`
- **C-SETTINGS** (TSK-0005): `vp test run apps/server/src/serverSettings.test.ts apps/server/src/auth/ServerSecretStore.test.ts apps/server/src/auth/RpcAuthorization.test.ts`
- **C-LIFECYCLE** (TSK-0005): `vp test run apps/server/src/provider/ProviderInstanceLifecycle.test.ts apps/server/src/provider/ProviderInstanceRegistry.test.ts apps/server/src/provider/ProviderInstanceRegistryHydration.test.ts apps/server/src/provider/ProviderRegistry.test.ts`
- **C-ORCHESTRATION** (TSK-0005): `vp test run apps/server/src/orchestration-v2/ProviderSessionManager.test.ts apps/server/src/orchestration-v2/ProviderTurnStartService.test.ts apps/server/src/orchestration-v2/ProviderTurnControlService.test.ts apps/server/src/orchestration-v2/ProviderAdapterRegistry.test.ts apps/server/src/orchestration-v2/ProviderContinuationService.test.ts apps/server/src/orchestration-v2/ProviderRuntimeRecoveryService.test.ts apps/server/src/orchestration-v2/RunExecutionService.test.ts`
- **C-WEB** (TSK-0006): `vp test run apps/web/src/components/settings/AddProviderInstanceDialog.test.ts apps/web/src/components/settings/ProviderInstanceCard.test.ts apps/web/src/components/settings/ProviderSettingsForm.test.ts apps/web/src/components/settings/providerStatus.test.ts apps/web/src/providerInstances.test.ts apps/web/src/providerModels.test.ts apps/web/src/modelSelection.test.ts apps/web/src/onboarding/providerReadiness.logic.test.ts`
- **C-MOBILE** (TSK-0007): `vp test run apps/mobile/src/features/settings/SettingsProviderInstancesRouteScreen.test.tsx apps/mobile/src/features/settings/SettingsRouteScreen.logic.test.ts apps/mobile/src/features/settings/settings-scoped-server.test.ts apps/mobile/src/features/threads/provider-catalog-refresh.test.ts apps/mobile/src/features/threads/thread-provider-instance.test.ts apps/mobile/src/state/thread-provider-switching.test.ts`
- **C-INTEGRATION** (TSK-0008): `vp test run apps/server/src/orchestration-v2/MiMoOrchestratorV2.integration.test.ts`
- **C-PRESERVE** (TSK-0008): `vp test run packages/provider-opencode/src/server/driver.test.ts packages/provider-opencode/src/server/status.test.ts packages/provider-opencode/src/server/openCode2Catalog.test.ts apps/server/src/ws.test.ts`
- **C-TYPES** (TSK-0008): `vp run --filter @t3tools/contracts --filter @t3tools/provider-mimo --filter @t3tools/client-runtime --filter t3 --filter @t3tools/web --filter @t3tools/mobile --filter @t3tools/desktop typecheck`

Each command identity has one owner and one scheduled execution. Acceptance mappings reference checks without scheduling duplicates. Run each once; after a supported fix rerun only affected failures. Two different failed repair attempts require escalation with evidence. No routine suite reruns. If a later authorized push is requested, `vp run check:changed` remains the repository's separate pre-push requirement. No push, install or application test is authorized by this plan-writing job.

## Acceptance coverage

All 15 frozen criteria are covered below. Expected observations are specified in the owning tasks and external procedures. Coverage is a plan, not an acceptance pass. C-TYPES is cross-cutting static validation and cannot substitute for any behavior criterion.

| Criterion | Owning tasks | Evidence methods |
| --- | --- | --- |
| AC-P0-01 | TSK-0002, TSK-0003, TSK-0004, TSK-0006, TSK-0007, TSK-0008 | Q-CLI, C-CONFIG, C-RUNTIME, C-INTEGRATION, M-LIVE |
| AC-P0-02 | TSK-0003, TSK-0004, TSK-0005, TSK-0006, TSK-0007, TSK-0008 | C-CONFIG, C-RUNTIME, C-WEB, C-MOBILE, C-INTEGRATION, M-CLIENTS |
| AC-P0-03 | TSK-0001, TSK-0003, TSK-0005, TSK-0006, TSK-0007, TSK-0008 | C-CONFIG, C-SETTINGS, C-WEB, C-MOBILE, C-PRESERVE, M-CLIENTS |
| AC-P0-04 | TSK-0002, TSK-0004, TSK-0005, TSK-0008 | Q-CLI, C-RUNTIME, C-ORCHESTRATION, C-INTEGRATION, C-PRESERVE, M-CLIENTS, M-LIVE |
| AC-P0-05 | TSK-0005, TSK-0006, TSK-0007, TSK-0008 | C-SETTINGS, C-LIFECYCLE, C-ORCHESTRATION, C-WEB, C-MOBILE, C-INTEGRATION, M-REVIEW, M-CLIENTS |
| AC-P1-01 | TSK-0003, TSK-0004, TSK-0005, TSK-0006, TSK-0007, TSK-0008 | C-CONFIG, C-SETTINGS, C-RUNTIME, C-WEB, C-MOBILE, C-INTEGRATION, M-CLIENTS |
| AC-P1-02 | TSK-0002, TSK-0003, TSK-0006, TSK-0007, TSK-0008 | Q-CLI, C-CONFIG, C-WEB, C-MOBILE, M-LIVE |
| AC-P1-03 | TSK-0003, TSK-0004, TSK-0005, TSK-0006, TSK-0007, TSK-0008 | C-CONFIG, C-RUNTIME, C-LIFECYCLE, C-WEB, C-MOBILE, C-INTEGRATION |
| AC-P1-04 | TSK-0002, TSK-0004, TSK-0006, TSK-0007, TSK-0008 | Q-CLI, C-RUNTIME, C-WEB, C-MOBILE, M-PLATFORMS |
| AC-P1-05 | TSK-0004, TSK-0006, TSK-0007, TSK-0008 | C-RUNTIME, C-WEB, C-MOBILE, C-INTEGRATION, M-LIVE |
| AC-P1-06 | TSK-0004, TSK-0005, TSK-0006, TSK-0007, TSK-0008 | C-RUNTIME, C-LIFECYCLE, C-ORCHESTRATION, C-WEB, C-MOBILE, C-INTEGRATION, M-LIVE |
| AC-P1-07 | TSK-0002, TSK-0003, TSK-0004, TSK-0005, TSK-0008 | Q-CLI, C-CONFIG, C-SETTINGS, C-LIFECYCLE, C-RUNTIME, C-INTEGRATION, M-REVIEW, M-PLATFORMS |
| AC-P1-08 | TSK-0002, TSK-0004, TSK-0008 | Q-CLI, C-RUNTIME, C-INTEGRATION, M-LIVE, M-PLATFORMS |
| AC-P1-09 | TSK-0002, TSK-0004, TSK-0005, TSK-0008 | Q-CLI, C-RUNTIME, C-LIFECYCLE, C-ORCHESTRATION, C-INTEGRATION, M-LIVE, M-PLATFORMS |
| AC-CH-01 | TSK-0001, TSK-0002, TSK-0003, TSK-0004, TSK-0005, TSK-0006, TSK-0007, TSK-0008 | Q-CLI, C-CONFIG, C-RUNTIME, C-SETTINGS, C-LIFECYCLE, C-ORCHESTRATION, C-WEB, C-MOBILE, C-INTEGRATION, M-CLIENTS, M-LIVE |

## Manual and external evidence still pending

### M-CLIENTS (manual; owner TSK-0008)

After explicit browser/device authorization, the primary integrator uses isolated seeded T3 state and one integrated pass: locally served web, hosted web to remote destination, desktop to bundled and remote destination, and iOS/Android. Create preset/custom instances, replace/clear, edit/disable/re-enable/remove; verify denied grants, selected environment, picker/Settings/onboarding/command palette/keybinding/scheduled selection, busy rejection, reconnect and preserved unavailable saved threads. Capture before/after UI evidence. Do not use live userdata or consume user pairing links.

Expected observation: Every applicable entrypoint uses the same destination identity and permission behavior, only redacted presence reaches clients, and saved/available/live-verified states remain distinct. Native and desktop observations recorded individually.

Status: pending. Record redacted digest-bound repository evidence or an approved HTTPS/report:/external:/urn: reference later; planning does not grant authority or authenticity to a report.

### M-LIVE (external; owner TSK-0008)

After explicit account/network/billing authorization, on the exact qualified CLI release run a small tool-capable coding task against the matching Token Plan account/region and a separately authorized non-preset Chat Completions endpoint. Observe streaming/reasoning, approval allow/deny, workspace tool result, completed checkpoint, cancel request then actual settlement, disconnect/reconnect and saved-session resume after runtime/server restart. Change one idle instance and verify the other remains usable. Stop on auth/quota failure without changing account, region, model or billing route. Record tested release/config digest and redacted evidence reference, never the key.

Expected observation: Real coding lifecycle and independent reusable custom setup demonstrated for the explicitly tested configurations. Untested regions/accounts/models remain pending; a simple API completion is insufficient.

Status: pending. Record redacted digest-bound repository evidence or an approved HTTPS/report:/external:/urn: reference later; planning does not grant authority or authenticity to a report.

### M-PLATFORMS (external; owner TSK-0008)

On separate authorized Windows, macOS and Linux destination hosts with the pinned user-installed release, repeat the isolated Q-CLI protocol/isolation suite and focused integrated runtime scenario once per supported platform. Record executable/version/readiness, process teardown, isolated config/secret permissions, continuation/restart and local versus remote routes. Each platform uses its own disposable state; no global configuration writes.

Expected observation: Evidence identifies exact OS/architecture/runtime and proves platform-dependent launch/isolation/cancellation/resume. Windows-only evidence never closes macOS/Linux support.

Status: pending. Record redacted digest-bound repository evidence or an approved HTTPS/report:/external:/urn: reference later; planning does not grant authority or authenticity to a report.

### M-REVIEW (manual; owner TSK-0008)

An independent reviewer checks the final TSK-0005 admission/settings/hydration design and integrated diff against D-004/D-005/D-008, using the deterministic race and recovery evidence. Trace generic patches, queued/delegated/scheduled and background work, cancellation settlement, lock order, restart reservations, secret rollback/redaction, old-provider compatibility and failure recovery.

Expected observation: No unresolved consequential review findings; exact reviewed revision and evidence are recorded. A review is not runtime/live qualification.

Status: pending. Record redacted digest-bound repository evidence or an approved HTTPS/report:/external:/urn: reference later; planning does not grant authority or authenticity to a report.

## Surface and preservation checklist

| Boundary | Planned coverage |
| --- | --- |
| Settings/onboarding/chat picker/project defaults | TSK-0003/0006 shared schema/catalog; M-CLIENTS verifies interactions. |
| Command palette/keybindings/scheduled model selection | TSK-0006 audits shared catalog consumers; TSK-0008 verifies reachability and service admission. No unneeded entrypoint rewrite. |
| Web/local and hosted, desktop | Same web provider flow; destination-owned bundled or remote server. TSK-0006 plus M-CLIENTS. |
| Mobile/iOS/Android | New instance setup route using existing shared commands; TSK-0007 plus M-CLIENTS. |
| MCP/agents/scheduled/delegated work | Existing services, common work admission, thread-specific MCP/permission isolation; TSK-0002/0004/0005/0008. |
| Providers | Distinct MiMo driver; preserve all current providers, Codex managed configuration and externally hosted OpenCode. C-PRESERVE and independent review. |
| Contracts and mixed versions | Reuse extensible driver/instance and existing typed settings RPC; scope guards are additive and payload-sensitive. No implicit history migration. |
| Reverse states | Explicit clear, disable/re-enable, removal/unavailable saved threads, cancel/settled distinction; TSK-0005/0006/0007. |
| Local/remote/relay/tunnel, multiple environments | Existing routing; two same-named destination instances remain distinct. C-CONFIG/C-SETTINGS/C-PRESERVE and M-CLIENTS. |
| Docs/install/recovery | Existing user install guide plus focused MiMo guide; TSK-0008. No additional internal feature catalog. |

## Source and authority record

- `.legion-cli/specs/spec-t3-code/SPEC.md` SHA256 `c8a4003a40e6e2c2b71a990e68c3fc952d160100ffdfb317dbc5ee8f22fd7841`.
- `.legion-cli/map/DISCOVERY.md` SHA256 `f7543f5d1ef22384f2bf161a0ce2c848a66dc2c696a207ef5ad59fa99dd1775d`.
- `.legion-cli/map/ARCHITECTURE.md` SHA256 `ca48674060c4884548d874d81ff3bc9781f52a7229cd44b5ba27a54857de2fb3`.

The complete bounded input digest inventory is `.legion-cli/cache/runs/plan-mviu7s5p-95011b6a/inputs.json`. Base HEAD: `b5a226e49c52ecab4ddc2d678a7012d97e651a6a`. Pre-existing WIP: modified `.gitignore` and untracked `.legion-cli/`; preserve both. Map rootHash from SessionBrief: `fa098aa9eb89c10f65eaa4623c3e5a7f801d53494ccd9e80925d6d4127da5a77` (fallback map; not qualification).

The frozen frontmatter governs despite stale draft prose in the body. This plan does not edit the spec, resolve assumptions by assertion, approve the plan/spec, write engine readiness/authority records, run Legion CLI, implement code, launch clients/providers or publish anything. Browser/device, real provider/account calls and external platform evidence remain separately authorized. No credential or live data is required for planning.

## Native validation repair

The first native plan run rejected flat task frontmatter and removed those task files. Eight draft task records now preserve the seven reviewed outcomes plus the mobile test-project follow-up. They use the installed TaskSchema with nested contract, blocks, assignee, notes, explicit file limits and expected artifacts. Qualification probes are lasting test sources under packages/provider-mimo/qualification; task evidence is retained in captured output and permitted run summaries. Tasks never own Legion workflow files. No application source, frozen spec, assumptions or workflow authority was edited by this repair.

Run `plan-mviuzx72-c6c8d4b0` preserves this reviewed scope and all eight existing task contracts. Its source-only validation report is `.legion-cli/cache/runs/plan-mviuzx72-c6c8d4b0/validation.json`; the validator imports only the installed task schema and YAML parser, never the CLI or workflow engine. It checks contract exclusivity, dependency ordering, command identities, acceptance coverage and prospective test ownership. Engine validation and human approval remain separate. The earlier build_plan.py and plan-inventory.json are historical failed-run evidence and must not regenerate these artifacts. Read review.md for the bounded repair and unresolved gates.
