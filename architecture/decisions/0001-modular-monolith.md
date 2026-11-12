# ADR 0001: Modular Monolith First

- Status: Accepted
- Decision: Build Core as a modular monolith with clear domain boundaries and PostgreSQL schemas.
- Context: Early traffic and team size do not justify distributed services.
- Consequences: Lower operational overhead and simpler transactions; modules must maintain explicit interfaces so they can be extracted later if scale requires it.
