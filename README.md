# CeloHT Documentation

**The complete technical, governance, and impact documentation for CeloHT a Haitian-led, open-source, community-governed initiative for financial inclusion, blockchain education, and environmental sustainability, founded in Léogâne, Haiti.**

[![License: Apache 2.0](https://img.shields.io/badge/License-Apache_2.0-blue.svg)](./LICENSE)
[![No Token Policy](https://img.shields.io/badge/Token-None-critical)](./NO_TOKEN_POLICY.md)
[![Community Governed](https://img.shields.io/badge/Governance-Community-1B2A4A)](./GOVERNANCE.md)

---

## Start Here

| I want to... | Read |
|---|---|
| Understand what CeloHT is, in 5 minutes | [LITEPAPER.md](./LITEPAPER.md) |
| Get the full institutional-grade overview | [WHITEPAPER.md](./WHITEPAPER.md) |
| See how CeloHT started and what's happened so far | [HISTORY.md](./HISTORY.md) |
| Understand how CeloHT is funded and sustained | [BUSINESS_MODEL.md](./BUSINESS_MODEL.md) |
| Understand how CeloHT is governed | [GOVERNANCE.md](./GOVERNANCE.md) |
| Confirm CeloHT has no token | [NO_TOKEN_POLICY.md](./NO_TOKEN_POLICY.md) |
| Learn the technical architecture | [ARCHITECTURE.md](./ARCHITECTURE.md) |
| Understand the Education pillar | [EDUCATION.md](./EDUCATION.md) |
| Understand the Agent Network pillar | [AGENT_NETWORK.md](./AGENT_NETWORK.md) |
| Understand the Reforestation pillar | [REFORESTATION.md](./REFORESTATION.md) |
| Build on CeloHT (smart contracts, dApp) | [DEVELOPER_GUIDE.md](./DEVELOPER_GUIDE.md) + [SMART_CONTRACTS.md](./SMART_CONTRACTS.md) |
| Integrate with CeloHT's API | [API_REFERENCE.md](./API_REFERENCE.md) |
| Report a security issue | [SECURITY.md](./SECURITY.md) |
| Contribute | [CONTRIBUTING.md](./CONTRIBUTING.md) |
| See what's coming | [ROADMAP.md](./ROADMAP.md) |
| Look up a term | [GLOSSARY.md](./GLOSSARY.md) |

---

## What is CeloHT?

CeloHT is a Haitian-led, open-source initiative expanding financial inclusion through three permanent pillars:

1. **[Education](./EDUCATION.md)** - Web3, financial literacy, and digital security education, delivered primarily in Haitian Creole.
2. **[Agent Network](./AGENT_NETWORK.md)** - a trained, community-rooted network of local agents providing cash ↔ cUSD conversion and digital payment support.
3. **[Reforestation](./REFORESTATION.md)** - measurable, transparently reported environmental restoration tied to community development.

CeloHT uses the **Celo blockchain** as infrastructure supporting **cUSD** for payments, **CELO** for gas, and the **Valora** wallet. CeloHT is independently governed by its community and is **not officially affiliated with, endorsed by, or operated by Celo Foundation or Valora.**

**CeloHT has no native token, no ICO, no presale, and makes no investment promises.** See [NO_TOKEN_POLICY.md](./NO_TOKEN_POLICY.md).

## Language Policy

All content in this repository is maintained in **English** as the primary technical/reference language, to ensure consistency for the global developer and partner community. Education-facing materials distributed directly to communities are produced separately, primarily in Haitian Creole see [EDUCATION.md](./EDUCATION.md#localization).

## Repository Map

```
celoht-docs/
├── README.md                  You are here
├── WHITEPAPER.md               Full institutional overview
├── LITEPAPER.md                Concise overview for partners/press
├── HISTORY.md                   Origin and verified key milestones
├── BUSINESS_MODEL.md            Funding sources and long-term sustainability
├── FOUNDATION.md                Foundational structure and principles
├── FOUNDER.md                   Founder profile and role
├── AUTHORS.md                   Contributor recognition
├── ARCHITECTURE.md             System design and technical architecture
├── SYSTEM_DESIGN.md             ADRs and detailed data flows
├── SMART_CONTRACTS.md          Smart contract specifications
├── DAPP.md                     dApp design and user flows
├── API_REFERENCE.md            API specification
├── SDK.md                       SDK specification
├── CLI.md                       CLI tool specification
├── TECHNOLOGY.md                 One-page technology stack overview
├── THREAT_MODEL.md               Detailed threat analysis
├── INCIDENT_RESPONSE.md          Step-by-step incident response process
├── TRADEMARK.md                  Trademark usage and enforcement
├── SUPPORT.md / CONTACT.md       How to get help, who to contact
├── MAINTAINERS.md / FIRST_CONTRIBUTION.md   Maintainer model, first-PR guide
├── DEVELOPER_GUIDE.md          How to build with/on CeloHT
├── USER_GUIDE.md                 How to use CeloHT as an end user
├── DEPLOYMENT.md                 Deployment process across environments
├── MONITORING.md                 Observability and incident response
├── EDUCATION.md                Education pillar
├── AGENT_NETWORK.md            Agent Network pillar
├── REFORESTATION.md            Reforestation pillar
├── CELO.md / CUSD.md / VALORA.md         Ecosystem integration docs
├── GOVERNANCE.md               Decision-making, maintainers, working groups
├── WORKING_GROUPS.md            Working group charters
├── NO_TOKEN_POLICY.md          Formal no-token policy
├── FUNDING_POLICY.md            Funding rules and transparency
├── LEGAL_STATUS.md             Legal structure and disclaimers
├── DISCLAIMER.md                Full legal disclaimer (liability, no investment, blockchain risk)
├── PRIVACY.md / TERMS.md        Privacy and terms summaries
├── SECURITY.md                 Security policy and threat model
├── ROADMAP.md                  Multi-year roadmap
├── PARTNERS.md                 Partnership framework and current partners
├── METRICS.md / IMPACT.md       Impact metrics, methodology, theory of change
├── CASE_STUDIES.md / RESEARCH.md  Case study standards, research partnerships
├── COMMUNITY.md / AMBASSADOR_PROGRAM.md / EVENTS.md   Community structure
├── ACCESSIBILITY.md              Accessibility standard and testing
├── SUSTAINABILITY.md             Environmental + organizational sustainability
├── TRANSLATION_GUIDE.md          Localization and translation standards
├── FAQ.md                      Frequently asked questions
├── GLOSSARY.md                 Terminology reference
├── CONTRIBUTING.md             How to contribute
├── CODING_STANDARDS.md          Code style and testing requirements
├── RELEASE_MANAGEMENT.md        Versioning and release process
├── PROJECT_STRUCTURE.md         Repository and org structure
├── DESIGN_SYSTEM.md             Application-level design token implementation
├── SUPPORTED_NETWORKS.md        Celo network tiers used
├── SUCCESS_STORIES.md / BLOG_GUIDE.md / CAREERS.md   Content and employment standards
├── CODE_OF_CONDUCT.md          Community standards
├── CHANGELOG.md                Documentation version history
└── LICENSE                     Apache 2.0 License

education/            Full 8-module curriculum, lesson-by-lesson (see EDUCATION.md)
agent-network/         Full operational manuals: onboarding, training, risk, dashboards, emergencies
reforestation/          Full operational manuals: planting, nursery, monitoring, volunteers
templates/              Standard response templates: community updates, partnership inquiries, issue triage
validate.sh             Local validation script (mirrors CI checks)
```

## Related Repositories

- Brand assets & visual identity: [github.com/Celo-HT/Brand](https://github.com/Celo-HT/Brand)
- Website: [github.com/Celo-HT/Website](https://github.com/Celo-HT/Website)
- dApp: [github.com/Celo-HT/dApp](https://github.com/Celo-HT/dApp)
- Smart Contracts: [github.com/Celo-HT/Smart-Contracts](https://github.com/Celo-HT/Smart-Contracts)

## Contact

contact@celoht.com ·  · [celoht.com](https://celoht.com)
