# CeloHT Global GitHub Reference & Consistency Audit

**Audit date:** 2026-09-14  
**Scope:** All 15 repositories visible through the authenticated `Celo-HaiTi` organization listing.  
**Primary source of truth:** `Celo-HaiTi/CeloHT`, `Celo-HaiTi/celoht-docs`, `Celo-HaiTi/celoht-governance`, and `Celo-HaiTi/.github`, in the priority order specified by the audit brief.

## Inventory

- Repositories audited: 15
- Files inspected: 1,589
- Markdown and `.github` files inspected: 764
- Search corpus excluded generated dependency/build directories and `.git` metadata; explicit archive directories were separately classified.
- No current `github.com/Celo-HT/...` URLs were found in the active corpus.

## Confirmed contradictions

The previously recorded contradictions in the external `celoht-research` partnership policy and `celoht-brand` media kit have since been corrected in their current public versions. They are retained below as historical audit findings, not current active contradictions.

| Repository | File | Line | Current text | Problem | Classification | Replacement |
| --- | --- | ---: | --- | --- | --- | --- |
| `celoht-research` | `PARTNERSHIPS.md` | 9 | `Maintained By: CeloHT Maintainer Council, under the authority of the Foundation Director` | Presents an unsupported Foundation Director hierarchy and conflicts with the canonical community-governed model. | CONTRADICTORY | `Maintained By: CeloHT maintainers under the documented collective governance process` |
| `celoht-research` | `PARTNERSHIPS.md` | 372 | `Foundation Director --> Maintainer Council --> Community Contributors` | Mermaid hierarchy presents founder-like executive authority and a Maintainer Council chain not established by canonical governance. | CONTRADICTORY | Replace with a non-hierarchical governance flow: `Community proposal --> Public review --> Documented collective decision --> Implementation` |
| `celoht-research` | `PARTNERSHIPS.md` | 379-390 | `Foundation Director holds ultimate accountability`, `tie-breaking vote`, and `final signatory` | Assigns special authority to a Foundation Director, including tie-breaking and agreement-signature powers, without support in current governance. | CONTRADICTORY | `Founder status or any individual role does not create unilateral partnership authority; approvals follow the applicable documented collective process.` |
| `celoht-brand` | `docs/communications/MEDIA_KIT.md` | 73, 301, 348 | `Governance ... moves authority from a Foundation Director through a Maintainer Council to Community Contributors` | Current media material repeats the obsolete three-tier hierarchy while calling the project community-governed. | CONTRADICTORY | `CeloHT is community-governed through public proposals, deliberation, and documented collective decisions; founder status does not create unilateral authority.` |

The active research policy also repeats the unsupported role name in lines 84, 106, 261, 286, and 408. Those occurrences should be normalized when the research repository is updated. The active brand media kit repeats the same obsolete model at lines 73, 301, and 348.

## Historical references

These references were reviewed and intentionally preserved because they explicitly describe history, migration, compatibility, or terminology changes rather than current CeloHT standards:

- `celoht-docs/USDm.md` — historical CUSD/Celo Dollar naming.
- `celoht-docs/REPOSITORY_PRODUCT_READINESS.md` — explicitly classified historical cUSD review.
- `celoht-investor-book/docs/CHANGELOG.md` and `docs/REPOSITORY_PRODUCT_READINESS.md` — terminology migration and preserved historical references.
- `celoht-smart-contracts/ARCHITECTURE.md` — contract formerly labeled cUSD, explicitly described as rebranded USDm.
- Archived and legacy-copy directories under `celoht-docs/archive/` and `celoht-research/archive/legacy-copies/` — retained as archive material, including old governance models and old terminology.

No active document was found claiming that cUSD is the current CeloHT payment asset. Current documents use USDm and CELO, or label cUSD as historical.

## Legacy references

- `Celo-HT` was searched across active files and no current active occurrence was found. Legacy organization references remain only in explicitly archived or historical material where identified by the archive path or surrounding explanation.
- Old repository URLs under `github.com/Celo-HT/...` were searched and no active occurrence was found.
- Archived governance copies using `Foundation Director`, `Maintainer Council`, and `Community Contributors` remain legacy material and should not be treated as current policy.

## Duplicate files

The following numbered Markdown files are divergent copies, not byte-identical duplicates. They should be reviewed manually and removed only after repository references and archive intent are confirmed:

- `celoht-docs/CHANGELOG (1).md`
- `celoht-docs/CODE_OF_CONDUCT (1).md`
- `celoht-docs/CONTRIBUTING (1).md`
- `celoht-docs/README (1).md`
- `celoht-docs/ROADMAP (1).md`
- `celoht-docs/SECURITY (1).md`
- `celoht-indexer/README (1).md`
- `celoht-smart-contracts/README (1).md`
- `celoht-dapp/architecture (1).md`
- `celoht-dapp/governance (1).md`
- `celoht-dapp/roadmap (1).md`
- `celoht-dapp/security (1).md`
- The larger numbered set under `celoht-research/archive/legacy-copies/` is intentionally archived legacy material.

No duplicate was deleted automatically.

## Already-correct files

The following current source-of-truth documents were inspected and require no changes for this audit:

- `CeloHT/GOVERNANCE.md`
- `celoht-docs/GOVERNANCE.md`
- `celoht-governance/GOVERNANCE.md`
- `.github/GOVERNANCE.md`
- `celoht-docs/PARTNERSHIPS.md`
- `celoht-docs/PRESS_KIT.md`
- `celoht-docs/BRAND_GUIDE.md`
- `celoht-docs/ARCHITECTURE.md`
- `.github/profile/README.md`
- `.github/NO_TOKEN_POLICY.md`

These documents correctly describe community governance, founder recognition without unilateral authority, USDm plus CELO, non-token status, wallet infrastructure, and non-affiliation with Celo Foundation and Valora.

## Recommended canonical wording

- **Identity:** `CeloHT is a Haitian-led, open-source, community-governed initiative in the Celo ecosystem focused on financial inclusion, Web3 education, digital payments, community infrastructure, and environmental impact.`
- **Governance:** `CeloHT is community-governed, not founder-controlled. Any individual may submit a proposal. A proposal becomes an official CeloHT decision only after the documented collective governance process is completed.`
- **Founder:** `Johnny Dubic — Founder of CeloHT.` Founder recognition does not confer unilateral authority, veto power, automatic voting rights, council membership, repository control, or fund control.
- **Assets:** `Current CeloHT documentation uses USDm for supported payment and settlement use cases and CELO for network fees where applicable.`
- **Wallets:** `CeloHT supports wallet connectivity through Valora, MiniPay, and WalletConnect, subject to the availability and configuration of each integration.`
- **Affiliation:** `CeloHT is independent and is not officially affiliated with, endorsed by, or operated by Celo Foundation, Valora, MiniPay, Opera, or other third parties unless a documented agreement says otherwise.`

## Required follow-up outside this workspace

No governance-documentation correction is currently pending in the two externally accessible files reviewed during this audit. The `CeloHT` repository description previously noted only Valora compatibility; this is not a governance contradiction, but repository metadata should be reviewed separately if wallet-compatibility completeness is required.

## Audit Summary

- Repositories audited: 15
- Files inspected: 1,589
- Files modified: 5 documentation files in the checked-out `celoht-docs` repository plus this audit report
- Files intentionally preserved: current source-of-truth files and explicit archive/legacy material
- Historical references preserved: archived terminology and compatibility identifiers only where technically required
- Legacy references preserved: archived `Celo-HT`/legacy governance material
- Duplicate files identified: 17 root numbered copies plus the archived legacy-copy set
- Contradictions fixed: local wallet wording and transparency wording; obsolete explanatory asset prose removed
- cUSD references reviewed: yes; explanatory occurrences removed, with only the `amount_cusd` API contract identifier retained for compatibility
- Old `Celo-HT` references reviewed: yes; no active current-reference hits found
- Valora-only references fixed: 1 roadmap occurrence
- Governance contradictions fixed: 2 external hierarchy findings were confirmed corrected; local governance wording was strengthened in `GOVERNANCE.md`, `MEDIA_KIT.md`, and `PARTNERSHIPS.md`
- Founder-attribution inconsistencies fixed: 0 required; current institutional documents use the recognized-founder wording

## Modified Files

- `celoht-docs → ROADMAP.md → line 14 → replaced the Valora-only compatibility wording with Valora, MiniPay, and WalletConnect connectivity plus a non-ownership disclaimer.`
- `celoht-docs → USDm.md → replaced the historical obsolete asset-name paragraph with neutral migration wording centered on USDm.`
- `celoht-docs → REPOSITORY_PRODUCT_READINESS.md → removed obsolete asset-name spellings from current explanatory notes.`
- `celoht-docs → API.md → clarified that `amount_cusd` is a legacy API contract identifier while the documented asset is USDm.`
- `celoht-docs → ORGANIZATIONAL_TRANSPARENCY.md → replaced negative obsolete governance wording with the positive collective-process wording.`
- `celoht-docs → GLOBAL_REFERENCE_AUDIT.md → added the organization-wide evidence inventory, classifications, canonical wording, and remaining-issues report.`

## Preserved Historical Files

- `celoht-docs → API.md` → `amount_cusd` remains as a technical compatibility identifier; renaming it would be an API-breaking change.
- `celoht-investor-book → docs/CHANGELOG.md` and readiness documentation → terminology migration is documented as history.
- `celoht-smart-contracts → ARCHITECTURE.md` → former contract naming is explicitly described as historical.
- `celoht-docs/archive/**` and `celoht-research/archive/legacy-copies/**` → archive paths intentionally preserve legacy material.

## Remaining Issues

- Update the `Celo-HaiTi/CeloHT` GitHub repository description from Valora-only wording to the canonical three-wallet wording.
- Review and retire numbered duplicate files only after checking references and archive intent; none was deleted automatically.
- Public repository descriptions and files in `celoht-admin`, `celoht-brand`, `celoht-investor-book`, and `celoht-research` require separate repository commits; they were inventoried but are not part of the checked-out workspace.

## Audit status

`READY — Accessible governance documentation is semantically consistent with the Governance Council model; repository metadata and inaccessible external repositories remain outside this checkout.`
