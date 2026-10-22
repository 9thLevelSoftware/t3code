# Brownfield discovery

Intent: repository audit
Source snapshot: 31dba453b0f8d67a615f6799af670be2b8224ede1b4ce66862f67c3285516f82

## Architecture and integration points

Read .legion-cli/map/ARCHITECTURE.md for module exports and imports.
Mapped modules: 3890. Source files: 2620. Test files: 199.

## Verification configuration (not executed)

- package.json scripts.test: vp run -r test

## Existing behavior and constraints

Use the selected change to inspect its entrypoints, tests, callers, persistence, and external dependencies.
Confirm deployment requirements and invariants with the user; the module map cannot establish these.

## Findings to confirm and prioritize

### F-1 (P2)
2617 source files have no nearby test by filename heuristic; this does not establish missing coverage.
- .coderabbit.config.ts
- .github/scripts/ci-changes.cjs
- .github/scripts/mirror-play-apk.cjs
- .pnpmfile.cjs
- .repos/alchemy-effect/.pnpmfile.mjs
- .repos/alchemy-effect/benchmark/container/alchemy.run.ts
- .repos/alchemy-effect/benchmark/container/contexts/microvm-bun/server.js
- .repos/alchemy-effect/benchmark/container/contexts/microvm-node/server.js
- .repos/alchemy-effect/benchmark/container/contexts/microvm-python/app.py
- .repos/alchemy-effect/benchmark/container/scripts/plot-blog.py
- .repos/alchemy-effect/benchmark/container/src/build-role.ts
- .repos/alchemy-effect/benchmark/container/src/bun-container.ts
- .repos/alchemy-effect/benchmark/container/src/bun-image.ts
- .repos/alchemy-effect/benchmark/container/src/bun-object.ts
- .repos/alchemy-effect/benchmark/container/src/container-worker.ts
- .repos/alchemy-effect/benchmark/container/src/effectful-bun.ts
- .repos/alchemy-effect/benchmark/container/src/effectful-container.ts
- .repos/alchemy-effect/benchmark/container/src/effectful-impl.ts
- .repos/alchemy-effect/benchmark/container/src/effectful-node.ts
- .repos/alchemy-effect/benchmark/container/src/effectful-object.ts

## Next decision

Select a bounded remediation increment with the user before writing a specification. Unselected findings remain a backlog.

This is bounded static discovery, not a comprehensive security or coverage audit. No checks or remediation were executed.
