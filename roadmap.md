# Development Roadmap

## Foundation
- [x] Create component repositories.
- [x] Add Core TypeScript service and PostgreSQL foundation migration.
- [x] Add shared SDK contract seed.
- [x] Document architecture and security boundaries.
- [ ] Add Core authentication, sessions and service-to-service authorization.
- [ ] Add migration tests and CI.

## Integrations
- [ ] Connect website to Core API.
- [ ] Connect Glitch Bot while preserving independent/offline operation.
- [ ] Add transactional outbox worker and event consumers.
- [ ] Validate ATLAS plugin/API compatibility on an isolated test server.
- [ ] Validate 7DTD server interface before implementing commands.
- [ ] Add ARK after first two game integrations stabilize.

## Player services
- [ ] Product catalog and entitlements.
- [ ] Payment sandbox and signed webhook validation.
- [ ] Idempotent game reward delivery.
- [ ] Mod catalog and compatibility metadata.
