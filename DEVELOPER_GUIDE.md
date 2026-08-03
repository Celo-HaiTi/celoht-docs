# Developer Guide

## Purpose

This guide helps developers set up, understand, and contribute to CeloHT's codebase across the website, dApp, and smart contracts.

## Local Setup

```bash
git clone https://github.com/Celo-HT/dApp.git
cd dApp
npm install
cp .env.example .env.local   # fill in required values, see below
npm run dev
```

### Smart Contract Development

```bash
git clone https://github.com/Celo-HT/Smart-Contracts.git
cd Smart-Contracts
npm install
npx hardhat compile
npx hardhat test
```

> These commands require network access to install dependencies from the npm registry — they cannot be executed inside a network-isolated environment. Run them in your own local or CI environment before opening a pull request.

### Environment Variables

```
NEXT_PUBLIC_CELO_NETWORK=alfajores        # alfajores (testnet) or mainnet
NEXT_PUBLIC_API_BASE_URL=https://api.celoht.com/v1
WALLETCONNECT_PROJECT_ID=<your-project-id>
```

Never commit `.env.local` or any file containing real credentials — see [SECURITY.md](./SECURITY.md#secrets-management).

## Project Structure

```
dApp/
├── app/                 Next.js App Router pages
├── components/          Shared React components
├── lib/
│   ├── wallet/          Valora connection logic
│   ├── api/             API client (see API_REFERENCE.md)
│   └── contracts/       Contract ABI bindings
├── public/
├── styles/
└── tests/
```

## Development Workflow

1. Fork the repository (external contributors) or branch directly (maintainers)
2. Branch naming: `feature/short-description`, `fix/short-description`, `docs/short-description`
3. Write code + tests together — no PR is merged without corresponding test coverage for new logic
4. Run `npm run lint`, `npm run typecheck`, and `npm test` locally before opening a PR
5. Open a PR referencing the related issue

## Branch Strategy

- `main` — always deployable
- `develop` — integration branch for the next release
- Feature branches merge into `develop` via PR; `develop` merges into `main` on release per [CHANGELOG.md](./CHANGELOG.md) semantic versioning

## Testing

- **Unit tests:** Jest, colocated with source files (`*.test.ts`)
- **Smart contract tests:** Hardhat + Chai — see [SMART_CONTRACTS.md](./SMART_CONTRACTS.md#reference-test-suite-hardhat--chai--illustrative)
- **Integration tests:** covering wallet connection flows and API integration
- **End-to-end tests:** Playwright, covering critical user flows (onboarding, send/receive, agent cash-in/cash-out)
- **Accessibility tests:** automated axe-core checks in CI plus manual screen-reader testing before major releases

## CI/CD

GitHub Actions runs on every PR: lint, typecheck, unit tests, and smart contract tests (where applicable). Merges to `main` trigger deployment to staging; production deployment requires a manual approval gate per [GOVERNANCE.md](./GOVERNANCE.md).

## Code Review

Every PR requires at least one maintainer approval. PRs touching smart contracts or the Agent Network compliance logic require two maintainer approvals — the same elevated review bar CeloHT applies to sensitive changes across all its repositories (see the [Brand repository's CONTRIBUTING.md](https://github.com/Celo-HT/Brand/blob/main/CONTRIBUTING.md) for the equivalent policy there).

## Debugging

- Local blockchain interactions: use the Celo Alfajores testnet (`NEXT_PUBLIC_CELO_NETWORK=alfajores`) — never test against mainnet with real funds
- Wallet connection issues: check WalletConnect project configuration and browser console for signature rejection errors

## Release Workflow

CeloHT follows [Semantic Versioning](https://semver.org/): `MAJOR.MINOR.PATCH`. Releases are tagged on `main`, with release notes published in each repository's `CHANGELOG.md`.

## SDK Usage

```javascript
// Illustrative — see the celoht-sdk repository for current package status
import { CeloHT } from '@celoht/sdk';

const client = new CeloHT({ network: 'alfajores' });
const modules = await client.education.listModules();
const nearbyAgents = await client.agents.nearby({ lat: 18.5944, lng: -72.3074, radiusKm: 10 });
```

## Coding Standards

- TypeScript strict mode required for all frontend code
- Solidity: NatSpec comments required on all public/external functions (see [SMART_CONTRACTS.md](./SMART_CONTRACTS.md) for style example)
- No secrets, private keys, or credentials in source code — ever
- All user-facing strings go through the localization layer, never hardcoded

## References

- [ARCHITECTURE.md](./ARCHITECTURE.md)
- [SMART_CONTRACTS.md](./SMART_CONTRACTS.md)
- [API_REFERENCE.md](./API_REFERENCE.md)
- [SECURITY.md](./SECURITY.md)
