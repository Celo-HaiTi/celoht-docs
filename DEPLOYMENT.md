# Deployment

## Environments

| Environment | Purpose | Network |
|---|---|---|
| Local | Development | Hardhat local network |
| Staging | Pre-release testing | Celo Alfajores (testnet) |
| Production | Live | Celo Mainnet |

## Website & dApp Deployment

Deployed via CI/CD on merge to `main` (staging) with manual promotion to production, per [DEVELOPER_GUIDE.md](./DEVELOPER_GUIDE.md#cicd).

```bash
# Staging (automatic on merge to main)
# Production (manual promotion, requires approval)
npm run build
npm run deploy:production
```

## Smart Contract Deployment

Follows the mandatory process in [SMART_CONTRACTS.md](./SMART_CONTRACTS.md#path-to-production) — audit and 90-day monitored testnet trial required before mainnet.

```bash
# Testnet deployment (Alfajores)
npx hardhat run scripts/deploy.js --network alfajores

# Mainnet deployment — requires Maintainer Council sign-off per GOVERNANCE.md
npx hardhat run scripts/deploy.js --network celo
```

Deployment scripts must output the deployed contract address and transaction hash to a version-controlled deployment log, never left only in a deployer's local terminal history.

## Rollback Procedure

- **Website/dApp:** redeploy the previous known-good build via the hosting platform's release history
- **Smart contracts:** contracts are not directly "rolled back" (immutable once deployed); instead, the governance multisig can pause administrative functions (see [SMART_CONTRACTS.md](./SMART_CONTRACTS.md#agentregistry--reference-specification)) while a fix is prepared and deployed as a new, audited version

## Configuration Management

Environment-specific configuration (API URLs, network settings) is managed per environment and never hardcoded — see [DEVELOPER_GUIDE.md](./DEVELOPER_GUIDE.md#environment-variables) and [SECURITY.md](./SECURITY.md#secrets-management).

## Pre-Deployment Checklist

- [ ] All CI checks passing (lint, typecheck, tests)
- [ ] Security checklist completed (see [SECURITY.md](./SECURITY.md#security-checklist-pre-release))
- [ ] Changelog updated (see [CHANGELOG.md](./CHANGELOG.md))
- [ ] For contracts: audit and testnet trial requirements met

## References

- [DEVELOPER_GUIDE.md](./DEVELOPER_GUIDE.md)
- [SMART_CONTRACTS.md](./SMART_CONTRACTS.md#path-to-production)
- [MONITORING.md](./MONITORING.md)
- [SECURITY.md](./SECURITY.md)
