# Agent Operations Manual: Risk Management & Fraud Prevention

*Detailed operational companion to [../AGENT_NETWORK.md](../AGENT_NETWORK.md#risk-management).*

## Risk Categories

| Category | Examples |
|---|---|
| Transactional fraud | Fake transactions, coordinated multi-account abuse, transaction velocity anomalies |
| Impersonation | Fake agents (not on the [AgentRegistry](../SMART_CONTRACTS.md#agentregistry--reference-specification)), fake CeloHT "support" contacting users or agents |
| Coercion | Users pressured by third parties to complete transactions against their interest |
| Compliance drift | Agents not applying KYC consistently as transaction sizes grow |
| Physical security | Cash theft, agent safety incidents |

## Detection Mechanisms

### Automated
- Transaction velocity monitoring per agent (flags unusual spikes)
- Mandatory two-factor confirmation for cash-out above published thresholds
- On-chain event monitoring for irregular `AgentStatusChanged` patterns (see [../MONITORING.md](../MONITORING.md#on-chain-monitoring))

### Human
- Random compliance audits by Regional Coordinators (minimum quarterly per agent)
- Community reporting channel (in-app + contact@celoht.com)
- Reconciliation discrepancy review (daily cash/float reconciliation, see [training-curriculum.md](./training-curriculum.md#session-21--cash-handling-procedures))

## Response Procedure by Severity

| Severity | Example | Response |
|---|---|---|
| Low | Minor reconciliation discrepancy, first occurrence | Coaching conversation with Regional Coordinator, logged |
| Medium | Repeated KYC shortcuts, unclear reconciliation pattern | Formal warning, increased audit frequency, retraining |
| High | Confirmed fraudulent transaction, coordinated abuse | Immediate suspension (`setAgentStatus → Suspended`), investigation |
| Critical | Confirmed theft, impersonation of CeloHT, endangering users | Immediate offboarding (`setAgentStatus → Offboarded`), law enforcement referral where applicable, public advisory if user-facing risk exists |

## Offboarding Triggers

- Confirmed fraud or theft
- Repeated compliance violations after formal warning
- Impersonation or unauthorized representation of CeloHT
- Extended inactivity without communication (handled as a separate, non-punitive administrative offboarding)

## Community Protection Measures

- Public "Verified" badge tied directly to live on-chain status — a suspended or offboarded agent's badge disappears immediately, app-wide
- Published transaction limit thresholds so users know what to expect and can flag deviations
- Clear, well-publicized reporting channel (see [../SECURITY.md](../SECURITY.md#reporting-a-vulnerability))

## Agent-Facing Fraud Risks

Agents themselves are targets — impersonation scams targeting agents (e.g. fake "CeloHT compliance" requesting float transfers) are covered explicitly in [training-curriculum.md](./training-curriculum.md#session-23--fraud-recognition).

## Reporting & Transparency

Aggregate fraud metrics (incidents per 1,000 transactions) are published per [../AGENT_NETWORK.md](../AGENT_NETWORK.md#performance-metrics) and [../METRICS.md](../METRICS.md) — CeloHT reports this figure even when it's not flattering, consistent with [../METRICS.md](../METRICS.md#corrections-policy).

## References

- [../AGENT_NETWORK.md](../AGENT_NETWORK.md)
- [onboarding-and-verification.md](./onboarding-and-verification.md)
- [emergency-procedures.md](./emergency-procedures.md)
- [../SECURITY.md](../SECURITY.md)
