# Security Baseline

These requirements apply to every Chaotic Minds Gaming application, service, integration and payment flow.

## Payment webhooks

- Verify the payment provider's webhook signature using the provider's documented verification method, the unmodified raw request body and the configured webhook secret before processing **any** payment webhook event. Reject requests with missing or invalid signatures; do not process their payloads.
- Enforce webhook idempotency using the provider's stable event identifier (or an equivalent unique event key). Track processing state separately from completion (for example, `pending`, `processing`, `completed`, and `retryable_failed`). A claim must not permanently suppress retries: use a recoverable lease/timeout or equivalent mechanism so abandoned or failed claims can be safely reclaimed. Mark an event `completed` only after its entitlement side effects succeed. Where the claim and entitlement updates share a database, commit them in one atomic transaction. For external side effects, use an idempotency key and retry-safe delivery so retries cannot duplicate the effect. Treat only completed events as duplicates that require no further processing.
  
## Access and credentials

- Deny access by default and authorize every protected action against the requesting principal and its scope.
- Keep secrets in approved secret storage or environment configuration; never commit secrets or expose service credentials to browser or game clients.
- Use distinct, least-privilege service identities for applications and integrations.

## Operational safeguards

- Require HTTPS outside local development.
- Keep development, test and production data and credentials separate.
- Audit-log security-sensitive actions without recording secrets or payment credentials.
- Do not grant entitlements based only on browser redirects or client-supplied payment status; require verified server-side payment confirmation.
