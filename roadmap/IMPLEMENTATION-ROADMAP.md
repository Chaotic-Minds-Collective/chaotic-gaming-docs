# Implementation Roadmap

## Phase 1 — Platform foundation
- [x] Create dedicated repositories.
- [x] Establish Core TypeScript/Fastify scaffold.
- [x] Add initial PostgreSQL identity, access, audit, outbox and idempotency migration.
- [x] Add game registry and isolated game schemas.
- [x] Add service-token authentication middleware and provisioning CLI.
- [x] Define shared SDK contracts.
- [ ] Pass Core CI build and migration checks.
- [ ] Review and merge foundational PRs.

## Phase 2 — Identity and API
- [ ] Player registration and secure login/recovery.
- [ ] Discord and Steam account linking with proof of ownership.
- [ ] Scoped permission enforcement for user and service identities.
- [ ] API versioning, request validation, rate limiting and audit coverage.
- [ ] API contract tests and OpenAPI documentation.

## Phase 3 — Existing applications
- [ ] Integrate website with Core account and game catalog APIs.
- [ ] Integrate Glitch Bot using a dedicated service identity.
- [ ] Preserve bot-native features during Core outages.
- [ ] Add integration health and reconnect behavior.

## Phase 4 — Game integrations
- [ ] ATLAS compatibility proof-of-concept on an isolated test server.
- [ ] 7DTD compatibility proof-of-concept on an isolated test server.
- [ ] Normalize player identity, sessions, server health and game events.
- [ ] Build admin tools and safe configuration workflows.
- [ ] ARK adapter when first two game integrations are stable.

## Phase 5 — Community and commerce
- [ ] Community tickets, moderation cases, announcements and events.
- [ ] Product catalog and game-specific product mappings.
- [ ] Payment sandbox and signed webhook verification.
- [ ] Entitlements, append-only wallet ledger and reward queue.
- [ ] Reconciliation, refund handling and abuse controls.

## Release gates
No production deployment, live payment processing, game-server modification, live Discord changes or paid infrastructure until explicitly approved. All game adapters must pass compatibility tests on isolated servers first.
