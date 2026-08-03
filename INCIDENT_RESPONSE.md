# Incident Response

*Companion to [SECURITY.md](./SECURITY.md#incident-response), with the step-by-step process.*

## What Counts as an Incident

Any event that compromises user funds, personal data, service availability, or the integrity of the CeloHT name (impersonation, fake-token scams) — see [THREAT_MODEL.md](./THREAT_MODEL.md) for the categories this covers.

## Response Steps

### 1. Detection
Via monitoring (see [MONITORING.md](./MONITORING.md)), a security report (see [SECURITY.md](./SECURITY.md#reporting-a-vulnerability)), or community report.

### 2. Triage (within 24 hours for critical reports)
Engineering side of the Maintainer Council assesses severity:

| Severity | Example |
|---|---|
| Critical | Confirmed fund loss, active fake-token scam gaining traction, contract exploit |
| High | Confirmed agent fraud, data exposure |
| Medium | Suspicious activity pattern, unconfirmed |
| Low | Isolated report, no confirmed impact yet |

### 3. Containment
- **Smart contracts:** pause governance-controlled admin functions if applicable — see [SMART_CONTRACTS.md](./SMART_CONTRACTS.md#agentregistry--reference-specification)
- **Agent fraud:** immediate suspension via [AgentRegistry](./SMART_CONTRACTS.md#agentregistry--reference-specification) — see [agent-network/emergency-procedures.md](./agent-network/emergency-procedures.md)
- **Brand impersonation:** public advisory, platform takedown requests where applicable
- **Infrastructure:** rate-limiting, temporary feature disablement, or rollback per [DEPLOYMENT.md](./DEPLOYMENT.md#rollback-procedure)

### 4. Remediation
Fix developed, tested, and reviewed following normal [CODING_STANDARDS.md](./CODING_STANDARDS.md) and review requirements — security fixes don't skip review, they get *faster* review.

### 5. Disclosure
A public postmortem is published for any incident affecting user funds, data, or trust — regardless of how minor it turns out to be. This is non-negotiable: see the transparency commitment in [GOVERNANCE.md](./GOVERNANCE.md#transparency-commitments).

## Postmortem Format

```markdown
# Incident: [short title]
## Timeline
## Impact
## Root Cause
## Remediation
## What We're Changing
```

## Roles During an Incident

- **Incident lead** — coordinates response, usually the Engineering-side Council member on call
- **Communications** — drafts and publishes any user-facing advisory, coordinated with [CONTACT.md](./CONTACT.md) channels
- **Technical responder(s)** — implement containment/remediation

## Communication Principles

- Say what's known, say what's still being investigated, and don't speculate publicly beyond that
- Never downplay user-facing risk to protect CeloHT's image — see [VOICE_AND_TONE.md](https://github.com/Celo-HT/Brand/blob/main/VOICE_AND_TONE.md) (Brand repository) for why this matters to CeloHT specifically

## References

- [SECURITY.md](./SECURITY.md)
- [THREAT_MODEL.md](./THREAT_MODEL.md)
- [agent-network/emergency-procedures.md](./agent-network/emergency-procedures.md)
- [MONITORING.md](./MONITORING.md)
