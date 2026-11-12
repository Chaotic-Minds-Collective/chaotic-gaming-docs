# Implementation roadmap

## Phase 1 — Platform foundation

- [x] Create dedicated component repositories.
- [x] Establish initial Core runtime scaffold and database migration draft.
- [x] Establish shared SDK contract package.
- [x] Establish architecture and security documentation.
- [ ] Install dependencies and run typecheck/build against a real Node.js environment.
- [ ] Review migration against the selected PostgreSQL provider and test on an isolated database.

## Phase 2 — Identity and API

- [ ] Registration and authentication flows.
- [ ] Discord and Steam account ownership verification.
- [ ] Session issuance, rotation, revocation and recovery.
- [ ] Scoped RBAC enforcement and service credentials.
- [ ] OpenAPI specification and API integration tests.

## Phase 3 — Community and game integrations

- [ ] Integrate Glitch Bot through service-authenticated Core APIs.
- [ ] Add 7 Days to Die server adapter and event ingestion.
- [ ] Validate ATLAS Server API compatibility with an isolated server proof of concept.
- [ ] Add ARK adapter when the initial games are stable.

## Phase 4 — Player portal and commerce

- [ ] Player profile and linked-account management.
- [ ] Server status, player sessions and game-specific dashboards.
- [ ] Product catalog, payment-provider sandbox and entitlement ledger.
- [ ] Idempotent reward delivery with retry and reconciliation.

## Phase 5 — Operations

- [ ] Server/plugin registry and compatibility checks.
- [ ] Observability, audit review and alerting.
- [ ] Backup/restore and incident runbooks.
- [ ] Production readiness review before any deployment.
