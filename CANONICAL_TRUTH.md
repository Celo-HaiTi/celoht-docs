**CeloHT Canonical Truth**

«Status: Canonical
Scope: CeloHT ecosystem
Organization: Celo-HaiTi
Project: CeloHT
Last reviewed: September 16, 2026»

This document defines the canonical current-state facts for the CeloHT ecosystem.

All active CeloHT repositories, applications, documentation, websites, configuration references, and public materials should remain consistent with this document.

---

1. Identity

Organization: Celo-HaiTi

Project: CeloHT

Official GitHub organization:

https://github.com/Celo-HaiTi

Official website:

https://celoht.com/

Production dApp target:

https://app.celoht.com/

CeloHT is an open-source Haitian Web3 initiative focused on:

- Financial inclusion
- Blockchain education
- Digital payments
- Entrepreneurship
- Reforestation

CeloHT operates within the Celo ecosystem.

---

2. Founder

Founder: Johnny Dubic

Role: Founder

Founder status does not create unilateral control over CeloHT governance.

The Founder role must not be represented as an automatic executive, governance, treasury, or voting authority unless such authority is explicitly defined by the current governance system.

---

3. Governance

CeloHT uses a documented collective governance model.

Governance should prioritize:

- Transparent decision-making
- Defined roles and permissions
- Auditable actions
- Separation of responsibilities
- Protection against unilateral control
- Community participation
- Treasury accountability
- Security and operational controls

CeloHT does not have a native governance token.

Governance must not be described as token-weighted governance.

The Founder does not automatically possess unilateral governance authority.

All governance documentation must remain consistent with the current implementation and approved governance specification.

---

4. Token Policy

CeloHT does not issue or operate a native CeloHT token.

CeloHT is:

- Not a token
- Not a blockchain
- Not an investment product
- Not an investment vehicle

References to a hypothetical or proposed CeloHT token must not be presented as a current product or asset.

---

5. Blockchain

CeloHT operates within the Celo blockchain ecosystem.

Current network references

Testnet: Celo Sepolia

Celo Sepolia Chain ID:

"11142220"

Network configuration must always distinguish between:

- Development
- Testnet
- Production/Mainnet

No deployment should be described as production/mainnet unless it has been independently verified.

---

6. Assets

CELO

CELO is the native Celo network asset.

Within CeloHT, CELO may be used for:

- Network gas
- Governance-related blockchain transactions where applicable
- Other explicitly documented Celo network operations

USDm

USDm is the current stable-value payment asset referenced by CeloHT.

CeloHT documentation should use USDm for current payment/stable-value functionality.

Asset addresses must never be invented or copied into configuration without verification against an authoritative deployment source.

---

7. Wallet Support

CeloHT supports the following wallet connection paths:

- MiniPay
- Valora
- WalletConnect-compatible wallets

Valora

Valora is a recommended wallet option for CeloHT.

Valora is not affiliated with CeloHT.

CeloHT must not be described as supporting Valora exclusively.

MiniPay

MiniPay is a supported wallet environment where the dApp can use the available injected provider.

WalletConnect

WalletConnect-compatible wallets may connect through the CeloHT wallet connection layer.

The dApp should not expose unsupported or misleading wallet options.

---

8. dApp

The CeloHT dApp is an application, not a marketing landing page.

Primary product areas include:

- Wallet and financial functionality
- Education
- Agents
- Reforestation
- Activity/history where applicable

The dApp must not present simulated data, fake transactions, fake balances, fake impact metrics, or mock production activity as real user activity.

Current product scope

CeloHT's dApp focuses on:

Education • Agents • Reforestation

with financial and wallet functionality supporting the broader ecosystem.

An Impact Dashboard is not part of the current dApp product scope.

Documentation should not describe an Impact Dashboard as an active dApp product unless the product scope is formally changed.

---

9. Education

Education is a core CeloHT pillar.

The Education experience should support structured learning rather than functioning only as a collection of informational pages.

Where implemented, educational progress and completion records must be based on real application state.

No fabricated completion statistics should be presented as real user data.

---

10. Agent Ecosystem

Agents are a core CeloHT pillar.

The agent ecosystem may include:

- Agent registration
- Agent identity
- Agent verification
- Agent-assisted transactions
- Agent activity
- Agent-related governance or ecosystem functionality

Agent identity and verification must use real verification data where verification is claimed.

External identity/verification references must not be presented as verified unless the underlying verification state can actually be validated.

---

11. Reforestation

Reforestation is a core CeloHT pillar.

The reforestation system may support:

- Donations
- Tree financing
- Planting records
- Certificates
- Reforestation-related activity
- Verification and recordkeeping

Impact figures must only be presented as official current metrics when they have a defined source and verification methodology.

The dApp must not fabricate environmental impact.

---

12. Backend

The CeloHT backend provides application services required by the ecosystem.

Backend functionality must distinguish between:

- Local development
- Test/staging infrastructure
- Production infrastructure

Production claims require actual production infrastructure and successful runtime verification.

Environment variables must not contain invented credentials, fake URLs, placeholder production secrets, or unverified service endpoints.

---

13. Indexer

The CeloHT indexer is responsible for processing relevant blockchain events and making blockchain activity available to application services.

The indexer must support appropriate:

- RPC connectivity
- Database connectivity
- Event processing
- Backfill
- Confirmation handling
- Retry behavior
- Restart recovery
- Reorganization/reorg handling

An indexer being able to build successfully does not by itself establish production readiness.

Live infrastructure verification is required.

---

14. Database

Supabase is part of the CeloHT application infrastructure.

The canonical database migration chain must remain internally consistent.

Database migrations must:

- Have unique migration identifiers
- Preserve migration order
- Avoid conflicting numbering
- Be applied through the canonical Supabase migration process
- Avoid destructive changes without explicit review
- Preserve data integrity

Repositories must not create competing migration histories.

---

15. Authentication and Security

Security-sensitive configuration must use environment variables or secure secret management.

Never commit:

- API secrets
- Private keys
- Wallet seed phrases
- Service-role credentials
- Authentication secrets
- Production credentials

Authentication and authorization must fail closed when required security configuration is missing.

Administrative operations must require appropriate authorization.

---

16. Smart Contracts

CeloHT smart contracts must be treated as security-critical infrastructure.

Testnet deployment does not equal production readiness.

Before production/mainnet deployment, the required security gates include:

1. Independent security review/audit
2. Remediation of identified findings
3. Public audit/remediation record where appropriate
4. Secure treasury/governance controls
5. Testnet validation
6. Extended monitored testnet operation
7. Governance/operational sign-off
8. Final deployment verification

Contract addresses must always come from verified deployment manifests or authoritative deployment records.

---

17. Production Readiness

A repository passing:

- lint
- typecheck
- tests
- build

does not automatically mean the CeloHT ecosystem is production-ready.

Production readiness requires both:

Local verification

- Tests
- Typecheck
- Lint
- Build
- Dependency/security checks

External verification

- Live database
- Live backend
- Live indexer
- Real RPC
- Real wallet connection
- Real blockchain transactions where applicable
- End-to-end application flows
- Security review
- Operational monitoring
- Production configuration validation

A component should be marked NOT READY when required external infrastructure has not been verified.

This is preferable to claiming readiness based only on local tests.

---

18. Environment Configuration

Production credentials must never be invented.

Expected infrastructure configuration may include environment variables for:

- Supabase
- Authentication
- Redis/rate limiting
- Celo RPC
- Indexer
- Backend
- Wallet integrations

Actual values must only be added when the corresponding infrastructure exists and has been verified.

Documentation may describe required variable names without exposing their secret values.

---

19. Documentation Rules

All active documentation must use the current canonical facts defined in this document.

When a contradiction is discovered:

1. Identify the conflicting statement.
2. Compare it against this document.
3. Correct the active documentation.
4. Preserve factual historical records only where genuinely required.
5. Do not introduce unsupported claims.
6. Re-run repository-wide searches after corrections.

Documentation must not claim functionality that has not been implemented and verified.

Documentation must distinguish:

- Implemented
- Tested
- Deployed
- Verified
- Production-ready
- Planned
- Blocked by external dependency

These states must not be treated as interchangeable.

---

20. Roadmap Status

Roadmap items must use explicit status labels.

Recommended statuses:

- "COMPLETED"
- "IMPLEMENTED"
- "IN VALIDATION"
- "BLOCKED"
- "PLANNED"
- "DEFERRED"

A feature must not remain labeled "PLANNED" when it is already implemented and verified.

Likewise, an unverified production integration must not be labeled "COMPLETED" merely because source code exists.

---

21. Public Claims

Public-facing metrics and statements must be evidence-based.

This includes:

- Number of trees financed
- Number of trees planted
- Number of educated users
- Number of active agents
- Number of transactions
- Payment volume
- Partnerships
- Governance activity
- User activity

Each metric should have:

- A defined meaning
- A source
- A measurement period
- A verification method

If a metric cannot be verified, it must not be presented as a verified current metric.

---

22. Canonical URLs

Purpose| Canonical destination
Organization| https://github.com/Celo-HaiTi
Website| https://celoht.com/
Production dApp| https://app.celoht.com/

Repository documentation must use the canonical destinations above.

---

23. Synchronization Requirement

All active CeloHT repositories must remain synchronized with this document.

At minimum, synchronization must cover:

- Identity
- Founder role
- Governance
- Token policy
- Blockchain
- Assets
- Wallets
- dApp scope
- Website
- Deployment status
- Backend
- Indexer
- Database
- Security
- Production readiness
- Public metrics

A repository is considered synchronized only when its current documentation and implementation do not contradict the canonical facts defined here.

---

24. Source-of-Truth Hierarchy

When multiple documents disagree, use the following order of authority:

1. Verified on-chain deployment state
2. Current production implementation
3. Current approved governance specification
4. Current repository implementation
5. Canonical CeloHT documentation
6. Research/specification documents
7. Roadmaps and planning documents

Unverified assumptions must never override verified implementation or deployment state.

---

25. Change Control

Changes to canonical facts must be intentional.

A change to this document should include:

- What changed
- Why it changed
- Which repositories are affected
- Whether code changes are required
- Whether external verification is required

After a canonical change, affected repositories must undergo synchronization checks.

---

26. Final Rule

The CeloHT ecosystem should present one coherent current-state reality across:

- GitHub
- Documentation
- Website
- dApp
- Backend
- Indexer
- Database
- Smart contracts
- Governance
- Public communications

No repository should independently invent a different version of CeloHT's current architecture, governance, product scope, supported wallets, assets, deployment state, or production status.

Celo-HaiTi is the canonical organization identity.

CeloHT is the canonical project identity.

All current ecosystem materials must remain consistent with these facts.