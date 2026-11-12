# Security baseline

## Non-negotiable controls

1. Keep database credentials and service secrets out of Git, browser bundles, Discord messages and game configuration distributed to players.
2. Store only hashes of session tokens and service credentials.
3. Verify external identity ownership with provider-controlled proof before linking accounts.
4. Enforce authorization in Core APIs; never trust client-supplied roles or Discord role names.
5. Scope permissions to platform, game, cluster, server or guild.
6. Use least-privilege service identities, separate per application.
7. Validate request bodies and enforce payload limits.
8. Rate-limit authentication, account linking, ticket creation and sensitive actions.
9. Record security-relevant outcomes without logging secrets or unnecessary personal data.
10. Use idempotency keys for payment webhooks and reward delivery.

## Deployment controls

- Separate development, test and production credentials and databases.
- Require TLS for external traffic and database connections.
- Back up production data and test restore procedures before migrations.
- Never run migrations automatically during an unreviewed production deployment.
- Sensitive actions fail closed if authorization or provider verification is unavailable.
