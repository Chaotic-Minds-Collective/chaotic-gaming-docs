# Repository Map

| Repository | Responsibility |
| --- | --- |
| `cmg-gaming-site` | Existing public-facing Next.js website |
| `cmg-discord-glitch-bot` | Existing independent Discord bot |
| `cmg-atlas-core-plugin` | Shared Core API, database migrations, auth, events and platform modules |
| `cmg-sdk` | Shared TypeScript API/event/adapter contracts |
| `cmg-atlas-plugin` | ATLAS adapter and server-side integration |
| `cmg-7dtd-plugin` | 7 Days to Die adapter and server-side integration |
| `cmg-ark-plugin` | Future ARK adapter |
| `cmg-docs` | Architecture and operator documentation |

Repositories are private unless explicitly changed. Existing website and bot repositories are retained rather than duplicated.

## Dependency direction

Website, Discord bot and game adapters depend on versioned Core API contracts and the SDK. They do not depend on Core's internal database schema or share database credentials.
