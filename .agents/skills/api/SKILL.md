---
name: api
description: HTTP and API work — endpoints, REST design, auth, rate limits, webhooks, pagination, versioning, and client-side consumption. Triggers on "endpoint", "api", "rest", "webhook", "401", "403", "rate limit", "pagination", "json", "curl", "sdk", "openapi".
---

# API

## When to use

Something crosses a process or network boundary and the contract is the design.

## Rules

- Contract first, in writing: method, path, request shape, response shape, and every error status.
  Then implement. Code that invents the contract mid-stream is how two clients drift apart.
- Status codes mean what they say. 400 malformed, 401 no identity, 403 identity without permission,
  409 state conflict, 422 semantically invalid, 429 rate limited, 5xx our fault.
- Errors return a machine-readable `code` plus a human `message`. Never a stack trace to the client.
- Auth at the boundary, validated on every request. Never trust a role that came from the client.
- Validate input at the edge, once, and pass a typed value inward. Re-validating deeper is noise.
- Idempotency for anything that charges, sends, or creates: accept an idempotency key, and make the
  retry return the first result rather than a second effect.
- Paginate anything that can grow. `limit`/`offset` for small sets, cursor for large ones.
- Version from the first day, even if the version is the empty string. Removing a field is a breaking
  change; adding one is not.
- Rate-limit per identity and return `Retry-After`. A silent 429 teaches clients to hammer.
- Webhooks: verify the signature, make handling idempotent, respond fast and process after.
- Client code: one request helper that handles auth, timeout, and error mapping. Not ten inline `fetch`.
- Timeouts and retries live on the client, with a cap, and only for idempotent operations.

## Done when

- The contract is written down and matches the code.
- Every error path returns a shape a client can branch on.
