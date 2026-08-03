# System Design

> Complements [ARCHITECTURE.md](./ARCHITECTURE.md) with deeper design rationale and key data flows. Read `ARCHITECTURE.md` first for the system overview diagram.

## Key Design Decisions (Architecture Decision Records)

### ADR-001: Non-Custodial by Default
**Decision:** CeloHT never holds user funds; all transfers occur wallet-to-wallet.
**Rationale:** Removes an entire category of regulatory and security risk, and aligns with CeloHT's trust-first mission.
**Status:** Accepted, foundational (see [ARCHITECTURE.md](./ARCHITECTURE.md#design-principles)).

### ADR-002: Minimal On-Chain Data
**Decision:** Only agent verification status and optional transaction summaries live on-chain; personal data never does.
**Rationale:** Balances transparency (verifiable agent status, transaction integrity) against privacy and gas cost.
**Status:** Accepted (see [SMART_CONTRACTS.md](./SMART_CONTRACTS.md#design-principles)).

### ADR-003: No Native Token
**Decision:** No CeloHT token exists at any layer of the system.
**Rationale:** See [NO_TOKEN_POLICY.md](./NO_TOKEN_POLICY.md).
**Status:** Accepted, foundational — high bar to reverse.

### ADR-004: Governance-Gated Contract Administration
**Decision:** Administrative contract functions require multisig governance approval, never a single deployer key.
**Rationale:** Prevents single-point-of-failure control over agent verification, consistent with community governance principles.
**Status:** Accepted (see [SMART_CONTRACTS.md](./SMART_CONTRACTS.md#design-principles)).

## Data Flow: Agent Cash-In Transaction

```
User opens dApp → selects "Cash-In" → selects nearby verified agent
      │
      ▼
dApp queries AgentRegistry.isActiveAgent(agentAddress) [on-chain read]
      │
      ▼
User & Agent meet, agree amount → both confirm in-app
      │
      ▼
Agent initiates cUSD transfer from their wallet to user's wallet
      │
      ▼
User's wallet (Valora) prompts transaction signature
      │
      ▼
Transaction confirmed on Celo network → both apps show confirmation
      │
      ▼
Off-chain: transaction summary logged to Impact/Metrics pipeline (METRICS.md)
```

## Data Flow: Education Progress Tracking

```
User completes module in dApp → API POST /v1/education/progress/{moduleId}
      │
      ▼
Off-chain education platform record updated
      │
      ▼
Aggregated into public "people trained" metric (METRICS.md) on next sync cycle
```

## Scalability Considerations

- **Off-chain-first for non-financial data** (education progress, impact dashboards) to keep gas costs and on-chain load minimal
- **Regional data partitioning** anticipated as the Agent Network scales across regions (see [ROADMAP.md](./ROADMAP.md#medium-term-6–18-months))
- **CDN-cached public dashboards** (Tree Dashboard, Impact Dashboard) since these are read-heavy, publicly accessible, and don't require live blockchain reads for every page view

## Performance Standards

- API p95 response time target: under 500ms for read endpoints
- dApp initial load target: under 3 seconds on a mid-range Android device over 3G
- On-chain read caching: agent status cached client-side for 60 seconds to reduce redundant RPC calls

## References

- [ARCHITECTURE.md](./ARCHITECTURE.md)
- [SMART_CONTRACTS.md](./SMART_CONTRACTS.md)
- [API_REFERENCE.md](./API_REFERENCE.md)
- [METRICS.md](./METRICS.md)
