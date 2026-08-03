# Metrics & Impact Reporting

## Philosophy

CeloHT measures success through outcomes, not financial performance — because CeloHT is not a financial product. Every metric below has a defined methodology to prevent vanity-metric inflation.

## Core Metrics

| Metric | Definition | Source |
|---|---|---|
| People trained | Individuals completing at least one full education module with passing assessment | Off-chain education platform records |
| Active learners | Users with education activity in the last 30 days | Off-chain education platform records |
| Wallets created | Unique Valora wallets connected through CeloHT onboarding flow | dApp analytics, deduplicated by wallet address |
| Active agents | Agents with `Active` on-chain status per [AgentRegistry](./SMART_CONTRACTS.md#agentregistry--reference-specification) and at least one transaction in the last 30 days | On-chain + off-chain agent activity log |
| Transactions / cUSD volume | Count and total value of cUSD transactions processed via the Agent Network | On-chain transaction data |
| Communities reached | Distinct communities (defined at the commune/locality level) with at least one active agent or completed education program | Agent Network + Education records, cross-referenced |
| Trees planted | Logged planting events, GPS-tagged | Reforestation program records |
| Trees surviving | Trees confirmed alive at the 18-month monitoring check | Community + spot-verified monitoring, see [REFORESTATION.md](./REFORESTATION.md#methodology) |
| Partner organizations | Organizations with an active, signed partnership agreement | [PARTNERS.md](./PARTNERS.md) |
| GitHub contributors | Unique contributors with at least one merged PR across CeloHT repositories | GitHub |

## Methodology Principles

1. **Survival over vanity.** "Trees planted" alone is not reported without the paired survival rate — planting without survival is not impact.
2. **Deduplication.** Wallet and user counts are deduplicated by wallet address, not by app session or download count.
3. **Independent spot-verification.** Reforestation and agent activity metrics are subject to periodic independent spot-checks against community self-reporting, with discrepancies published, not hidden.
4. **No financial-return metrics.** CeloHT does not report or promote any metric resembling investment return, token price, or asset appreciation, consistent with [NO_TOKEN_POLICY.md](./NO_TOKEN_POLICY.md).

## Reporting Cadence

- **Public dashboard:** updated continuously (see [DAPP.md](./DAPP.md#dashboards)), reflecting near-real-time on-chain data and periodically synced off-chain data
- **Quarterly impact report:** published narrative report covering all core metrics, methodology notes, and any corrections to previously reported figures
- **Annual report:** comprehensive report including governance, funding, and full-year pillar outcomes

## Data Access

Aggregate metrics are available via the public API — see [API_REFERENCE.md](./API_REFERENCE.md#impact-metrics). Underlying on-chain data is independently verifiable on the Celo block explorer, consistent with CeloHT's transparency commitment (see [GOVERNANCE.md](./GOVERNANCE.md#transparency-commitments)).

## Corrections Policy

If a previously reported metric is found to be inaccurate, CeloHT publishes a correction in the next quarterly report and in [CHANGELOG.md](./CHANGELOG.md), rather than silently revising historical figures.

## References

- [REFORESTATION.md](./REFORESTATION.md#impact-measurement)
- [AGENT_NETWORK.md](./AGENT_NETWORK.md#performance-metrics)
- [EDUCATION.md](./EDUCATION.md#measuring-effectiveness)
- [GOVERNANCE.md](./GOVERNANCE.md#transparency-commitments)
