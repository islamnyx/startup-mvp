# Phase 3 - Connectors

- Envelope-encrypted secrets store (Postgres + age/KMS; Vault-ready).
- Connectors: HTTP (allowlist + SSRF protection), PostgreSQL (read-only default, parameterized queries only), SMTP email.
- **MCP gateway/proxy as first-class** - route MCP JSON-RPC through gateway, tool discovery with policy enforcement, full audit of all MCP calls.
- Credential broker issues short-lived, scoped leases; agents never receive raw secrets.
- Test deny on unknown tools/hosts.

Done when: agent does real work via MCP or native connector and never sees a password; all calls go through policy + audit. 

## Links
- Prev: [[Phase 2 - Policy Engine]]
- Next: [[Phase 4 - Approvals]]