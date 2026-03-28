# Agentic Ergonomics: Designing APIs for LLMs

To eliminate the need for custom MCP servers, an API must be "Self-Describing" for an AI agent. Use this checklist during the **Execution Phase** of your design.

## 1. High-Signal Descriptions
*   **Contextual Descriptions:** Don't just name the field; explain its role in the workflow.
    *   *Bad:* `description: The UTI`
    *   *Good:* `description: The Unique Trade Identifier (GUID) assigned after a match. Use this as the primary key for all subsequent state-tracking and confirmation calls.`
*   **Enum Clarity:** For every enum, describe what each state represents and what the expected "Next Step" is for the agent.

## 2. Mandatory Examples
*   **Value Discovery:** Every schema property MUST have a realistic `example`. 
*   **Complex Formats:** If a field is a `tx_hash` or `uetr`, provide a real-world string example (e.g., `example: 0x123...abc` or `f81d4fae...`).
*   **Full Object Examples:** Provide at least one complete request and response body example for every operation.

## 3. Semantic Error Objects
*   **Actionable Errors:** Errors should not just state what's wrong; they should suggest a "Self-Healing" path.
    *   *Example:* `{ "code": "RATE_LIMIT_EXCEEDED", "message": "Too many requests.", "suggested_retry_after_ms": 5000 }`
*   **Error Schemas:** Define the error structure in the OpenAPI spec so the agent can parse and handle failures programmatically.

## 4. Workflow & Linkage (`x-links`)
*   **Operation Linkage:** Use OpenAPI `links` to define the relationship between endpoints.
    *   *Pattern:* Link the `201 Created` response of a `POST /instructions` to the `GET /settlements/{uti}` operation using the returned ID.
*   **Sequence Hints:** If an API requires a specific sequence (e.g., *Match -> Escrow -> Confirm*), mention this in the top-level `info.description`.

## 5. Security Transparency
*   **Scope Guidance:** Explicitly state which OAuth2 scopes are required for each operation in the `description` or `security` sections.
*   **Idempotency:** Always include an `Idempotency-Key` header for state-changing operations to allow agents to safely retry after a timeout.
