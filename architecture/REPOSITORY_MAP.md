# Repository map

| Repository | Responsibility |
|---|---|
| chaotic-gaming | Existing public website and player-facing entry point |
| glitch-bot | Existing independent Discord bot |
| chaotic-gaming-core | Shared API, identity, authorization, data and event processing |
| chaotic-gaming-sdk | Shared TypeScript contracts |
| chaotic-gaming-atlas | ATLAS-specific adapter and server-side plugin work |
| chaotic-gaming-7dtd | 7 Days to Die adapter |
| chaotic-gaming-ark | Future ARK: Survival Evolved adapter |
| chaotic-gaming-docs | Canonical technical and operational documentation |

## Dependency direction

Website, Discord bot and game adapters depend on versioned Core API contracts and the SDK. They do not depend on Core's internal database schema or share database credentials.
