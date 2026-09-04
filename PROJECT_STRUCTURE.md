# Project Structure

## Repository Map (Organization-Wide)

```
github.com/Celo-HaiTi/
├── CeloHT/                 Meta/wiki repository, high-level org profile
├── celoht-docs/            This repository — full documentation
├── Brand/                  Visual identity, logo, brand guidelines
├── Website/                Marketing/education website (Next.js)
├── dApp/                   Core transactional application (Next.js/React)
├── Smart-Contracts/        Solidity contracts + Hardhat tooling
├── SDK/                    @celoht/sdk package (see SDK.md)
└── CLI/                    @celoht/cli package (see CLI.md)
```

## This Repository's Structure

```
celoht-docs/
├── README.md, WHITEPAPER.md, LITEPAPER.md, ...   Top-level reference docs
├── module-01 ... module-08 ...md                  Education curriculum modules
├── onboarding-and-verification.md                Agent network operations
├── training-curriculum.md, risk-management.md, ...
├── *.svg, *.png                                  Brand and favicon assets
├── *.docx, *.pptx                                Distributable source materials
└── validate.sh                                    Local documentation validation
```

## Design Principle Behind This Structure

Top-level `.md` files in the repository root are the **canonical reference** for each topic — kept concise and cross-linked. Education and operational manuals currently remain in the root so they are easy to discover and preserve stable links. New topic-specific subfolders should be introduced only when they reduce navigation cost without breaking existing links.

## Related Repository Structures

- **dApp repository structure:** [DEVELOPER_GUIDE.md](./DEVELOPER_GUIDE.md#project-structure)
- **Brand repository structure:** see that repository's own `README.md`

## Adding New Structure

New subfolders (for example, a future `reforestation/` folder for detailed planting-methodology manuals) are proposed via the standard RFC process — see [CONTRIBUTING.md](./CONTRIBUTING.md) — to keep the structure intentional rather than organically inconsistent. Any move must preserve links or include redirects/documented migration guidance.

## References

- [CONTRIBUTING.md](./CONTRIBUTING.md)
- [DEVELOPER_GUIDE.md](./DEVELOPER_GUIDE.md)
- [ARCHITECTURE.md](./ARCHITECTURE.md)
