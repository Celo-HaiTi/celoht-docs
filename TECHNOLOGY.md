# Technology

## Summary

A single-page overview of everything CeloHT is built on. For depth, follow the links to the dedicated document for each piece.

## Blockchain Layer

| Component | Role | Detail |
|---|---|---|
| Celo | Underlying blockchain | [CELO.md](./CELO.md) |
| cUSD | Payment asset (stable value) | [CUSD.md](./CUSD.md) |
| CELO (token) | Gas only, never promoted as a holding | [CELO.md](./CELO.md#gas--fees) |
| Valora | Recommended wallet | [VALORA.md](./VALORA.md) |

## Application Layer

| Component | Role | Detail |
|---|---|---|
| Official website | Public information platform | [WHITEPAPER.md](./WHITEPAPER.md#digital-ecosystem-website-and-dapp) |
| Official dApp | Operational platform (wallet connect, education, agent tools) | [DAPP.md](./DAPP.md) |
| Smart contracts | On-chain agent verification, minimal footprint | [SMART_CONTRACTS.md](./SMART_CONTRACTS.md) |
| API | Public/protected endpoints for programs, education, agents, impact | [API_REFERENCE.md](./API_REFERENCE.md) |

## Stack Details

- **Frontend:** Next.js, React, TypeScript, Tailwind CSS
- **Smart contracts:** Solidity, Hardhat
- **CI/CD:** GitHub Actions
- **Hosting:** GitHub (source), standard web hosting for the official website and dApp

## Why These Choices

Every technology choice here traces back to one constraint: the target user often has a lower-end Android device, limited data, and no prior blockchain experience. Celo's mobile-first design and cUSD's stability address the blockchain-layer half of that; Next.js/React with an offline-tolerant design (see [DAPP.md](./DAPP.md#offline-first-concepts)) addresses the application-layer half.

## What CeloHT Deliberately Doesn't Use

No proprietary or closed-source dependency for core financial functionality, no multi-chain complexity (see [SUPPORTED_NETWORKS.md](./SUPPORTED_NETWORKS.md#why-not-multi-chain)), and no token contract of any kind (see [NO_TOKEN_POLICY.md](./NO_TOKEN_POLICY.md)).

## References

- [ARCHITECTURE.md](./ARCHITECTURE.md)
- [SYSTEM_DESIGN.md](./SYSTEM_DESIGN.md)
- [DEVELOPER_GUIDE.md](./DEVELOPER_GUIDE.md)
- [SUPPORTED_NETWORKS.md](./SUPPORTED_NETWORKS.md)
