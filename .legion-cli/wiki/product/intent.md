---
schemaVersion: legion-cli-wiki-page/v1
title: Intent
aliases:
  - intent brief
tags:
  - product
trust: untrusted
updated: 2026-10-22T00:34:51.490Z
---

T3 Code users who want additional coding model providers, including API-accessible subscriptions such as Xiaomi MiMo Token Plan.

They want to select and use those providers within T3 Code; the existing configuration and integration gaps are being checked against the repository before choosing an implementation.

Proposed runtime revision: MiMo-Code, with no separate OpenCode installation. Preserve reusable API setup and MiMo Token Plan as the first preset. This revision remains a discussion proposal.

Happy path: 1) In the destination environment's provider settings, choose the MiMo Token Plan preset or supported custom API setup. 2) Supply the region/base URL, secret API credential and model selection or discovery settings, and receive clear validation feedback. 3) Select the configured provider and model in a new coding thread. 4) Submit a coding request and interact with streamed progress, tools and approvals using the compatible existing harness. 5) Return to the thread or reconnect from another client, then edit, disable or remove the configuration using existing provider lifecycle rules without corrupting saved work.

Out of scope:
- Writing a new coding-agent loop or replacing T3 orchestration; integrating the existing MiMo-Code runtime through a provider adapter is in the proposed scope.
- Compatibility with every API or support for additional API protocol families in v0.
- Automatic reconfiguration of independently hosted runtime services; preserve existing external OpenCode connections and their host-owned setup.
- Non-coding audio or video services.
- Automatic fallback from Token Plan billing to pay-as-you-go billing.
- Bundling or forking MiMo-Code source, embedding its desktop UI, or implementing its unrelated memory, workflow and multimedia features in T3.

Revised after the user questioned the OpenCode dependency and supplied XiaomiMiMo/MiMo-Code. MiMo-Code is a proposed runtime, not an approved implementation. Prior interview rounds remain intact; technical assumptions and discussion decisions remain open/proposed.
