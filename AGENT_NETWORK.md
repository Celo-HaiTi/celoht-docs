# Agent Network

> **Current status:** the first cohort of community agents (Léogâne) is being recruited and trained as of this writing — see [ROADMAP.md](./ROADMAP.md#phase-1--foundation-2026-q2q3). The lifecycle, training, and operational detail below (including [`agent-network/`](./agent-network/)) describe the designed, standard process this first cohort and all future cohorts follow — not an already-mature, multi-region network.

## Purpose

The Agent Network is CeloHT's human bridge between cash economies and digital payments. Agents are trained, verified community members who provide cash-in/cash-out services, wallet onboarding, and ongoing local support.

## Agent Lifecycle

1. **Recruitment** — candidates identified through community nomination or application, prioritizing existing trusted local figures (shop owners, community leaders)
2. **Registration** — identity verification and application submitted through the Agent onboarding flow (see [DAPP.md](./DAPP.md#agent-dashboard))
3. **Verification** — background and identity checks per the compliance process below
4. **Training** — mandatory training covering the modules listed under [Training Curriculum](#training-curriculum)
5. **Certification** — agents must pass a competency assessment before activation
6. **Operations** — active agent status, subject to ongoing performance and compliance monitoring
7. **Renewal / Offboarding** — periodic re-certification; offboarding for inactivity, policy violation, or voluntary exit

**Full step-by-step operational procedure:** [agent-network/onboarding-and-verification.md](./agent-network/onboarding-and-verification.md)

## Registration & Verification

- Government-issued ID verification
- Physical location verification (agents operate from a known, fixed community location)
- Reference check from at least two existing community members or partner organizations
- Digital identity record created and linked to the agent's on-chain verification status (see [SMART_CONTRACTS.md](./SMART_CONTRACTS.md#agent-registry))

## Training Curriculum

**Full 3-day training syllabus:** [agent-network/training-curriculum.md](./agent-network/training-curriculum.md)

- CeloHT mission, pillars, and No-Token Policy (agents must be able to correctly explain this to users)
- Wallet operations (Valora) and transaction verification
- Cash handling procedures and reconciliation
- Fraud recognition and prevention (see [Risk Management](#risk-management))
- Customer service and conflict de-escalation
- Digital security and safe device practices
- Reporting procedures for suspicious activity or emergencies

## Operations

### Core Services
- **Cash-in:** converting physical cash to cUSD for a user
- **Cash-out:** converting a user's cUSD to physical cash
- **Wallet onboarding:** helping new users set up Valora safely
- **Community liquidity:** agents maintain a cUSD/cash float to serve their community reliably

### Agent Dashboards
Agents access a mobile-optimized dashboard (see [DAPP.md](./DAPP.md#agent-dashboard)) showing: transaction history, current float/liquidity status, compliance status, and training/certification status. **Full dashboard specification:** [agent-network/dashboards.md](./agent-network/dashboards.md)

### Regional Coordinators
Coordinators support clusters of agents within a region — handling escalations, float replenishment logistics, and local training delivery. Coordinators report to the Agent Network Working Group (see [GOVERNANCE.md](./GOVERNANCE.md#working-groups)).

## Risk Management

**Full risk management and fraud-response procedures:** [agent-network/risk-management.md](./agent-network/risk-management.md)

### Fraud Prevention
- Transaction limits and velocity monitoring per agent
- Mandatory two-factor confirmation for cash-out transactions above defined thresholds
- Random compliance audits
- Community reporting channel for suspicious agent behavior

### Compliance
- Agents operate under published transaction limits aligned with applicable local financial regulation — see [LEGAL_STATUS.md](./LEGAL_STATUS.md)
- Know-your-customer (KYC) practices proportionate to transaction size
- Full audit trail for every transaction, linking on-chain records to agent identity

## Revenue Model

Agents earn a transparent, published per-transaction fee for cash-in/cash-out services, denominated and paid in cUSD. This fee structure is published to prevent both agent exploitation and predatory fee practices toward users. Agents do **not** receive token-based compensation of any kind — see [NO_TOKEN_POLICY.md](./NO_TOKEN_POLICY.md).

## Expansion Model

New regions are onboarded by first identifying and training a Regional Coordinator, who then recruits and trains local agents using the standard curriculum, ensuring consistent quality as the network grows.

## Performance Metrics

Active agents, transaction volume per agent, user satisfaction (post-transaction survey), fraud incidents per 1,000 transactions, and agent retention rate. See [METRICS.md](./METRICS.md).

## Field Operations & Emergency Procedures

**Full emergency procedures manual:** [agent-network/emergency-procedures.md](./agent-network/emergency-procedures.md)

Agents are equipped with a documented emergency procedure for: device loss/theft (immediate account freeze via dashboard), suspected fraud (immediate reporting channel to Regional Coordinator), and physical safety concerns (local emergency contact protocol, maintained per region).

## Support Systems

Agents have access to a dedicated support channel (see [Community](./PARTNERS.md)) separate from general user support, staffed by the Agent Network Working Group.

## References

- [SMART_CONTRACTS.md](./SMART_CONTRACTS.md#agent-registry) — on-chain agent verification record
- [SECURITY.md](./SECURITY.md) — fraud and security threat model
- [EDUCATION.md](./EDUCATION.md) — agent training as an education delivery channel
- [METRICS.md](./METRICS.md) — Agent Network performance reporting
