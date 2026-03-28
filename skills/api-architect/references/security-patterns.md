# API Security Patterns

## Authentication (Who are they?)
*   **OAuth2 Client Credentials:** Default for machine-to-machine (M2M) FIs/Banks.
*   **OAuth2 Authorization Code + PKCE:** Default for user-facing applications.
*   **JWT (JSON Web Tokens):** Use for stateless claims; include `iss`, `sub`, `aud`, `exp`, and custom `scopes`.

## Authorization (What can they do?)
*   **Fine-Grained Scopes:** Use `resource:action` patterns (e.g., `trade:write`, `instruction:cancel`).
*   **On-Behalf-Of (OBO):** If an intermediary acts for a beneficiary, require a `Subject-Id` or `Agent-Token` header for auditability.

## Integrity & Non-Repudiation
*   **Request Signing:** For high-value transactions (e.g., JWS or HTTP Signatures).
*   **Idempotency:** Require an `Idempotency-Key` header for all `POST`, `PUT`, `PATCH`, and `DELETE` operations to prevent double-execution.

## Transport & Rate Limiting
*   **mTLS (Mutual TLS):** Strongly recommended for inter-bank connectivity.
*   **Rate Limits:** Expose limits via headers (`X-RateLimit-Limit`, `X-RateLimit-Remaining`).
