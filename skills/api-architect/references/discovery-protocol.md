# Capability-First Discovery Protocol

## Step 1: Core Business Capability
**Question:** "What is the primary business outcome we are exposing to the consumer?"
*   *Avoid UI/Data Focus:* If the user describes a "Screen" or "Database Table," stop. Ask for the *capability* (e.g., "Settlement Orchestration" vs "Bank Transactions").

## Step 2: Actors, Roles & Use Cases
**Question:** "Who is interacting with this API and what are their specific use cases?"
*   **Mandatory:** Ask for **Concrete Examples**. Request real-world scenarios and sample data values (e.g., "A Bank settles 100 USD with a Broker for 0.05 BTC").
*   **Intermediaries:** Identify if actors are acting on behalf of others (Beneficiaries/Agents).

## Step 3: Lifecycle & Workflow
**Question:** "What is the end-to-end journey of the resource?"
*   **States:** Identify clear transition points (e.g., `MATCHED` -> `ESCROWED` -> `COMPLETED`).
*   **Finality:** Define what constitutes "Success" and "Finality" (e.g., Ledger confirmation, external bank feed).
*   **Failure Modes:** Define what happens during disputes, timeouts, or cancellations.

## Step 4: Security & Compliance
**Question:** "What is the trust model for this capability?"
*   Reference [SECURITY.md](references/security-patterns.md) for patterns.
*   Identify Scopes (e.g., `settlement:read`, `settlement:write:internal`).

## Step 5: Source of Truth
**Question:** "Where does the authoritative data live?"
*   Is the API the "Primary Record" or a "Reflector" of external systems (Blockchain, ERP, Core Banking)?
