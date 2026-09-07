# Security Policy

## Reporting a Vulnerability

Email **contact@celoht.com** with subject line `[SECURITY]`. Do not open a public GitHub issue for security vulnerabilities. We aim to acknowledge reports within 5 business days.

Please include: affected repository/component, steps to reproduce, potential impact, and your suggested severity.

## Responsible Disclosure

We ask researchers to give CeloHT a reasonable window to address a reported issue (typically 90 days) before public disclosure, and to avoid accessing, modifying, or deleting data beyond what's necessary to demonstrate the issue.

## Threat Model

| Area | Key threats | Mitigations |
|---|---|---|
| Smart contracts | Reentrancy, access control bypass, governance key compromise | Minimal on-chain logic, multisig governance, mandatory audit before mainnet (see [SMART_CONTRACTS.md](./SMART_CONTRACTS.md#path-to-production)) |
| Wallet interaction | Phishing, malicious QR codes, fake dApp domains | Domain verification guidance in education content, wallet-native transaction confirmation review |
| Agent Network | Agent impersonation, fraudulent transactions | On-chain AgentRegistry verification, transaction limits, two-factor confirmation (see [AGENT_NETWORK.md](./AGENT_NETWORK.md#risk-management)) |
| Brand/identity | Fake "CeloHT token" scams, impersonation | [NO_TOKEN_POLICY.md](./NO_TOKEN_POLICY.md), active monitoring, public reporting channel |
| API/infrastructure | Credential leakage, rate-limit abuse, injection | Secrets management practices below, rate limiting (see [API_REFERENCE.md](./API_REFERENCE.md#rate-limits)) |

## Wallet Safety

CeloHT never asks users for their seed phrase, private key, or wallet password, under any circumstance, through any channel. Any communication requesting this is fraudulent — see [Reporting Violations](./NO_TOKEN_POLICY.md#reporting-violations).

## Data and service boundaries

- **Authentication:** the backend uses wallet nonce/signature authentication for wallet-linked sessions; server-side session handling is owned by `celoht-backend`. A public dApp connection alone is not an authenticated application session.
- **Authorization:** roles are re-read server-side and enforced by the backend; client-side role labels and dashboard visibility are not authorization.
- **KYC privacy:** KYC and identity evidence are user data, not on-chain data and not public impact metrics. Store and review them only through the provisioned backend/Supabase controls.
- **Secrets:** service-role keys, RPC credentials, signing keys, and deployment secrets remain server-side and outside the dApp/admin browser bundle. Never commit them.
- **Database security:** Supabase RLS, ownership boundaries, migrations, backups, and immutable audit logs are required. The indexer writes only indexer-owned tables; the backend must not rewrite indexed provenance.
- **Derived metrics:** dashboards must label whether a value is on-chain, indexed, database-owned, user-submitted, or derived. Missing data is `UNAVAILABLE`, not zero.

## Smart Contract Security

- Contract-specific custody, roles, and administrative controls must be checked against the canonical deployed source and manifest; this documentation does not certify a multisig or pause mechanism.
- No CeloHT native token exists. USDm is the settlement asset and CELO is the gas/network asset.
- Mandatory third-party audit before any mainnet deployment beyond testnet
- Public audit reports and remediation tracking

## Incident Response

1. **Detection** — via monitoring, bug bounty reports, or community reports
2. **Triage** — Engineering Working Group assesses severity within 24 hours for critical reports
3. **Containment** — for smart contracts, use only controls actually exposed by the deployed contract; for the dApp/API, this may mean rate-limiting or temporary feature disablement
4. **Remediation** — fix developed, tested, and reviewed
5. **Disclosure** — public post-mortem published for any incident affecting user funds, data, or trust, regardless of severity

## Supply Chain Security

- Dependency updates reviewed via automated scanning (Dependabot or equivalent) in CI
- No dependency is added without a maintainer reviewing its purpose and maintenance status
- Lockfiles (`package-lock.json`) are committed and required to match `package.json` in CI

## Secrets Management

- No credentials, API keys, or private keys are committed to any repository
- Environment-specific secrets are managed via the hosting platform's secret storage, never in `.env` files committed to git
- Rotation procedure documented internally for the Engineering Working Group; compromised secrets are rotated immediately upon suspicion, not confirmation

## Security Checklist (Pre-Release)

- [ ] Dependency scan clean or exceptions documented
- [ ] Lint and typecheck passing
- [ ] No secrets detected in diff (automated scan + manual review)
- [ ] Smart contract changes reviewed by two maintainers minimum
- [ ] Accessibility regression check passed

## Audit Readiness

Before requesting an external audit, the Engineering Working Group ensures: complete NatSpec documentation, 100% branch coverage on critical contract logic in the test suite, and a written specification matching the deployed code exactly (this document is that specification for `AgentRegistry` — see [SMART_CONTRACTS.md](./SMART_CONTRACTS.md)).

## References

- [SMART_CONTRACTS.md](./SMART_CONTRACTS.md)
- [NO_TOKEN_POLICY.md](./NO_TOKEN_POLICY.md)
- [AGENT_NETWORK.md](./AGENT_NETWORK.md#risk-management)
- [GOVERNANCE.md](./GOVERNANCE.md)
- [PRODUCTION_READINESS.md](./PRODUCTION_READINESS.md)
- [OPERATIONS_RUNBOOKS.md](./OPERATIONS_RUNBOOKS.md)
