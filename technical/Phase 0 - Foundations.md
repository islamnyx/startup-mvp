# Phase 0 - Foundations

- Write threat model for the gateway itself: token theft, policy tampering, audit tampering, confused deputy, SSRF, tenant isolation.
- Fix demo scenario: finance/ops agent that reads invoices, queries DB, emails customers, issues refunds.
- Set up repo, CI, Compose, coding standards, ADRs.
- Start customer interviews in parallel, keep through whole plan.

Done when: repo runs `docker compose up` and threat model reviewed by everyone.

## Links
- Next: [[Phase 1 - Gateway Skeleton]]
- Informs: [[Security]]