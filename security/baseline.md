# Security Baseline

- Separate production and development credentials.
- Never commit tokens, passwords, OAuth secrets or database credentials.
- Use least-privilege service identities, separate per application and environment.
- Store credential hashes, support rotation and revocation.
- Verify ownership before linking Discord, Steam or game identities.
- Discord roles alone never grant game administration.
- Scope permissions to platform, game, cluster, server or guild.
- Audit administrative actions and sensitive account changes.
- Rate-limit authentication and verification; prevent account enumeration.
- Validate webhook signatures and payment-provider events server-side.
- Keep commerce ledger entries immutable and reward delivery idempotent.
- No production deployment or live payments before security review, backups and recovery procedures.
