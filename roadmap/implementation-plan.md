# Chaotic Gaming Implementation Plan

## Phase 1 — Foundation

- [x] Create dedicated repositories and reuse existing website and Glitch Bot repositories.
- [x] Core identity/session and scoped service identity foundation.
- [x] PostgreSQL migrations for identity, game topology, community, commerce, operations and game data.
- [x] Public server status API and heartbeat ingestion.
- [x] Normalized game event ingestion with idempotency and outbox.
- [x] Persistent plugin registry and per-server desired state/health APIs.
- [x] Role assignment and server/service provisioning CLIs.
- [x] Website account, store, server and mods page foundations.
- [x] Shared typed SDK contracts and Core client.
- [ ] Fresh PostgreSQL migration CI green and API integration tests.
- [ ] Security review and account recovery/email verification.

## Phase 2 — 7DTD first server integration

- [x] Existing authenticated Web API client and SSE parser reviewed.
- [x] Core event publisher and durable local event spool.
- [ ] Verify actual server OpenAPI endpoint paths on a disposable 7DTD server.
- [ ] Configure exact SSE event-name mapping.
- [ ] Verify server heartbeat and player session events end-to-end.
- [ ] Add player identity mapping and read-only server statistics.
- [ ] Build safe mod/plugin lifecycle adapter after protocol validation.

## Phase 3 — ATLAS

- [x] Minimal Windows x64 plugin lifecycle DLL source and CI build scaffold.
- [ ] Confirm AtlasApi loader ABI, manifest and directory layout on disposable server.
- [ ] Build/load/unload the DLL on the exact ATLAS server build.
- [ ] Add authenticated Core heartbeat/event bridge.
- [ ] Implement server status, player sessions, grid/map/tribe data only after API validation.

## Phase 4 — Website, commerce and community

- [x] Account and catalog UI foundations.
- [ ] Discord/Steam OAuth ownership verification and secure account recovery.
- [ ] Payment provider sandbox and signed webhook verification.
- [ ] Order reconciliation, refunds and entitlements.
- [ ] Reward delivery workers and idempotent game confirmation.
- [ ] Admin interface and community features.

## Phase 5 — ARK

- [x] Logical ARK schema prepared.
- [ ] Confirm server API and cluster transfer model.
- [ ] Implement adapter and test popular maps in isolated cluster.
- [ ] Enable staged launch after ATLAS and 7DTD are stable.

## Release gates

No production deployment, billing, public sale, plugin installation or live server modification is part of these source-code milestones. Each requires separate validation and approval.
