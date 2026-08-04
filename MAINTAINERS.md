# CeloHT Maintainers

**Version 1.0 · August 2026**

This document defines who holds repository-level maintainer authority within CeloHT, what that authority includes, and how it is granted, reviewed, and revoked. It follows maintainer-governance conventions used by CNCF, the Linux Foundation, and Apache Software Foundation projects.

---

## Table of Contents

1. [Repository Maintainers](#1-repository-maintainers)
2. [Responsibilities](#2-responsibilities)
3. [Review Process](#3-review-process)
4. [Code Ownership](#4-code-ownership)
5. [Release Responsibilities](#5-release-responsibilities)

---

## 1. Repository Maintainers

CeloHT's technical work spans multiple repositories (governance, website, dApp monorepo, smart contracts package, documentation hub). Each repository has its own maintainer roster, appointed by the Governance Council per `GOVERNANCE.md` Section 3.3.

| Repository | Maintainer(s) | Status |
|---|---|---|
| celoht-governance | Open | No Maintainer currently appointed |
| celoht-website | Open | No Maintainer currently appointed |
| celoht-dapp | Open | No Maintainer currently appointed |
| celoht-contracts | Open | No Maintainer currently appointed |
| celoht-docs | Open | No Maintainer currently appointed |

As of this document's publication date, no repository has a confirmed, named Maintainer distinct from the Founder's initial contribution activity. This is disclosed explicitly. As Maintainers are appointed, this table will be updated with their name or handle, appointment date, and repository scope.

---

## 2. Responsibilities

A CeloHT Maintainer is responsible for:

- Reviewing and merging pull requests within their assigned repository scope.
- Enforcing the Code Review Policy defined in `ARCHITECTURE.md` Section 12.4 and `GOVERNANCE.md` Section 13.
- Triaging and responding to reported issues and, where relevant, security disclosures per `GOVERNANCE.md` Section 12.
- Maintaining release quality and tagging releases per Section 5 below.
- Escalating technical decisions that exceed operational scope to the relevant Working Group or Governance Council, per the Decision-Making Framework in `GOVERNANCE.md` Section 4.

Maintainer status does not confer authority over governance, treasury, or strategic decisions, which remain the responsibility of the Governance Council.

---

## 3. Review Process

- All non-trivial changes require review from at least one Maintainer with write access to the relevant repository before merge.
- Changes affecting smart-contract logic or fund-handling code require review from two Maintainers with relevant technical expertise, consistent with `GOVERNANCE.md` Section 13.3.
- Reviews evaluate correctness, security, adherence to the repository's contribution guidelines, and consistency with `ARCHITECTURE.md`.
- Disagreements between reviewers that cannot be resolved through discussion are escalated per the RFC process defined in `GOVERNANCE.md` Section 4.3.

---

## 4. Code Ownership

Code ownership within CeloHT repositories is assigned at the directory or module level using a `CODEOWNERS` file (see `CODEOWNERS.md` and the repository-level `CODEOWNERS` configuration), which determines which Maintainer or team is automatically requested for review on a given change.

- Ownership reflects **review responsibility**, not personal or proprietary claim to the code, consistent with CeloHT's open-source licensing commitments in `LEGAL_STATUS.md` Section 11.
- Ownership assignments are public, versioned, and updated as Maintainers are appointed or step down.
- Unowned areas of a repository default to review by any active Maintainer for that repository, or, absent an appointed Maintainer, remain pending until one is appointed.

---

## 5. Release Responsibilities

- Maintainers are responsible for tagging releases, writing release notes (per `GOVERNANCE.md` Section 18.5), and ensuring the CI/CD pipeline (`ARCHITECTURE.md` Section 14.2) has passed prior to a production release.
- Releases affecting smart contracts require prior security review per `GOVERNANCE.md` Section 12 and `ARCHITECTURE.md` Section 12.6 before deployment.
- Release decisions are logged and, for significant releases, reported to the relevant Working Group and Governance Council.

---

## 6. Appointment, Review, and Removal

- Maintainers are appointed by the Governance Council based on a sustained record of quality contributions, per `GOVERNANCE.md` Section 3.3.
- Maintainer activity is reviewed at a minimum every six months; Maintainers inactive for 90 days without prior notice to the Council are moved to emeritus status, retaining recognition but losing write access.
- Maintainer status may be revoked by Governance Council majority vote for breach of the Code of Conduct, repeated policy violations, or sustained inactivity, following the process in `GOVERNANCE.md` Section 3.9.

---

*This document is maintained alongside `GOVERNANCE.md`, `ARCHITECTURE.md`, `TEAM.md`, `AUTHORS.md`, `CONTRIBUTORS.md`, and `VERIFICATION_POLICY.md` in the CeloHT governance repository.*
