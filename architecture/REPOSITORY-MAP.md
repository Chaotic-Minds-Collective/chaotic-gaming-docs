# Repository Map

| Repository | Responsibility |
| --- | --- |
| `cmg-gaming-site` | Public-facing Chaotic Minds Gaming website and player portal |
| `cmg-discord-glitch-bot` | Discord community bot for verification, onboarding, tickets, moderation and status |
| `cmg-atlas-core-plugin` | Shared Core API, database migrations, auth, events and platform modules |
| `cmg-sdk` | Shared TypeScript API, event and adapter contracts |
| `cmg-atlas-plugin` | ATLAS adapter and server-side integration |
| `cmg-7dtd-plugin` | 7 Days to Die adapter and server-side integration |
| `cmg-ark-plugin` | Future ARK: Survival Evolved adapter |
| `cmg-atlas-resource-map-plugin` | ATLAS island, resource and travel map application |
| `cmg-atlas-restart-overlay-plugin` | ATLAS restart countdown overlay and schedule utility |
| `cmg-atlas-status-host-plugin` | Planned ATLAS status-host component; currently a placeholder |
| `cmg-admin-console-plugin` | ATLAS administration console and server operations dashboard |
| `cmg-atlas-admin-plugin` | ATLAS admin tools, backend, Discord bot, frontend and backup utilities |
| `cmg-atlas-tribes-plugin` | Cluster-aware tribes and group management |
| `cmg-atlas-commerce-plugin` | Multi-grid shop, wallet, entitlements and reward delivery |
| `cmg-atlas-connect-plugin` | Cross-grid chat, announcements and Discord relay |
| `cmg-atlas-player-plugin` | Player utilities, recovery and progression |
| `cmg-atlas-world-plugin` | World/grid policy, safe zones and gameplay rules |
| `cmg-atlas-sentinel-plugin` | Read-only health classification, security monitoring and alerts |
| `cmg-atlas-gridforge-plugin` | ATLAS configuration authoring, map editing and resource coverage |
| `cmg-atlas-adventures-plugin` | Quests, challenges and progression systems |
| `cmg-docs` | CMG architecture, security standards and operator documentation |

All names above are canonical repository slugs now live on GitHub. Use these names for repository links and clone URLs.

The following table preserves selected historical repository names for migration traceability. It is not an exhaustive rename list; the complete 33-entry mapping is maintained in the [organization naming standard](https://github.com/Chaotic-Minds-Collective/.github/blob/main/BRAND-AND-REPOSITORY-NAMING.md). Use the Canonical target slug column for current links and clone URLs.

| Canonical target slug | Historical repository name |
| --- | --- |
| `cmg-gaming-site` | `chaotic-gaming` |
| `cmg-discord-glitch-bot` | `glitch-bot` |
| `cmg-atlas-core-plugin` | `chaotic-gaming-core` |
| `cmg-sdk` | `chaotic-gaming-sdk` |
| `cmg-atlas-plugin` | `chaotic-gaming-atlas` |
| `cmg-7dtd-plugin` | `chaotic-gaming-7dtd` |
| `cmg-ark-plugin` | `chaotic-gaming-ark` |
| `cmg-docs` | `chaotic-gaming-docs` |

Repository visibility was not changed by the rename operation. Existing website and bot repositories were retained rather than duplicated.

## Dependency direction

Website, Discord bot and game adapters depend on versioned Core API contracts and the SDK. They do not depend on Core's internal database schema or share database credentials.
