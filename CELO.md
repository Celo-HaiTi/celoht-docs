# Celo (Ecosystem Integration)

## What Celo Is

Celo is an independent, mobile-first blockchain network. CeloHT uses Celo as its payment infrastructure layer. **Celo Foundation does not operate, endorse, or control CeloHT** — see [LEGAL_STATUS.md](./LEGAL_STATUS.md#non-affiliation-disclaimer).

## Why CeloHT Uses Celo

- **Mobile-first design** — Celo was built for smartphone-based access, matching CeloHT's target users
- **Low, predictable transaction fees** — critical for everyday small-value transactions
- **Native stable-value asset (cUSD)** — see [CUSD.md](./CUSD.md) — reduces volatility exposure for payments
- **EVM compatibility** — allows CeloHT's smart contracts (see [SMART_CONTRACTS.md](./SMART_CONTRACTS.md)) to use standard, well-audited tooling (Solidity, Hardhat)

## Network Usage

| Environment | Purpose |
|---|---|
| Alfajores (testnet) | Development, testing, and staging — see [DEVELOPER_GUIDE.md](./DEVELOPER_GUIDE.md#debugging) |
| Mainnet | Production — only after the audit process in [SMART_CONTRACTS.md](./SMART_CONTRACTS.md#path-to-production) |

## Gas & Fees

Transaction fees on Celo are paid in **CELO**. CeloHT never asks users to acquire or hold CELO as an investment — see [NO_TOKEN_POLICY.md](./NO_TOKEN_POLICY.md). Where possible, the dApp abstracts gas handling to minimize the burden on non-technical users (see [DAPP.md](./DAPP.md)).

## Blockchain Explorers

CeloHT transaction and contract data is independently verifiable on public Celo block explorers, consistent with the transparency commitments in [GOVERNANCE.md](./GOVERNANCE.md#transparency-commitments). Specific explorer links for deployed CeloHT contracts are published once mainnet deployment occurs, per [SMART_CONTRACTS.md](./SMART_CONTRACTS.md#path-to-production).

## Cross-Border Payments

Celo's low-fee, stable-value transaction model supports CeloHT's relevance to diaspora communities sending remittances — a use case reflected in CeloHT's target user base (see [PARTNERS.md](./PARTNERS.md) and the master project context).

## References

- [CUSD.md](./CUSD.md)
- [VALORA.md](./VALORA.md)
- [ARCHITECTURE.md](./ARCHITECTURE.md)
- [LEGAL_STATUS.md](./LEGAL_STATUS.md)
