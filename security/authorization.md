# Security and Authorization Model

## Principals

A principal is either a human user or an application/service identity. Each bot, game adapter and automation receives a separate service principal.

## Role-based access control

Roles grant permissions at a specific scope:
- platform
- game
- cluster
- server
- Discord guild

Examples include platform administrator, game administrator, server administrator, moderator, support, player, plugin manager, plugin runtime reporter, server heartbeat reporter and game event publisher.

Discord role membership does not automatically grant Core permissions.

## Credential handling

- Passwords use Argon2id.
- Opaque player session tokens are stored as hashes.
- Service tokens are high entropy and stored as hashes; the cleartext is shown once at creation.
- Use a distinct service credential per application and environment.
- Rotate credentials by creating a replacement, switching the service, then revoking the old one.
- Never put service tokens or database credentials in browser code or game clients.

## Game server boundaries

- Game adapters receive only the permissions they need.
- Heartbeat reporting is separate from server administration.
- Event publishing is separate from plugin management.
- Plugin runtime reports are separate from plugin release registration.
- Server and game scopes must not be widened to platform scope for convenience.

## Fail-closed rules

- Do not grant an entitlement before signed payment confirmation.
- Do not install or execute a plugin based only on a catalogue entry.
- Do not allow player identity linking based only on a claimed username.
- Do not allow privileged operations when Core authorization is unavailable.
- Do not trust browser redirect parameters as proof of payment.

## Operational requirements

- HTTPS outside localhost.
- Rate limits on public authentication routes.
- Audit logs for authorization-sensitive actions.
- Secrets stored in environment/secret managers, not Git.
- Isolated development, test and production databases.
- No live game server or Discord changes from CI.
