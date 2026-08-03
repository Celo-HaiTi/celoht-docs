# Module 8: Developer Onboarding Track

*Part of the CeloHT Education curriculum — see [../EDUCATION.md](../EDUCATION.md).*
*Previous (general track): [Module 7 →](./module-07-using-the-agent-network.md)*

## Audience
Developers joining CeloHT's open-source community, whether contributing to the dApp, smart contracts, or documentation.

## Duration
Self-paced, approx. 2–3 hours including hands-on setup.

## Learning Objectives

1. Set up a local CeloHT development environment
2. Understand CeloHT's architecture at a level sufficient to contribute
3. Make a first contribution following CeloHT's standards

## Lesson 8.1 — Mission Context for Developers

Before touching code, every developer contributor is asked to read [../MISSION.md] *(Brand repository)* and [../NO_TOKEN_POLICY.md](../NO_TOKEN_POLICY.md) — understanding *why* CeloHT is built the way it is (non-custodial, minimal on-chain data, no token) prevents well-intentioned contributions that accidentally work against these principles.

## Lesson 8.2 — Environment Setup

Follow [../DEVELOPER_GUIDE.md](../DEVELOPER_GUIDE.md#local-setup) exactly. Common first-time issues:
- Missing environment variables (see [../DEVELOPER_GUIDE.md](../DEVELOPER_GUIDE.md#environment-variables))
- Attempting to test against mainnet instead of Alfajores testnet (see [../CELO.md](../CELO.md#network-usage))

## Lesson 8.3 — Architecture Orientation

Read [../ARCHITECTURE.md](../ARCHITECTURE.md) and [../SYSTEM_DESIGN.md](../SYSTEM_DESIGN.md) together. Recommended exercise: trace the full data flow of a single cash-in transaction through the diagrams in both documents before writing any code.

## Lesson 8.4 — Your First Contribution

Recommended path for a first PR:
1. Find an issue tagged `good-first-issue` (see [../EVENTS.md](../EVENTS.md#hackathon-participation) for where these are listed)
2. Follow the branch and testing standards in [../DEVELOPER_GUIDE.md](../DEVELOPER_GUIDE.md#development-workflow)
3. Open a PR using the template, and expect review per [../DEVELOPER_GUIDE.md](../DEVELOPER_GUIDE.md#code-review)

## Lesson 8.5 — Smart Contract Contributors: Extra Care

Any contribution touching [../SMART_CONTRACTS.md](../SMART_CONTRACTS.md) requires understanding the non-custodial, no-token, minimal-on-chain-data design principles deeply — these aren't just style preferences, they're the mechanisms that make CeloHT's trust and safety claims true. A contribution that technically "works" but stores personal data on-chain, for example, would undermine [../PRIVACY.md](../PRIVACY.md) even if well-intentioned.

## Completion

There's no formal "certificate" for this track — completion is demonstrated by a merged first contribution, recognized in [../AUTHORS.md](../AUTHORS.md).

## Back to Curriculum Overview

[← Back to EDUCATION.md](../EDUCATION.md)
