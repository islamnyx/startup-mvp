# MVP Todo List

## Phase 0 - Foundations (weeks 1-2)
- [ ] Write threat model draft (token theft, policy tampering, audit tampering, confused deputy, SSRF, tenant isolation)
- [ ] Review threat model with whole team
- [ ] Fix demo scenario (finance/ops agent: read invoices, query DB, email customers, issue refunds)
- [ ] Write attack script for demo
- [ ] Set up repo, CI, Compose skeleton
- [ ] Define coding standards and ADRs
- [ ] Define policy input JSON schema (contract)
- [ ] Schedule first 5 customer interviews

## Phase 1 - Gateway Skeleton (weeks 3-5)
- [ ] Agent registry
- [ ] Short-lived signed tokens
- [ ] Token rotation and revocation
- [ ] Tool registry
- [ ] Invoke endpoint (pass-through with logging)
- [ ] Mock tools for tests
- [ ] Test: agent registers, calls mock tool, call recorded

## Phase 2 - Policy Engine (weeks 6-8)
- [ ] OPA sidecar integration
- [ ] Stable policy input schema
- [ ] First Rego policies
- [ ] Policy versions stored in Postgres
- [ ] Dry-run (simulate) mode
- [ ] Deny reasons in API response
- [ ] Policy unit tests in CI
- [ ] Test: same call allowed/denied by policy, deny reason logged

## Phase 3 - Connectors (weeks 9-10)
- [ ] Envelope-encrypted secrets store
- [ ] HTTP connector (allowlist, SSRF protection)
- [ ] PostgreSQL connector (read-only default, parameterized queries)
- [ ] SMTP email connector
- [ ] MCP proxy
- [ ] Test: agent does real work, never sees password

## Phase 4 - Approvals (weeks 11-12)
- [ ] Pending state
- [ ] Approver queue
- [ ] Approve/deny with timeout
- [ ] Approval bound to exact params (hash)
- [ ] Emergency kill switch (revoke tokens immediately)
- [ ] Test: refund above threshold pauses; changing amount invalidates approval

## Phase 5 - Audit (weeks 13-14)
- [ ] Hash-chained audit log
- [ ] Verify CLI
- [ ] Export to JSON
- [ ] Optional external hash anchoring
- [ ] Test: editing a DB row detected by verification

## Phase 6 - Cross-Step Policies (weeks 15-16)
- [ ] Trust labels on data (internal, customer-supplied, web)
- [ ] Carry labels through session
- [ ] Session-aware rules (untrusted -> external send -> require approval)
- [ ] Test: invoice-injection attack blocked by session-aware rule

## Phase 7 - Console (weeks 17-18)
- [ ] Agents page
- [ ] Policies page
- [ ] Live activity page
- [ ] Approvals queue page
- [ ] Audit page with verify button
- [ ] Kill switch control

## Phase 8 - Red-Team & Hardening (weeks 19-20)
- [ ] Prompt-injection test suite (automated)
- [ ] Before/after report
- [ ] Pen-test gateway against Phase 0 threat model
- [ ] Documentation and install guide
- [ ] Recorded demo

## Cross-Cutting Security
- [ ] Rate limiting and per-agent budgets
- [ ] Strict input validation on every connector
- [ ] HTTP connector: allowlist, no private IP ranges, no redirects by default
- [ ] Tenant isolation tests from start
- [ ] Dependency pinning and scanning
- [ ] Secrets scanning in CI
- [ ] Policy changes audited and approval-gated

## MVP Acceptance Criteria
- [ ] Agent registered, scoped identity, revoked in seconds
- [ ] No tool call reaches business system without logged policy decision
- [ ] Agents never receive real credentials
- [ ] High-risk actions pause for human; approval bound to exact params
- [ ] Audit log verifies; tampering detected
- [ ] Demo prompt-injection attack blocked with report
- [ ] Deploys with one command on customer's own machine