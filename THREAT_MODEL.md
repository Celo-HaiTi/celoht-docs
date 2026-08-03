# Threat Model

*Companion to [SECURITY.md](./SECURITY.md), with more detail on how each threat is analyzed.*

## Assets Being Protected

- User funds (held in users' own non-custodial wallets, not by CeloHT — see [ARCHITECTURE.md](./ARCHITECTURE.md#design-principles))
- User trust in the CeloHT name and brand
- Agent Network integrity (accurate verification status)
- Personal data collected per [PRIVACY.md](./PRIVACY.md)
- CeloHT's own infrastructure (API, website, repositories)

## Threat Actors

| Actor | Motivation | Typical method |
|---|---|---|
| Phishing/impersonation scammers | Financial fraud against users | Fake "CeloHT" sites, fake token offers, seed-phrase requests |
| Malicious agent candidates | Direct financial fraud | False credentials at registration, transaction manipulation |
| Opportunistic contributors | Reputation, curiosity, or low-stakes vandalism | Malicious PRs, spam issues |
| Sophisticated attackers | Smart contract exploitation | Reentrancy, access-control bypass, once contracts are live |
| Supply-chain attackers | Broad compromise via dependencies | Malicious npm packages, compromised CI actions |

## Threats by Category

### Impersonation & Brand Misuse
**Threat:** third party creates a fake "CeloHT token," phishing site, or impersonation account.
**Mitigation:** [NO_TOKEN_POLICY.md](./NO_TOKEN_POLICY.md) as a bright-line public reference; active community reporting channel; consistent, repeated public messaging that CeloHT has no token.

### Wallet & Seed-Phrase Phishing
**Threat:** attacker tricks a user into revealing their seed phrase.
**Mitigation:** absolute rule taught in [education/module-04-wallet-safety.md](./education/module-04-wallet-safety.md): CeloHT never asks for it, under any circumstance.

### Smart Contract Vulnerabilities
**Threat:** reentrancy, access-control bypass, or logic errors in deployed contracts.
**Mitigation:** minimal on-chain logic, mandatory third-party audit before mainnet, governance-gated admin functions — see [SMART_CONTRACTS.md](./SMART_CONTRACTS.md#path-to-production).

### Agent Fraud
**Threat:** a registered agent commits fraud against users, or a fraudster impersonates an agent.
**Mitigation:** on-chain [AgentRegistry](./SMART_CONTRACTS.md#agentregistry--reference-specification) verification, mandatory training and re-certification, transaction limits and velocity monitoring — see [agent-network/risk-management.md](./agent-network/risk-management.md).

### Supply Chain
**Threat:** a compromised dependency introduces malicious code.
**Mitigation:** dependency scanning in CI, committed lockfiles, maintainer review of new dependencies — see [SECURITY.md](./SECURITY.md#supply-chain-security).

### Data Exposure
**Threat:** personal data (agent ID verification, user records) exposed through a breach.
**Mitigation:** data minimization, no on-chain PII, encrypted storage for sensitive off-chain records — see [PRIVACY.md](./PRIVACY.md).

## Out of Scope (For Now)

Threats specific to a live mainnet smart contract deployment (MEV, complex economic attacks) are out of scope until contracts actually reach mainnet — see [SMART_CONTRACTS.md](./SMART_CONTRACTS.md#path-to-production). Revisit this model before that happens, not after.

## Review Cadence

This threat model is reviewed whenever a new major feature ships (especially anything touching funds or agent verification) and at minimum annually, coordinated by the Engineering side of the Maintainer Council (see [WORKING_GROUPS.md](./WORKING_GROUPS.md)).

## References

- [SECURITY.md](./SECURITY.md)
- [SMART_CONTRACTS.md](./SMART_CONTRACTS.md)
- [agent-network/risk-management.md](./agent-network/risk-management.md)
- [PRIVACY.md](./PRIVACY.md)
