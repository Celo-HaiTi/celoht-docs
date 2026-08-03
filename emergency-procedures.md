# Agent Operations Manual: Emergency Procedures

*Detailed operational companion to [../AGENT_NETWORK.md](../AGENT_NETWORK.md#field-operations--emergency-procedures).*

## Device Loss or Theft

1. Agent (or a trusted contact, if the agent cannot act themselves) contacts their Regional Coordinator or the emergency support line immediately
2. Regional Coordinator initiates an immediate account freeze via the governance-controlled admin function — sets status to `Suspended` on the [AgentRegistry](../SMART_CONTRACTS.md#agentregistry--reference-specification), preventing any further transactions from being attributed to the compromised account
3. Agent's dashboard access is invalidated pending identity re-verification
4. Once the agent's identity is confirmed safe and secure device access restored/replaced, reactivation follows an abbreviated version of [onboarding-and-verification.md](./onboarding-and-verification.md#step-7-activation)

## Suspected Fraud (By or Against the Agent)

1. Immediate report to Regional Coordinator via the priority support channel
2. Regional Coordinator escalates to the Agent Network Working Group within the response targets defined in [../MONITORING.md](../MONITORING.md#alerting)
3. If the agent is the suspected victim (e.g. impersonation targeting them), support includes helping the agent secure their account and alerting nearby agents to the pattern
4. If the agent is the suspected source, [risk-management.md](./risk-management.md#response-procedure-by-severity) governs the response

## Physical Safety Concerns

- Each region maintains a documented local emergency contact protocol (coordinated by the Regional Coordinator with local context — this varies by region and is maintained outside this public repository for safety reasons, consistent with not publishing information that could be misused)
- Agents are trained to prioritize personal safety over transaction completion or reconciliation in any safety-risk situation — no transaction is worth physical risk, and agents are explicitly told this during training (see [training-curriculum.md](./training-curriculum.md#session-31--customer-service--de-escalation))
- Post-incident: Regional Coordinator ensures the agent has access to appropriate support and conducts a review of whether any operational change (location, hours, procedure) would reduce future risk

## System Outage During a Transaction

1. If the dApp/API is unavailable mid-transaction, agents are trained to **not** complete the physical cash exchange until confirmation is visible in-app, even if this means asking the user to wait or return later
2. Once service resumes, any legitimately queued offline transaction (see [../DAPP.md](../DAPP.md#offline-first-concepts)) syncs automatically
3. Outages are tracked per [../MONITORING.md](../MONITORING.md) and communicated to affected agents

## Post-Incident Review

Every emergency-procedure activation is logged and reviewed by the Agent Network Working Group to identify whether the procedure itself needs revision — this document is treated as a living operational standard, updated through the same review process as other Agent Network policy (see [../GOVERNANCE.md](../GOVERNANCE.md#working-groups)).

## References

- [../AGENT_NETWORK.md](../AGENT_NETWORK.md)
- [risk-management.md](./risk-management.md)
- [../MONITORING.md](../MONITORING.md)
- [../SECURITY.md](../SECURITY.md#incident-response)
