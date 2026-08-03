# Monitoring & Observability

## What CeloHT Monitors

| System | What's monitored | Why |
|---|---|---|
| dApp/Website | Uptime, error rate, page load performance | User experience for a low-bandwidth audience |
| API | Response time, error rate, rate-limit hits | Reliability for dApp and SDK/CLI consumers |
| Smart contracts | Event logs (`AgentStatusChanged`, `GovernanceTransferred`) | Security and audit trail |
| Agent Network | Transaction velocity per agent, anomaly flags | Fraud prevention (see [AGENT_NETWORK.md](./AGENT_NETWORK.md#risk-management)) |
| Reforestation | Planting event logging consistency, monitoring check-in adherence | Data integrity for public metrics |

## Alerting

Critical alerts (API downtime, contract event anomalies, unusual agent transaction velocity) route to the Engineering Working Group on-call rotation, with defined response-time targets:

| Severity | Response target |
|---|---|
| Critical (service down, suspected fraud) | 15 minutes |
| High (degraded performance) | 2 hours |
| Medium (non-urgent bug) | Next business day |

## Dashboards

Internal engineering dashboards track system health; public dashboards (Impact, Tree, Treasury, Governance — see [DAPP.md](./DAPP.md#dashboards)) are a separate, user-facing observability layer focused on program transparency rather than system health.

## Logging Standards

- No personally identifiable information in logs
- No secrets or credentials in logs (see [SECURITY.md](./SECURITY.md#secrets-management))
- Structured logging (JSON) for machine parseability
- Log retention: 90 days for standard logs, extended retention for security-relevant audit logs per the Engineering Working Group's internal policy

## On-Chain Monitoring

Contract events (`AgentStatusChanged`, `GovernanceTransferred`) are monitored for unexpected patterns — e.g. rapid status changes outside normal verification workflow timing — as an additional fraud-detection layer alongside off-chain Agent Network monitoring.

## Incident Postmortems

Every incident affecting availability, security, or user funds triggers a public postmortem, consistent with [SECURITY.md](./SECURITY.md#incident-response).

## References

- [SECURITY.md](./SECURITY.md#incident-response)
- [DEPLOYMENT.md](./DEPLOYMENT.md)
- [AGENT_NETWORK.md](./AGENT_NETWORK.md#risk-management)
