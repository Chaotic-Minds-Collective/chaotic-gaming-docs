# ADR 0003: Separate Game Data Schemas

- Status: Accepted
- Decision: Keep game-specific records in separate PostgreSQL schemas while sharing central identity and authorization.
- Initial schemas: `games_atlas`, `games_7dtd`, `games_ark`.
- Consequences: Common platform identity is shared without forcing different game models into one generic table.
