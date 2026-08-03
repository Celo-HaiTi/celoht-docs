# Project Structure

## Repository Map (Organization-Wide)

```
github.com/Celo-HT/
├── CeloHT/                 Meta/wiki repository, high-level org profile
├── Docs/                   This repository — full documentation
├── Brand/                  Visual identity, logo, brand guidelines
├── Website/                Marketing/education website (Next.js)
├── dApp/                   Core transactional application (Next.js/React)
├── Smart-Contracts/        Solidity contracts + Hardhat tooling
├── SDK/                    @celoht/sdk package (see SDK.md)
├── CLI/                    @celoht/cli package (see CLI.md)
└── .github/                Org-wide default community health files
```

## This Repository's Structure

```
Docs/
├── README.md, WHITEPAPER.md, LITEPAPER.md, ...   Top-level reference docs
├── education/                                     Detailed curriculum modules
│   └── module-01 ... module-08 ...md
├── agent-network/                                 Detailed operational manuals
│   ├── onboarding-and-verification.md
│   ├── training-curriculum.md
│   ├── risk-management.md
│   ├── dashboards.md
│   └── emergency-procedures.md
└── .github/                                       Issue templates, PR template, CI workflow
```

## Design Principle Behind This Structure

Top-level `.md` files in the repository root are the **canonical reference** for each topic — kept concise and cross-linked. Deep operational detail (training syllabi, step-by-step manuals) lives in topic subfolders (`education/`, `agent-network/`) linked *from* the canonical file, so a newcomer can get oriented from the root README without being immediately overwhelmed, while depth is still fully available.

## Related Repository Structures

- **dApp repository structure:** [DEVELOPER_GUIDE.md](./DEVELOPER_GUIDE.md#project-structure)
- **Brand repository structure:** see that repository's own `README.md`

## Adding New Structure

New subfolders (e.g. a future `reforestation/` folder for detailed planting-methodology manuals, matching the pattern already used for `agent-network/`) are proposed via the standard RFC process — see [CONTRIBUTING.md](./CONTRIBUTING.md) — to keep the structure intentional rather than organically inconsistent.

## References

- [CONTRIBUTING.md](./CONTRIBUTING.md)
- [DEVELOPER_GUIDE.md](./DEVELOPER_GUIDE.md)
- [ARCHITECTURE.md](./ARCHITECTURE.md)
