# Stack

| Part | Choice | Why |
|---|---|---|
| API and gateway | Python 3.12, FastAPI, Pydantic | Fast to build, strong typing |
| Database | PostgreSQL | Registry, policies, audit, approval queue (no Redis until needed) |
| Policy engine | OPA sidecar over REST | Standard, testable policy-as-code |
| Migrations/ORM | Alembic, SQLAlchemy | Standard |
| Frontend | Next.js + TypeScript, minimal | Console for agents, approvals, audit |
| Agent-side | Thin Python SDK + MCP proxy | Meets agents where they are |
| Observability | Structured logs first, OpenTelemetry later | Avoid early overhead |
| Packaging/CI | Docker Compose, GitHub Actions, pytest | |

Skip for now: Keycloak (local users with argon2 + TOTP, OIDC-ready), Vault (envelope-encrypted secrets in Postgres), Celery, Kubernetes.

## Links
- Runs: [[Request Flow]]
- Stores: [[Data Model]]