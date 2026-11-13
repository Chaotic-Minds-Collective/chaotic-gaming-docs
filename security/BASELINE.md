# Security Baseline

These requirements apply to every Chaotic Gaming application, service, integration and payment flow.

## Payment webhooks

- Verify the payment provider's webhook signature using the provider's documented verification method, the unmodified raw request body and the configured webhook secret before processing **any** payment webhook event. Reject requests with missing or invalid signatures; do not process their payloads.
- Enforce webhook idempotency using the provider's stable event identifier (or an equivalent unique event key). Record and claim the event atomically before triggering payment or entitlement side effects, and treat duplicate deliveries as already processed. Signature verification does not replace idempotency; both controls are required.

## Access and credentials

- Deny access by default and authorize every protected action against the requesting principal and its scope.
- Keep secrets in approved secret storage or environment configuration; never commit secrets or expose service credentials to browser or game clients.
- Use distinct, least-privilege service identities for applications and integrations.

## Operational safeguards

- Require HTTPS outside local development.
- Keep development, test and production data and credentials separate.
- Audit-log security-sensitive actions without recording secrets or payment credentials.
- Do not grant entitlements based only on browser redirects or client-supplied payment status; require verified server-side payment confirmation.
