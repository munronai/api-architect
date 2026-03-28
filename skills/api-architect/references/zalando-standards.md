# Zalando RESTful Guidelines (Condensed)

## 1. Naming Conventions
*   **Properties:** `snake_case` (e.g., `external_reference`).
*   **Paths:** `/kebab-case-resources` (Plural, e.g., `/settlement-instructions`).
*   **Headers:** `Kebab-Case` (e.g., `Idempotency-Key`).

## 2. Resource Modeling
*   **Sub-resources:** Use sparingly; prefer top-level collections for primary capabilities.
*   **Versioning:** Do not use version numbers in the URL. Prefer `Accept` headers or non-breaking evolutionary changes.

## 3. Operations & Status Codes
*   **POST:** Use for creation; return `201 Created` (Sync) or `202 Accepted` (Async).
*   **GET:** Return `200 OK` or `404 Not Found`.
*   **DELETE:** Return `204 No Content`.
*   **Conflict:** Return `409 Conflict` if the resource state prevents the action.

## 4. Documentation (OpenAPI)
*   **Descriptions:** Every property, parameter, and schema MUST have a `description`.
*   **Examples:** Every schema MUST provide at least one realistic `example`.
