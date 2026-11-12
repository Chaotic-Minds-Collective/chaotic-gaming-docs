# System Overview

```mermaid
flowchart LR
  WEB[Website / Player Portal] -->|HTTPS REST| CORE[Chaotic Gaming Core]
  BOT[Glitch Discord Bot] -->|HTTPS REST| CORE
  ATLAS[ATLAS Adapter] -->|HTTPS REST| CORE
  TD[7DTD Adapter] -->|HTTPS REST| CORE
  ARK[ARK Adapter - future] -->|HTTPS REST| CORE
  CORE --> DB[(PostgreSQL)]
  CORE --> OUTBOX[Transactional Outbox]
  OUTBOX --> BOT
  OUTBOX --> ADAPTERS[Game Adapters]
```

Core owns player identity, authorization, platform state, commerce entitlements and integration event records. Clients do not connect directly to PostgreSQL. The bot remains operational for independent Discord functions during Core outages.
