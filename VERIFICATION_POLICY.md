# CeloHT Verification Policy

**Version 1.0 · August 2026**

This document defines how CeloHT verifies the identity and public presence of individuals holding roles of trust or authority (Governance Council members, Maintainers, Working Group Leads, Ambassadors). It exists to close the gap between "a name appears in project documentation" and "that name is a verifiable, accountable individual" — a distinction that matters directly to investors, grant reviewers, auditors, and partners conducting due diligence.

---

## Table of Contents

1. [Identity Verification Requirements](#1-identity-verification-requirements)
2. [Public Profile Requirements](#2-public-profile-requirements)
3. [GitHub Verification](#3-github-verification)
4. [Conflict of Interest Disclosure](#4-conflict-of-interest-disclosure)
5. [Removal Policy](#5-removal-policy)
6. [Privacy Considerations](#6-privacy-considerations)

---

## 1. Identity Verification Requirements

Before an individual is published in `TEAM.md` or `MAINTAINERS.md` with a status other than "Open," "Vacant," or "TBA," CeloHT requires:

- Confirmation, directly from the individual, of the name or handle they wish to be publicly associated with their role.
- Confirmation that the individual is a real, identifiable person actively performing the responsibilities of the role in question.
- Where the role carries treasury, security, or Governance Council authority, at least one additional verification step (for example, a live video confirmation with an existing Council member, or an equivalent method adopted by the Governance Council) before the role is confirmed as "Verified."

CeloHT does not consider a role "Verified" based solely on a self-submitted claim. Until the applicable verification step is complete, the individual's status is recorded as "Pending Verification," and this is disclosed openly rather than presented as complete.

---

## 2. Public Profile Requirements

Consistent with `TEAM.md` Section 7, individuals holding a Governance Council seat, Maintainer role, or Working Group Lead role are expected to maintain:

- A GitHub profile consistent with the account performing their CeloHT activity.
- At least one additional public, verifiable profile sufficient to establish real-world identifiability (for example, a professional network profile or personal website).

CeloHT does not create, estimate, or infer these profiles on an individual's behalf. If an individual has not yet provided verifiable public profile links, their entry in `TEAM.md` reads "TBA," and no placeholder link is published in its place.

---

## 3. GitHub Verification

- Role holders are expected to use a consistent, identifiable GitHub account for all CeloHT-related activity, rather than rotating between anonymous or unlinked accounts.
- Where feasible, GitHub two-factor authentication is required for any account with write access to a CeloHT repository, consistent with `ARCHITECTURE.md` Section 12 (Security Architecture).
- Organization-level access review is conducted periodically by the Governance Council to confirm that active write-access holders correspond to currently confirmed roles in `TEAM.md` and `MAINTAINERS.md`.

---

## 4. Conflict of Interest Disclosure

Verification and conflict-of-interest disclosure are linked processes:

- As part of verification, an individual assuming a Governance Council, Maintainer, or Working Group Lead role discloses any relationship (employment, family, financial) that could reasonably create a conflict of interest with CeloHT decisions, per `GOVERNANCE.md` Section 10 and `LEGAL_STATUS.md` Section 15.
- Disclosures are logged in a private register reviewable by the Governance Council and summarized, without unnecessary personal detail, in public meeting notes where relevant to a specific recusal.
- Failure to disclose a known conflict of interest is treated as a verification and Ethics Policy violation under `GOVERNANCE.md` Section 11.

---

## 5. Removal Policy

A verified role holder's status may be revised or revoked under the following circumstances:

| Circumstance | Action |
|---|---|
| Individual becomes unreachable or inactive beyond the thresholds in `GOVERNANCE.md` Section 3.9 | Moved to emeritus/inactive status; entry updated in `TEAM.md` |
| Verification information is later found to be inaccurate or misrepresented | Immediate suspension of role pending Governance Council review |
| Confirmed Ethics Policy or Conflict of Interest violation | Role removal per `GOVERNANCE.md` Section 11.5 and Section 3.9 |
| Voluntary resignation | Processed per `GOVERNANCE.md` Section 16.5; entry updated to "Open" |

All removals are reflected in `TEAM.md` and `MAINTAINERS.md` promptly, with the role marked "Open" or "Vacant" rather than left showing an inaccurate name.

---

## 6. Privacy Considerations

- CeloHT collects only the identity and profile information necessary to establish accountable, verifiable roles — not broader personal data unrelated to that purpose, consistent with `LEGAL_STATUS.md` Section 16.
- Individuals may choose to disclose additional biographical detail voluntarily, but CeloHT does not require it beyond what is necessary for role verification and public accountability.
- Verification records containing sensitive personal information (e.g., documents used for identity confirmation) are held privately and are not published; only the resulting verification status ("Verified," "Pending Verification," "Open," or "TBA") is made public.
- Contributors who are not in a role of trust or authority (Section 1) are not required to complete identity verification and may contribute under a consistent handle without disclosing their legal identity, consistent with `AUTHORS.md` Section 2.

---

*This document is maintained alongside `GOVERNANCE.md`, `LEGAL_STATUS.md`, `TEAM.md`, `AUTHORS.md`, `MAINTAINERS.md`, and `CONTRIBUTORS.md` in the CeloHT governance repository.*
