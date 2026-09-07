# Production Readiness

This is the canonical readiness matrix for the CeloHT implementation repositories. Status is evidence-based and applies to the repository revisions checked on 2026-09-07. `IMPLEMENTED` means code or documentation exists; it does not mean deployed. `DEPLOYED` means a deployment manifest or environment evidence exists. `VERIFIED` means the deployment or artifact was independently checked by the named source. `AUDITED` is reserved for an independent security audit. `PRODUCTION READY` requires the relevant operational, security, and governance evidence.

| Component | IMPLEMENTED | DEPLOYED | VERIFIED | AUDITED | Current status | Evidence / limitation |
|---|---:|---:|---:|---:|---|---|
| Smart contracts | Yes | TESTNET only | Yes, Celo Sepolia Blockscout | No | TESTNET | Five contracts are deployed on Celo Sepolia (`11142220`). No Mainnet manifest exists. |
| Audit | No independent audit | N/A | No | No | PLANNED | No audit report or remediation record is present in the contracts source. |
| Indexer | Yes | Not production | Testnet configuration only | No | TESTNET | Reads Celo Sepolia events and USDm transfers; Mainnet is deliberately disabled. |
| Supabase/data layer | Schema and ownership are defined in the implementation repos | No production evidence in this docs checkout | No live project evidence | No | PLANNED | Backend and indexer require an externally provisioned Supabase project. |
| Backend | Yes | No deployed URL configured | Build/test evidence only | No | IMPLEMENTED / UNAVAILABLE | Auth, KYC, application workflows, and authorization are implemented in source; live integration is unavailable without environment provisioning. |
| Admin | Yes | No live operational integration | Build/test evidence only | No | IMPLEMENTED / UNAVAILABLE | Dashboard uses contained mock data unless a reviewed Supabase integration is provisioned. |
| dApp | Yes | Testnet application | Celo Sepolia config synchronized | No | TESTNET | Mainnet financial use is blocked; backend-dependent features remain unavailable without a backend URL. |
| Monitoring | Health/readiness endpoints and operational docs exist | No production service evidence | No | No | PLANNED | Indexer and backend expose checks in code, but no production monitoring ownership or alert evidence is documented. |
| Governance | Contract governance code and policy exist | Testnet contract governance exists | Testnet metadata only | No | TESTNET / PLANNED | No verified production authority or Mainnet deployment is documented. |
| Treasury | Treasury address is present in the Celo Sepolia manifest | TESTNET only | Address is recorded in manifest | No | TESTNET | The manifest uses one Celo Sepolia Safe address; custody and production controls are not established. |
| Incident response | Policies and runbooks are documented | No production exercise evidence | No | No | PLANNED | Incident ownership, drills, and recovery evidence remain open. |

## Canonical network and asset facts

- Celo Sepolia is the only current CeloHT deployment: chain ID `11142220`.
- Celo Mainnet chain ID is `42220`, but CeloHT Mainnet contracts and USDm metadata are unavailable.
- USDm is the settlement asset used by the protocol contracts. CELO is the Celo network gas asset.
- CeloHT has no native token, governance token, reward token, staking token, ICO, or presale.

## Status vocabulary

Use these terms precisely:

- **IMPLEMENTED**: present in the checked-in source.
- **DEPLOYED**: deployed to a named network with a traceable manifest or transaction evidence.
- **VERIFIED**: deployment or source verified by a named verification system or reproducible check.
- **AUDITED**: reviewed by an independent third-party security auditor with a published report.
- **TESTNET**: available only on a test network or suitable for testnet review.
- **MAINNET**: configured and evidenced on Celo Mainnet.
- **PRODUCTION READY**: all required security, operations, governance, data, and deployment gates are satisfied.
- **PLANNED**: intended work without current implementation evidence.
- **UNAVAILABLE**: not usable in the current configured environment; do not substitute mock or derived data.

No component in the current evidence set is `PRODUCTION READY` or `AUDITED`.
