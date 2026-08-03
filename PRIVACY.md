# Privacy Policy

> Summary reference. The authoritative, legally binding version is published and kept current at [celoht.com/privacy](https://celoht.com).

## Principles

- **Data minimization** — CeloHT collects only what's needed to operate education tracking, agent verification, and impact reporting
- **No on-chain PII** — personally identifiable information is never written to the blockchain (see [SMART_CONTRACTS.md](./SMART_CONTRACTS.md#design-principles))
- **No data sale** — CeloHT does not sell user data to third parties, ever
- **Transparency** — this policy describes what's actually collected, not a broad catch-all permission

## What Is Collected

| Data | Purpose | Where stored |
|---|---|---|
| Wallet address | Transaction association, education progress tracking | Off-chain database, linked pseudonymously |
| Education progress | Personalization, impact metrics | Off-chain database |
| Agent identity (ID verification) | Regulatory compliance, fraud prevention | Off-chain, encrypted, access-restricted to compliance function |
| Agent transaction records | Fraud prevention, compliance, public aggregate metrics | Off-chain (detail) + on-chain (aggregate summary only, no PII) |
| Basic analytics (page views, error logs) | Reliability, product improvement | Off-chain, anonymized where feasible |

## What Is Not Collected

CeloHT does not collect wallet private keys or seed phrases (impossible by design — these never leave the user's wallet app), nor does it require government ID for basic dApp use (only Agent Network registration requires ID verification, per [AGENT_NETWORK.md](./AGENT_NETWORK.md#registration--verification)).

## User Rights

Users may request access to, correction of, or deletion of their off-chain personal data (subject to regulatory retention requirements for agent compliance records) by contacting contact@celoht.com.

## Data Sharing

Aggregate, de-identified impact data is shared publicly per [METRICS.md](./METRICS.md). Individual-level data is shared with third parties only where legally required (e.g. regulatory compliance requests) or with explicit user consent.

## Children's Privacy

CeloHT's education programs for schools (see [EDUCATION.md](./EDUCATION.md)) are delivered in partnership with educational institutions and do not involve direct individual data collection from minors outside of anonymized, aggregate program participation counts.

## Changes to This Policy

Material changes are announced at least 30 days in advance via the website and, where feasible, direct notification to registered agents and active users.

## References

- [SECURITY.md](./SECURITY.md)
- [LEGAL_STATUS.md](./LEGAL_STATUS.md#privacy)
- [TERMS.md](./TERMS.md)
