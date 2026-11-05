# Request Flow

1. Agent calls via SDK/MCP proxy to POST /v1/tools/{tool}/invoke with its token (or MCP JSON-RPC).
2. Gateway authenticates token, loads agent, owner, session context, builds **delegation chain** (human → agent → session).
3. Normalizes into policy input: who (agent, owner, org, delegation chain), what (tool, action, parameters), on what (resource), context (session history, data labels, time, risk).
4. OPA returns allow, deny, or require_approval, plus reason and obligations (e.g. redact fields).
5. Approvals park in pending (console + Slack/Teams webhook). Human approves/denies; approval bound to hash of exact parameters and full delegation chain context.
6. On allow, credential broker issues short-lived, scoped credential (never exposed to agent); connector executes via brokered credential.
7. Output filtered (redaction, trust labeling), logged, returned.
8. Every step appends to hash-chained audit log with delegation chain, policy version, decision reason, and signed root.

## Links
- Uses: [[Stack]]
- Governed by: [[Ground Rules]]
- Stored in: [[Data Model]]
- Audited by: [[Phase 5 - Audit]]