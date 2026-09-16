# CeloHT Global GitHub Reference & Consistency Audit

**Audit date:** 2026-09-16
**Scope:** All 15 active repositories visible through the Celo-HaiTi organization listing.

## 1. Canonical Vocabulary

- **Active project:** `CeloHT`
- **Canonical GitHub organization:** `Celo-HaiTi`
- **Canonical stable-value currency:** `USDm`
- **Network fee currency:** `CELO`, where applicable
- **Canonical donation amount field:** `amount_usdm`

The canonical names above are immutable vocabulary requirements. Cleanup must never alter `CeloHT` or `Celo-HaiTi`.

## 2. Current Corpus Requirement

The current editable repository corpus must use only canonical active terminology. Obsolete terminology must not be retained merely because it appears in historical context. Immutable Git history is excluded from this requirement.

The current corpus includes current README files, Markdown files, source files, configuration, website content, examples, links, tables, text diagrams, changelogs, generated documentation whose editable source is available, and other tracked files presented as current project material.

Immutable history includes old commits, commit messages, immutable commit hashes, and historical Git objects. Those records are not rewritten by this audit.

## 3. Prohibited Vocabulary Enforcement

The audit must fail when current editable files contain either prohibited token. This policy represents them with escaped code points so that the current policy file does not itself introduce visible prohibited terminology:

- obsolete currency token: `c\u0055SD`
- obsolete project-name token: `Celo\u002DHT`
- obsolete organization URL forms: `github.com/Celo\u002DHT/` and `github.com/Celo\u002DHT`

The escaped forms above identify the exact tokens enforced by `validate.sh`; they are not acceptable current vocabulary. Historical context in a current editable file must be rewritten with canonical terminology when the meaning can be preserved. A file is not exempt because it is a changelog, audit, migration note, generated artifact, repository-readiness report, or archive copy.

## 4. API and Implementation Boundary

`celoht-docs` is a static documentation repository. It contains no backend, API runtime, OpenAPI source outside `API.md`, frontend client, TypeScript package, smart-contract source, or test suite that implements the donation API. `API.md` is a planned specification, not a live service contract.

The current planned API uses `amount_usdm` consistently in the transaction example, donation request and response, cURL, JavaScript, TypeScript, Python, and Dart examples, validation error, required fields, properties, and response schema. No compatibility exception preserves an obsolete field name.

## 5. Local Validation Results

The checked-out `celoht-docs` worktree has zero current editable-file matches for the prohibited vocabulary. `bash validate.sh` checks Markdown structure, links, configuration, text files, and text embedded in PPTX artifacts.

The local current corpus includes:

- `API.md`
- `GLOBAL_REFERENCE_AUDIT.md`
- `REPOSITORY_PRODUCT_READINESS.md`
- `CeloHT-Investor-Deck.pptx`
- all other tracked documentation and configuration files

## 6. Organization-Wide Scan Findings

The latest scan covered all 15 active repositories listed by the Celo-HaiTi organization. The local worktree is clean, but the published remote repositories are not yet synchronized:

- `Celo-HaiTi/celoht-brand/README.md:1` uses the obsolete project-name form in its current title. Replace it with `CeloHT Brand Repository`.
- `Celo-HaiTi/CeloHT/docs/CANONICAL_IDENTITY.md:11` exposes the obsolete project-name form while describing it as invalid. Rewrite the sentence using neutral canonical wording.
- `Celo-HaiTi/celoht-smart-contracts/ARCHITECTURE.md:60` contains a former-asset explanation. Rewrite it as a neutral current-terminology statement because this is a current editable architecture file.
- `Celo-HaiTi/celoht-investor-book/README.md:12`, `docs/REPOSITORY_PRODUCT_READINESS.md:164`, `docs/CHANGELOG.md:22-32`, and `PRODUCTION_READINESS.md:52` expose the former-asset token in current documentation. Rewrite these passages without displaying the token.
- `Celo-HaiTi/celoht-research/CeloHT-Investor-Deck.pptx` contains the former-asset token in visible slide content. Update the source deck; the matching deck in this worktree has already been cleaned.
- The published `Celo-HaiTi/celoht-docs` branch still contains the pre-cleanup API and audit documents. Publish this worktree before treating the organization as synchronized.

These are current editable-corpus violations, not acceptable historical exceptions. No immutable Git history was rewritten.

## 7. URL Verification

The organization-wide scan found no obsolete organization URL matches. Existing replacement links use the verified `Celo-HaiTi` organization and repository names returned by the organization listing. No repository or URL was invented during this audit.

## 8. Historical and Archive Handling

Historical Git objects may retain old terminology because rewriting immutable history is outside normal documentation cleanup. Current tracked files may not retain it merely to explain history. A historical explanation must use neutral wording such as “former asset terminology” or “obsolete project-name form.”

Archive directories and current changelogs are still editable files in the published corpus unless their repository explicitly excludes them from its current documentation experience. They are not automatic exceptions.

## 9. Enforcement Procedure

For every repository:

1. Run `bash validate.sh` when the repository provides it.
2. Search current editable files for the prohibited token forms and obsolete organization URL forms.
3. Inspect every match in context before changing it.
4. Correct documentation, examples, generated source, and links using the canonical vocabulary.
5. Leave immutable Git history unchanged.
6. Repeat the organization-wide search after all repository changes are published.

The audit fails if any current editable file contains a prohibited token, including a historical explanation, current changelog, current archive copy, generated artifact, or compatibility note.

## 10. Audit Status

**Local repository:** READY — local validation passes and the current editable corpus is clean.

**Organization-wide status:** NOT READY — the remote findings in Section 6 require correction and publication before the full Celo-HaiTi corpus can be marked ready.
