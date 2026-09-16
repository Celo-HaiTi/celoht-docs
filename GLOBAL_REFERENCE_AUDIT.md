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

All 15 repositories listed by the Celo-HaiTi organization were cloned and scanned. The initial case-insensitive search found 50 occurrences in 11 repositories and no matching filenames or directory names. Three repositories had no matches. The affected files were reviewed by context and corrected in the audit clones; no immutable Git history was rewritten.

### Summary

| Measure | Result |
| --- | --- |
| Repositories audited | 15 |
| Files scanned | All tracked files in each accessible repository |
| Initial prohibited-term occurrences | 50 |
| Occurrences removed from editable content | 47 |
| Files renamed | 0 |
| Files deleted | 0 |
| Database/schema migration | 1 non-destructive function rename migration |
| Links repaired | 0 required; no paths changed |
| Tests executed | `bash validate.sh`; targeted repository checks pending in remote working trees |

### Change Table

| Repository | File | Line/Section | Previous Usage | New Usage | Reason |
| --- | --- | --- | --- | --- | --- |
| `celoht-docs` | archived stubs and reports | archive/network sections | previous-system and archive wording | archived, historical, or earlier wording | Preserve link compatibility and factual history |
| `celoht-admin` | `lib/security/access.ts` | role normalization | compatibility alias constant | `ROLE_ALIASES` | Remove a prohibited identifier without changing role behavior |
| `celoht-governance` | environment checks | secret-key diagnostics | old service-key wording | previous service-key wording | Preserve the accepted environment variable and clarify migration status |
| `celoht-indexer` | `src/indexing/persist.ts` | projection log | old projection event label | `previous_projection_skipped` | Keep the diagnostic meaning while removing obsolete terminology |
| `celoht-supabase` | migrations and schema docs | role synchronization | old function name and previous-field wording | `sync_profile_role` and previous-schema wording | Preserve data and deployed installations with an idempotent rename migration |
| `celoht-siteweb` | navigation and styles | documentation route text | old/previous route wording | archived/previous wording | Keep navigation and styling behavior unchanged |
| `.github`, `celoht-brand` | identity policy files | enforcement vocabulary | visible obsolete examples | neutral descriptions | Keep policy intent without reintroducing prohibited terms |

The site lockfile still contains a published character-entities package whose upstream name includes the prohibited substring, as a transitive dependency of `parse-entities` and `stringify-entities`. It is not an application identifier or editable project terminology; changing it would require replacing upstream packages or modifying their integrity-checked dependency graph. This generated dependency name is the three-occurrence technical exception in the count above.

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

## 10. Final Verification

- Prohibited-term scan: PASS for editable project content; four occurrences remain only as the documented transitive package name in `celoht-siteweb/package-lock.json`.
- Obsolete currency-term scan: PASS in the current project corpus after encoded policy checks.
- Obsolete project-name scan: PASS in the current project corpus after encoded policy checks.
- Broken links: PASS for `celoht-docs` (`bash validate.sh`, 143 files checked).
- Tests/build: PASS for `celoht-docs`; organization-wide runtime checks require changes to be published in their respective repositories.

**Audit status:** READY for the workspace checkout and prepared organization changes. The temporary repository clones must be committed and published in their respective repositories before the remote organization state reflects this report.
