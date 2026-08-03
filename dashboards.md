# Agent Operations Manual: Agent Dashboards

*Detailed operational companion to [../AGENT_NETWORK.md](../AGENT_NETWORK.md#agent-dashboards) and [../DAPP.md](../DAPP.md#dashboards).*

## Dashboard Sections

### Overview
At-a-glance: current status (Active/Suspended/etc. per [AgentRegistry](../SMART_CONTRACTS.md#agentregistry--reference-specification)), recertification due date, today's transaction count and float summary.

### Transaction History
Full log of cash-in/cash-out transactions, filterable by date range, with each entry showing: timestamp, type, amount (cUSD), counterparty (pseudonymous), and confirmation status.

### Float & Liquidity
Current cUSD balance and estimated physical cash float, with a low-float alert threshold the agent can configure — prompting timely replenishment coordination with their Regional Coordinator.

### Compliance Status
Training completion, last audit date and result, and any open flags — visible to the agent for full transparency, not hidden administrative data.

### Earnings Summary
Transparent breakdown of per-transaction fees earned (see [../AGENT_NETWORK.md](../AGENT_NETWORK.md#revenue-model)), by period, matching the published fee schedule exactly — agents can independently verify they're being paid correctly.

## Field Operation Workflow (Typical Day)

1. Agent opens dashboard, reviews float status
2. User arrives, agent initiates cash-in/cash-out flow per [../USER_GUIDE.md](../USER_GUIDE.md#using-an-agent-cash-in--cash-out)
3. Dashboard shows real-time pending confirmation state
4. Transaction completes, appears immediately in Transaction History
5. End of day: agent reconciles physical cash against dashboard float summary (see [training-curriculum.md](./training-curriculum.md#session-21--cash-handling-procedures))

## Regional Coordinator View

Coordinators have an aggregated view across their assigned agents: float replenishment needs, compliance audit scheduling, and cohort-level performance metrics — feeding into [../METRICS.md](../METRICS.md#core-metrics).

## Mobile & Offline Considerations

Dashboard is optimized for the same offline-tolerant design as the general dApp (see [../DAPP.md](../DAPP.md#offline-first-concepts)) — transaction confirmations queue and sync automatically, with clear pending-state indicators so agents are never uncertain whether a transaction fully processed.

## Accessibility

Agent dashboards meet the same [ACCESSIBILITY.md](../ACCESSIBILITY.md) standard as the general dApp — agents are core users, not an edge case, given many spend extended periods using this interface daily.

## References

- [../AGENT_NETWORK.md](../AGENT_NETWORK.md)
- [../DAPP.md](../DAPP.md)
- [onboarding-and-verification.md](./onboarding-and-verification.md)
