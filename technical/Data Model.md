# Data Model

Core tables: organizations, users, agents, agent_tokens, tools, connectors, secrets, policies (versioned), policy_bindings, sessions, delegation_chains, tool_calls, decisions, approvals, audit_events, secret_leases.

- **audit_events** is append-only. Each row stores the hash of the previous row plus its own content (prev_hash, hash), plus Ed25519 signature on periodic signed roots. A verification command/CLI detects tampering.
- **delegation_chains** records human → agent → session authorization with scope/justification; required on tool_calls, approvals, decisions, audit_events.
- **secret_leases** tracks short-lived brokered credentials; secrets encrypted at rest (envelope encryption, Postgres + age/KMS; Vault-ready).
- **approvals** bound to params hash and full delegation chain context.
- Fast revocation via agent_tokens revocation lists and agents.revoked_at.

## Links
- Supports: [[Request Flow]]
- Implemented in: [[Phase 1 - Gateway Skeleton]], [[Phase 2 - Policy Engine]], [[Phase 4 - Approvals]], [[Phase 5 - Audit]]