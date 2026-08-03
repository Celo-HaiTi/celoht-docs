# Architecture

## Purpose & Scope

This document describes CeloHT's technical architecture at the system level: how the dApp, smart contracts, Agent Network tooling, and educational platform relate to each other and to the underlying Celo blockchain. For implementation-level detail, see [DEVELOPER_GUIDE.md](./DEVELOPER_GUIDE.md), [SMART_CONTRACTS.md](./SMART_CONTRACTS.md), and [DAPP.md](./DAPP.md).

## System Overview

```
┌─────────────────────────────────────────────────────────────────┐
│                         User-Facing Layer                        │
│   Website (Next.js)   │   dApp (Next.js/React)   │  Agent App    │
└───────────┬───────────────────────┬───────────────────┬─────────┘
            │                       │                   │
            ▼                       ▼                   ▼
┌─────────────────────────────────────────────────────────────────┐
│                       Application/API Layer                      │
│     Auth · Education Content API · Impact/Metrics API            │
│     Agent Management API · Notification Service                  │
└───────────┬───────────────────────┬───────────────────┬─────────┘
            │                       │                   │
            ▼                       ▼                   ▼
┌─────────────────────────────────────────────────────────────────┐
│                    Wallet & Blockchain Layer                     │
│      Valora Wallet Connection                                    │
│      Celo Blockchain (cUSD payments, CELO gas)                   │
│      CeloHT Smart Contracts (see SMART_CONTRACTS.md)             │
└─────────────────────────────────────────────────────────────────┘
            │
            ▼
┌─────────────────────────────────────────────────────────────────┐
│                    Data & Impact Layer                           │
│   On-chain transaction data · Off-chain impact metrics store     │
│   Reforestation monitoring data · Education completion records   │
└─────────────────────────────────────────────────────────────────┘
```

## Design Principles

1. **Mobile-first.** Every layer is designed for low-end Android devices and inconsistent connectivity, common in the target user base.
2. **Non-custodial.** CeloHT never holds user funds directly — all transactions occur through the user's own Valora wallet.
3. **Minimal on-chain surface area.** Only what genuinely benefits from blockchain transparency (payment records, agent verification records) is on-chain; educational content and impact dashboards are off-chain for performance and cost reasons, with on-chain data as the verifiable source of truth for financial claims.
4. **Offline-tolerant.** Educational content and core UI are designed to degrade gracefully with intermittent connectivity (see [DAPP.md](./DAPP.md#offline-first-concepts)).
5. **Open by default.** All application and contract code is public; no closed-source dependency is used for core financial functionality.

## Components

### Website
Marketing, education entry point, impact reporting, and partner-facing content. Built with Next.js, TypeScript, and Tailwind CSS.

### dApp
The core transactional application — wallet connection, payments, agent dashboard, education dashboard. Full detail in [DAPP.md](./DAPP.md).

### Smart Contracts
On-chain logic for agent registration/verification records and transparent transaction logging. Full detail in [SMART_CONTRACTS.md](./SMART_CONTRACTS.md).

### Agent Tooling
Dashboards and mobile-friendly tools for Agent Network members to process cash-in/cash-out transactions and manage their verification status. See [AGENT_NETWORK.md](./AGENT_NETWORK.md#agent-dashboards).

### Impact/Metrics Pipeline
Aggregates on-chain transaction data with off-chain program data (training completions, trees planted) into the public metrics reported in [METRICS.md](./METRICS.md).

## Technology Stack

| Layer | Technology |
|---|---|
| Blockchain | Celo |
| Payment asset | cUSD |
| Gas asset | CELO |
| Wallets | Valora |
| Smart contracts | Solidity |
| Contract tooling | Hardhat |
| Frontend | Next.js, React, TypeScript |
| Styling | Tailwind CSS |
| Hosting/CI | GitHub, GitHub Actions |

## Security Architecture

Security considerations span smart contract design, wallet interaction safety, and agent verification — see [SECURITY.md](./SECURITY.md) for the full threat model and mitigations.

## Future Architecture Considerations

- GraphQL API layer alongside REST (see [API_REFERENCE.md](./API_REFERENCE.md#future-graphql))
- Expanded offline transaction queuing for low-connectivity regions
- GIS/satellite monitoring integration for Reforestation (see [REFORESTATION.md](./REFORESTATION.md#gis-and-satellite-monitoring-concepts))

## References

- [SMART_CONTRACTS.md](./SMART_CONTRACTS.md)
- [DAPP.md](./DAPP.md)
- [API_REFERENCE.md](./API_REFERENCE.md)
- [SECURITY.md](./SECURITY.md)
- [DEVELOPER_GUIDE.md](./DEVELOPER_GUIDE.md)

## Version History

See [CHANGELOG.md](./CHANGELOG.md).
