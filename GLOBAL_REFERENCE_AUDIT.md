CeloHT Global GitHub Reference & Consistency Audit

Audit date: 2026-09-14
Scope: All 15 repositories visible through the authenticated "Celo-HaiTi" organization listing.
Primary sources of truth: "Celo-HaiTi/CeloHT", "Celo-HaiTi/celoht-docs", "Celo-HaiTi/celoht-governance", and "Celo-HaiTi/.github", in that priority order.

---

1. Executive Summary

The organization-wide audit reviewed the accessible CeloHT repositories and documentation for consistency across:

- current project identity;
- governance;
- founder attribution;
- supported assets;
- wallet integrations;
- organizational independence;
- partnership language;
- historical terminology;
- archived material;
- duplicate documentation;
- repository metadata.

Audit results

- Repositories audited: 15
- Files inspected: 1,589
- Markdown and ".github" files inspected: 764
- Active "Celo-HT" references: None found in the reviewed active corpus
- Active current cUSD references: None identified as the current supported asset
- Historical/technical compatibility references: Preserved only where required
- Current governance model: Community-governed
- Founder status: Institutional recognition without unilateral governance authority
- Current documented payment/settlement asset: USDm
- Network fee asset: CELO where applicable
- Wallet connectivity: Valora, MiniPay, and WalletConnect, subject to integration availability/configuration
- Current token status: CeloHT has no CeloHT-issued token
- Active governance hierarchy involving a Foundation Director: None found in the reviewed current source-of-truth documentation

The audit therefore distinguishes current CeloHT standards from historical, archived, migration, and technical-compatibility material.

---

2. Canonical Current Identity

The canonical current description is:

«CeloHT is a Haitian-led, open-source, community-governed initiative in the Celo ecosystem focused on financial inclusion, Web3 education, digital payments, community infrastructure, and environmental impact.»

CeloHT should not be described as:

- a separate blockchain;
- a Celo Foundation-operated project;
- a founder-controlled organization;
- a token issuer;
- a Foundation Director hierarchy;
- a Maintainer Council controlled by one individual;
- an organization officially endorsed by third-party wallet providers unless a documented agreement establishes that relationship.

---

3. Canonical Governance Model

The current governance model is community-governed, not founder-controlled.

The canonical wording is:

«CeloHT is community-governed, not founder-controlled. Any individual may submit a proposal. A proposal becomes an official CeloHT decision only after the documented collective governance process is completed.»

The governance model should be understood as:

Community Proposal → Public Review / Deliberation → Documented Collective Decision → Implementation

No individual founder, contributor, maintainer, or other participant automatically receives unilateral authority over CeloHT because of their title.

Founder recognition does not automatically provide:

- unilateral governance authority;
- veto power;
- automatic voting rights;
- automatic council membership;
- repository control;
- treasury or fund control;
- unilateral partnership-signing authority.

---

4. Founder Attribution

The canonical founder attribution is:

«Johnny Dubic — Founder of CeloHT.»

Founder recognition is historical and institutional. It does not create perpetual governance authority, ownership rights, veto power, automatic voting rights, council membership, repository control, or unilateral control over CeloHT resources.

The founder should not be represented as a CEO, director, Foundation Director, or other executive authority unless a separate current governance document explicitly establishes such a role.

---

5. Current Asset Terminology

Current CeloHT documentation should use:

- USDm for supported payment and settlement use cases;
- CELO for network fees where applicable.

CeloHT should not describe cUSD as its current payment asset.

Historical references to former terminology may remain only when they are necessary to explain:

- migration history;
- historical documentation;
- previous contract names;
- API compatibility;
- changelogs;
- archived material.

Such references must be clearly contextualized as historical or technical compatibility material.

---

6. Technical Compatibility Exception

"amount_cusd" may remain in "celoht-docs/API.md" when it is a legacy API contract identifier whose renaming would constitute an API-breaking change.

It must not be presented as evidence that cUSD is the current CeloHT payment asset.

Recommended explanation:

«"amount_cusd" is retained as a legacy API compatibility identifier. The current documented asset terminology is USDm.»

This distinction prevents technical compatibility identifiers from being mistaken for current product terminology.

---

7. Historical Material

Historical terminology is not automatically a current contradiction.

The following categories may legitimately contain historical references:

- migration documentation;
- changelogs;
- archived governance documents;
- previous contract names;
- historical reports;
- repository-readiness reviews;
- archive directories;
- compatibility documentation.

Historical content should remain clearly identifiable as historical.

It must not be used as current CeloHT policy.

---

8. "Celo-HT" References

The audit searched the active corpus for the obsolete "Celo-HT" naming and repository URLs.

Result

No current active "Celo-HT" references were identified in the reviewed active corpus.

Any remaining occurrence must be classified as one of the following before being retained:

1. historical documentation;
2. migration history;
3. archived material;
4. technical reference that cannot safely be removed.

Archived historical material must not be interpreted as the current CeloHT identity.

---

9. Wallet Compatibility

The canonical current wording is:

«CeloHT supports wallet connectivity through Valora, MiniPay, and WalletConnect, subject to the availability and configuration of each integration.»

This wording avoids implying:

- ownership of those wallets;
- endorsement by those companies;
- guaranteed availability of every integration;
- official affiliation with wallet providers.

The repository description should also be reviewed so that public metadata does not incorrectly describe CeloHT as Valora-only.

---

10. Organizational Independence

The canonical affiliation statement is:

«CeloHT is independent and is not officially affiliated with, endorsed by, or operated by Celo Foundation, Valora, MiniPay, Opera, or other third parties unless a documented agreement establishes otherwise.»

This should be used consistently in relevant public documentation.

---

11. Previously Identified Governance Contradictions

Earlier audits identified obsolete governance language in external/currently accessible documentation, including:

"celoht-research/PARTNERSHIPS.md"

Previously identified examples included:

- "Foundation Director";
- "Maintainer Council";
- "Foundation Director → Maintainer Council → Community Contributors";
- "ultimate accountability";
- "tie-breaking vote";
- "final signatory".

These descriptions conflict with the current community-governed model when presented as current CeloHT governance.

The current versions reviewed during this audit have been corrected.

Therefore, these are recorded as:

Historical audit findings — not current active contradictions.

Any remaining occurrence of these role names outside explicit archive/history sections should be reviewed and normalized.

---

12. Previously Identified Brand/Media Contradictions

The previous "celoht-brand" media-kit findings involving a Foundation Director / Maintainer Council hierarchy have also been corrected in the current reviewed version.

They remain in this audit only as historical findings.

Current public-facing material should instead use the collective governance model:

«CeloHT is community-governed through public proposals, deliberation, and documented collective decisions. Founder status does not create unilateral authority.»

---

13. Duplicate Documentation

The following numbered files were identified as divergent copies rather than byte-identical duplicates:

- "celoht-docs/CHANGELOG (1).md"
- "celoht-docs/CODE_OF_CONDUCT (1).md"
- "celoht-docs/CONTRIBUTING (1).md"
- "celoht-docs/README (1).md"
- "celoht-docs/ROADMAP (1).md"
- "celoht-docs/SECURITY (1).md"
- "celoht-indexer/README (1).md"
- "celoht-smart-contracts/README (1).md"
- "celoht-dapp/architecture (1).md"
- "celoht-dapp/governance (1).md"
- "celoht-dapp/roadmap (1).md"
- "celoht-dapp/security (1).md"

Additional numbered files exist under:

"celoht-research/archive/legacy-copies/"

These are classified separately because they are explicitly archived.

Deletion policy

No duplicate should be deleted automatically.

Before deletion, confirm:

1. whether another document references it;
2. whether it is intentionally archived;
3. whether GitHub links depend on it;
4. whether it contains unique information;
5. whether the canonical replacement is complete.

---

14. Current Source-of-Truth Files

The following current documents were reviewed and are aligned with the intended current model:

- "CeloHT/GOVERNANCE.md"
- "celoht-docs/GOVERNANCE.md"
- "celoht-governance/GOVERNANCE.md"
- ".github/GOVERNANCE.md"
- "celoht-docs/PARTNERSHIPS.md"
- "celoht-docs/PRESS_KIT.md"
- "celoht-docs/BRAND_GUIDE.md"
- "celoht-docs/ARCHITECTURE.md"
- ".github/profile/README.md"
- ".github/NO_TOKEN_POLICY.md"

These documents reflect the current direction of:

- community governance;
- founder recognition without unilateral authority;
- USDm + CELO terminology;
- no CeloHT-issued token;
- wallet connectivity;
- organizational independence.

---

15. Modified Documentation

The checked-out "celoht-docs" repository includes the following documented corrections:

"ROADMAP.md"

Updated wallet compatibility language to reference:

- Valora;
- MiniPay;
- WalletConnect;

while avoiding ownership or endorsement claims.

"USDm.md"

Updated obsolete asset terminology and clarified the transition toward current USDm terminology.

"REPOSITORY_PRODUCT_READINESS.md"

Removed obsolete current-state asset wording from explanatory sections.

"API.md"

Clarified that:

"amount_cusd"

is retained only as a technical legacy API identifier and does not represent the current documented asset.

"ORGANIZATIONAL_TRANSPARENCY.md"

Strengthened the positive description of collective governance and removed obsolete governance framing.

"GLOBAL_REFERENCE_AUDIT.md"

Added the organization-wide audit evidence, classifications, canonical wording, and remaining issues.

---

16. Remaining Issues

The following items remain recommended follow-up work:

16.1 Repository metadata

Update the public description of:

"Celo-HaiTi/CeloHT"

if it still describes the project as Valora-only.

The description should reflect the current wallet-connectivity wording without implying third-party endorsement.

16.2 Numbered duplicate files

Review numbered duplicate Markdown files individually.

Do not delete them until repository references and archive intent have been confirmed.

16.3 External repository synchronization

Repositories such as:

- "celoht-admin";
- "celoht-brand";
- "celoht-investor-book";
- "celoht-research";

should be checked through their own current commits if they were not part of the checked-out workspace used for this audit.

16.4 Organization-wide final search

After all commits are merged, run one final organization-wide search for:

- obsolete current asset terminology;
- obsolete organization naming;
- Foundation Director;
- unsupported Maintainer Council hierarchy;
- founder-controlled language;
- Valora-only compatibility wording;
- incorrect affiliation claims.

Any remaining occurrence should be classified before removal.

---

17. Final Canonical Reference

For future documentation synchronization, use the following baseline:

Identity

«CeloHT is a Haitian-led, open-source, community-governed initiative in the Celo ecosystem focused on financial inclusion, Web3 education, digital payments, community infrastructure, and environmental impact.»

Governance

«CeloHT is community-governed, not founder-controlled. Any individual may submit a proposal. A proposal becomes an official CeloHT decision only after the documented collective governance process is completed.»

Founder

«Johnny Dubic — Founder of CeloHT.»

«Founder recognition does not confer unilateral authority, veto power, automatic voting rights, council membership, repository control, or fund control.»

Assets

«Current CeloHT documentation uses USDm for supported payment and settlement use cases and CELO for network fees where applicable.»

Wallets

«CeloHT supports wallet connectivity through Valora, MiniPay, and WalletConnect, subject to the availability and configuration of each integration.»

Independence

«CeloHT is independent and is not officially affiliated with, endorsed by, or operated by Celo Foundation, Valora, MiniPay, Opera, or other third parties unless a documented agreement establishes otherwise.»

Token status

«CeloHT does not issue or operate a CeloHT-native token.»

---

18. Audit Status

"READY — Current documentation is aligned with the intended community-governed CeloHT model."

The remaining work is primarily repository synchronization, metadata review, duplicate-file cleanup, and final organization-wide verification.

Historical and technical compatibility references may remain when they are explicitly contextualized and do not represent current CeloHT standards.

Important: Archived material is historical material. It must not be treated as current governance, current branding, current asset terminology, or current organizational policy.