# Security

Cross-cutting:
- Rate limiting and per-agent budgets.
- Strict input validation on every connector. HTTP connector is biggest SSRF risk: allowlist, no private IP ranges, no redirects by default.
- Tenant isolation tests from start, even with one tenant.
- Dependency pinning and scanning, secrets scanning in CI.
- Policy changes audited and approval-gated.

## Links
- Origin: [[Phase 0 - Foundations]]
- Protects: [[Request Flow]]