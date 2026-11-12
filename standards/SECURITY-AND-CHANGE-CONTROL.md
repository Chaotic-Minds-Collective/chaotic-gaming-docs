# Security and Change Control

## Credentials
- Secrets must be stored in approved secret storage/environment configuration, never committed.
- Service tokens are random, high-entropy, scoped, revocable and stored only as hashes.
- Rotate credentials and revoke compromised tokens.
- Each app/game adapter has a distinct service identity.

## Authorization
- Deny by default.
- Check principal status and scope on every protected action.
- Never equate Discord roles with platform/game administrator roles.
- Record privileged actions and denied access attempts.

## Data
- Store timestamps in UTC.
- Store external identifiers as text.
- Store money in integer minor units.
- Use append-only ledgers for balances and rewards.
- Keep production, test and development data separate.

## Changes
- Work on feature branches.
- Use pull requests and CI.
- No destructive migrations; prefer additive changes and explicit backfills.
- No production deployment, live configuration change, payment activation or third-party contact without explicit approval.
