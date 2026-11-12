# System Architecture

## Applications
- `chaotic-gaming-core`: TypeScript modular monolith and PostgreSQL owner.
- `chaotic-gaming`: existing Next.js public website.
- `glitch-bot`: existing independent Discord bot; basic Discord operations must survive Core outages.
- `chaotic-gaming-sdk`: shared versioned contracts.
- Separate ATLAS, 7DTD and future ARK adapters.

## Data ownership
Core owns player identities, verified linked accounts, roles, entitlements, server registry and platform events. Game adapters own game-specific observations. Website and bot use authenticated APIs and never receive direct database credentials.

## Initial topology
One modular monolith with PostgreSQL schemas `core`, `community`, `commerce`, `integrations`, `operations`, `games_atlas`, `games_7dtd`, `games_ark`. REST APIs initially; transactional outbox for durable events. Consumers must tolerate retries and duplicate delivery.

No microservices, Redis requirement, paid broker, live payment processing or production server mutation in the first milestone.
