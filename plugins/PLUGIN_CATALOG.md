# Chaotic Gaming Plugin Ecosystem

## Mission
Build an owned, modular plugin ecosystem that replaces useful third-party mod functionality without copying protected code, assets, names, or proprietary designs. Every plugin must have a clear purpose, documented compatibility, safe defaults, and a removal path.

## Delivery rules
- Prioritize ATLAS and 7 Days to Die; keep ARK in the architecture.
- Prefer server-side or external integrations that do not require every player to install files.
- For 7 Days to Die, prefer its native Web API and server event stream for crossplay/EAC-friendly features. XML modlets are next when an in-game configuration change is necessary. C# ModAPI/Harmony is reserved for features that cannot be delivered safely another way and must disclose client/EAC implications.
- For ATLAS, validate the supported server API/loader and exact game build before depending on it. The known Atlas Server API 1.71 listing describes C++ server plugins; this is a compatibility lead, not proof that it works with our host build.
- Never trust client-submitted currency, inventory, permissions, or rewards.
- Privileged actions require server-side authorization and audit records.
- Network calls need timeouts, bounded retries, idempotency, and graceful offline behavior.
- Each plugin is independently enabled, configured, upgraded, disabled, and removed.
- No paid dependency is required for the initial ecosystem.

## Plugin catalogue
P0 = foundation / first release; P1 = high-value launch feature; P2 = later expansion.

| ID | Plugin | Priority | Purpose |
| --- | --- | --- | --- |
| CG-CORE-001 | Plugin Manager | P0 | Discover, enable, disable, configure and report plugin health |
| CG-CORE-002 | Server Bridge | P0 | Authenticated connection between game adapters and Core |
| CG-CORE-003 | Audit & Activity Log | P0 | Record administrative actions, economy changes and plugin events |
| CG-CORE-004 | Permissions Bridge | P0 | Map platform roles to explicitly scoped game/server permissions |
| CG-CORE-005 | Server Status & Health | P0 | Online state, player counts, uptime, latency and health history |
| CG-CORE-006 | Player Identity Link | P0 | Link game identities to verified Chaotic Gaming accounts |
| CG-CORE-007 | Announcements & Scheduler | P1 | Scheduled notices, restart warnings and event broadcasts |
| CG-CORE-008 | Chat Bridge | P1 | Moderated game chat relay to approved Discord channels |
| CG-CORE-009 | Player Sessions & Statistics | P1 | Join/leave history, playtime and supported player statistics |
| CG-CORE-010 | Admin Toolkit | P1 | Safe, permission-checked common administration actions |
| CG-CORE-011 | Player Support & Reports | P1 | Player reports routed to support tickets |
| CG-CORE-012 | Events & Challenges | P1 | Scheduled events, objectives and participation tracking |
| CG-CORE-013 | Rewards & Entitlements | P1 | Queue verified account entitlements for game-side delivery |
| CG-CORE-014 | Economy Adapter | P1 | Server-authoritative currency integration with immutable ledger |
| CG-CORE-015 | Starter Kits & Welcome Flow | P1 | Configurable onboarding rewards with claim limits and audit |
| CG-CORE-016 | Teleport & Travel Tools | P1 | Permission-gated travel/recall where the game API supports it |
| CG-CORE-017 | Claims & Territory Tools | P1 | Territory/claim utilities where supported by native systems |
| CG-CORE-018 | Tribe / Group Utilities | P1 | Tribe/group membership, activity and administration helpers |
| CG-CORE-019 | Anti-Abuse Rules | P1 | Rate limits, suspicious-action signals and configurable protections |
| CG-CORE-020 | Backup & Recovery Coordinator | P1 | Safe save/config backup orchestration and restore verification |
| CG-CORE-021 | Mod/Plugin Update Manager | P1 | Version inventory, compatibility warnings and staged updates |
| CG-CORE-022 | Server Configuration Manager | P1 | Validated, versioned configuration profiles and change history |
| CG-CORE-023 | Leaderboards | P2 | Season-aware rankings from verified server events |
| CG-CORE-024 | Quest & Progression Framework | P2 | Configurable challenges, milestones and rewards |
| CG-CORE-025 | Vote & Community Rewards | P2 | Verified votes and abuse-resistant reward claims |
| CG-CORE-026 | Market / Player Trading Adapter | P2 | Server-validated listing and trade workflows where supported |
| CG-CORE-027 | Map / Location Services | P2 | Game-specific map, location and waypoint integrations |
| CG-CORE-028 | Moderation Evidence Pack | P2 | Correlated chat, session and admin evidence with retention controls |

## ATLAS implementation strategy
Start with server-side plugins only after a minimal loader proof-of-concept confirms startup, shutdown, logging, supported hooks, and safe failure behavior. Build a thin ATLAS adapter; keep account, economy, permissions and event logic in Core.

Initial candidates: Server Status & Health; Audit & Activity Log; Announcements & Scheduler; Player Sessions & Statistics; Permissions Bridge; Admin Toolkit; Starter Kits; Events & Challenges; Rewards & Entitlements; Tribe Utilities; Teleport Tools; Claims Tools; Economy; Anti-Abuse; Backup Coordinator.

ATLAS grid/cluster topology must be modeled explicitly. A player can move between maps/grids; a server is not the same thing as a map.

## 7 Days to Die implementation strategy
Use the built-in dedicated-server Web API and event stream first for monitoring, chat, administration and external services. Confirm endpoint details from the running server's own OpenAPI documentation for the exact game build before coding. Prefer crossplay-compatible external services that do not add files to the Mods folder.

Initial candidates: Server Status; Sessions & Statistics; Announcements; Chat Bridge; Admin Toolkit; Audit Log; Player Reports; Events; Rewards; Leaderboards; Backup Coordinator; Configuration Manager; Anti-Abuse; Economy; Starter Kits (only if a safe server-side delivery mechanism exists).

<!-- coderabbit-ai-generated:v1 -->

<!-- coderabbit-ai-generated-section:v1:d27d8646fb8c5804c68a7754953ad49886b2f66121334ec62c81a8603e3bc9a9 -->

Use XML modlets for small server-synced config changes. Treat XML modlet crossplay compatibility as unverified until tested on the exact target game build and client platforms. Use C# ModAPI/Harmony only when an external adapter or XML cannot deliver the feature. Document server/client/EAC/crossplay impact for every package.

<!-- /coderabbit-ai-generated:v1 -->

## ARK (later)
Design adapter contracts for clusters, maps, survivors, tribes, transfers, sessions and server-side events. Do not make ARK a launch dependency.

## Plugin package contract
Every plugin package includes:
- `plugin.json`: stable ID, name, semantic version, game, entry point, API compatibility range, dependencies, capabilities, permissions, configuration schema and support status.
- README, CHANGELOG, LICENSE, automated tests, health/readiness reporting, structured logs, data-retention notes, rollback and uninstall instructions.

## Release gates
1. Research: confirm game build, API/loader, host OS and licensing constraints.
2. Build: compile/package from a clean checkout.
3. Test: unit, contract, malformed-input, offline-Core and idempotency tests.
4. Server: isolated disposable test server; never first-test on production.
5. Compatibility: document dedicated server, client install, EAC and crossplay requirements.
6. Release: versioned artifact, checksum, changelog, known limitations and rollback path.

## Sources and compatibility notes
- 7 Days to Die Modding Wiki, Getting Started: https://7d2dmodding.wiki.gg/wiki/Getting_Started
- 7 Days to Die WebAPI: https://7d2dmodding.wiki.gg/wiki/WebAPI
- 7 Days to Die V3.0 notes: https://7d2dmodding.wiki.gg/wiki/Version_Notes/V3.0
- ATLAS Server API 1.71 listing: https://www.ark-server-api.com/resources/atlas-server-api.139/

Community wiki material is useful but not a substitute for validation against the exact server build. The ATLAS API listing is dated May 2024; treat compatibility as unverified until tested.
