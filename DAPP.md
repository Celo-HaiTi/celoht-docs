# dApp

> **Status:** This document specifies the intended design of the CeloHT dApp. Implementation status of any given feature should be verified against the `celoht-dapp` repository's own README and CHANGELOG, not assumed from this specification alone.

## Purpose

The CeloHT dApp is the core transactional interface connecting users, agents, and CeloHT's on-chain and off-chain systems.

## User Flows

### New User Onboarding
1. Landing screen with plain-language explanation of what CeloHT is (and the No-Token Policy)
2. Wallet connection (Valora) — see [Wallet Connection](#wallet-connection)
3. Optional guided education mini-module before first transaction
4. Nearest verified agent lookup (for cash-in) or direct payment flow

### Sending / Receiving cUSD
1. User selects "Send" or "Receive"
2. For "Receive": QR code generated, displayable offline once loaded
3. For "Send": QR scan or manual address entry, amount entry in both cUSD and local currency equivalent, confirmation screen showing exact fee (gas in CELO), wallet-app signature
4. Transaction status shown with on-chain confirmation tracking

### Agent Interaction
1. User locates nearest verified agent via the agent directory (cross-referenced against [AgentRegistry](./SMART_CONTRACTS.md#agentregistry--reference-specification) on-chain status)
2. Cash-in or cash-out request initiated in-app
3. Agent confirms via their own dashboard; both parties see matched confirmation before cash/digital exchange

## Authentication

- Wallet-based authentication (signature challenge) — no separate CeloHT password/account system for basic use
- Optional profile layer for education progress tracking, secured via the connected wallet address

## Wallet Connection

- **Valora:** WalletConnect-based integration

## Dashboards

| Dashboard | Audience | Shows |
|---|---|---|
| Agent Dashboard | Agents | Transaction history, float status, compliance/certification status |
| Education Dashboard | All users | Module progress, certificates, recommended next content |
| Tree Dashboard | All users, public | Reforestation map, planting events, survival rates |
| Impact Dashboard | All users, public | Aggregated CeloHT-wide metrics (see [METRICS.md](./METRICS.md)) |
| Treasury Dashboard | Public | Funding sources and utilization per [GOVERNANCE.md](./GOVERNANCE.md#funding-governance) |
| Governance Dashboard | Public | Open RFCs, Maintainer Council composition, recent decisions |

## Notifications

Transaction confirmations, agent verification status changes, and education module reminders — delivered via in-app notification and, where available, SMS fallback for users without reliable data connectivity.

## Offline-First Concepts

- Education content cached locally after first load
- "Receive" QR codes generated and displayable without a live connection
- Transactions queued locally and submitted automatically upon reconnection, with clear pending-state UI so users are never uncertain whether a transaction was sent

## Accessibility

Follows WCAG 2.2 AA at minimum — see the CeloHT Brand repository's `COLOR_SYSTEM.md` and `TYPOGRAPHY.md` for the underlying design tokens. Screen-reader support and scalable text are required, not optional, given the target user base includes first-time smartphone users.

## Localization

Full Haitian Creole localization is the default language, with English and French available. All localization strings are managed centrally to avoid partial-translation states.

## API Integrations

The dApp consumes the endpoints defined in [API_REFERENCE.md](./API_REFERENCE.md) for education content, impact metrics, and agent directory data; on-chain reads/writes go directly to the Celo network per [ARCHITECTURE.md](./ARCHITECTURE.md).

## Security & Performance

See [SECURITY.md](./SECURITY.md) for the dApp-specific threat model (wallet phishing, fake agent impersonation, transaction confirmation spoofing) and [ARCHITECTURE.md](./ARCHITECTURE.md) for performance/scalability design principles.

## References

- [ARCHITECTURE.md](./ARCHITECTURE.md)
- [SMART_CONTRACTS.md](./SMART_CONTRACTS.md)
- [API_REFERENCE.md](./API_REFERENCE.md)
- [AGENT_NETWORK.md](./AGENT_NETWORK.md#agent-dashboards)
