# Chaotic Minds Gaming Platform Architecture

## 1. System overview

Chaotic Minds Gaming (CMG) is a multi-game PC community platform. The website, Discord bot and game servers share a central identity and integration layer without sharing database credentials or runtime processes.

### Applications
- **Core** — TypeScript modular monolith; PostgreSQL system of record; REST API; authorization; commerce and event processing.
- **Website** — player portal, game catalog, account management, community and future marketplace. Calls Core APIs; never connects directly to PostgreSQL.
- **Glitch Bot** — independent Discord application. Keeps Discord-native moderation, onboarding and support available when Core is unavailable. Core-dependent operations use authenticated service APIs.
- **Game adapters** — one adapter per game/server family. Translate game-specific server events and operations into stable Core contracts.
- **SDK** — shared API, event and adapter contracts.
- **Docs** — architecture, developer standards and operations runbooks.

## 2. Runtime topology

```text
Player Browser ──> Website ──┐
                             │ REST + user session
Discord ──> Glitch Bot ──────┼──> Chaotic Gaming Core ──> PostgreSQL
                             │             │
ATLAS Servers <──> ATLAS Adapter ─────────┤
7DTD Servers <──> 7DTD Adapter ──────────┤
ARK Servers <──> ARK Adapter (future) ───┘
                                           └──> Event Outbox / Workers
```

The Core is a modular monolith initially. Do not split it into microservices until operational load or team boundaries justify that complexity.

## 3. Data boundaries

One PostgreSQL deployment may host multiple schemas initially:
- `core` — principals, users, linked identities, sessions, roles, permissions, games, clusters and servers.
- `community` — guild settings, tickets, moderation and community activity.
- `commerce` — products, orders, verified payments, entitlements, wallet ledger and reward delivery.
- `operations` — audit logs, outbox, jobs, health and operational records.
- `games_atlas`, `games_7dtd`, `games_ark` — game-specific entities and events.

Logical schemas do not imply separate database servers. Keep data ownership explicit and use foreign keys within the database.

## 4. Identity

A player has one internal platform principal and may link multiple external identities: Discord, Steam and game-specific player/character IDs. External identifiers are stored as text and scoped by provider. Display names are never unique keys. Linking requires provider-backed proof of ownership.

A player may have multiple characters, survivors, maps and game sessions. Never assume one Steam identity equals one in-game character.

## 5. Authorization

Use RBAC with scoped assignments: platform, game, cluster, server or Discord guild. Discord roles do not automatically grant game-administration permissions. Each application and game adapter receives its own least-privilege service identity.

## 6. Events

State changes that need asynchronous consumers are written to a database-backed outbox in the same transaction as the originating change. Consumers must be idempotent, retry safely and expose delivery failures. The Discord bot must be able to resume missed events after reconnecting.

## 7. Commerce

Separate payment confirmation, entitlement ownership and game reward delivery. Verify payment-provider signatures server-side. Use idempotency keys. Keep wallet accounting append-only. Reward delivery must target a specific game, cluster, server/map and player/character identity. Use payment sandbox only until a separately approved production launch.

## 8. Resilience

- Website and Discord bot do not share a process.
- Bot-native moderation/onboarding continues if Core is unavailable.
- Game servers continue running if website/Core is unavailable.
- Core-dependent actions fail closed when authorization cannot be verified.
- Outbox workers retry safely after outages.
- No database credentials in browsers, Discord bot config or game plugin source.

## 9. Environments

Development, test and production are isolated. CI uses disposable PostgreSQL. Never point CI or local migrations at production. Production deployment and data changes require an approved change window.
