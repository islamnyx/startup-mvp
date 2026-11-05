# Ground Rules

- Enforce outside the model. The LLM only proposes actions.
- Credential brokering. Agents hold only a short-lived token for the gateway. Real secrets live in the gateway.
- Default deny, fail closed. If the policy engine is down or a rule is missing, the action is blocked.
- One tight vertical slice. No visual agent builder, no own orchestration engine, no marketplace, no billing, no multi-region.
- Self-hostable from day one. Everything runs from docker-compose, no proprietary cloud dependency.

## Links
- Shapes: [[Stack]], [[Request Flow]]
- Constrains: [[Slippage]]