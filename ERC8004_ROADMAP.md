# ERC-8004 Roadmap and Frontier Pool Readiness

## Current status

As of 2026-11-12, the linked CeloHT smart-contract repository contains
ERC-8004 interfaces, configuration, metadata helpers, and identity-link
adapter source. The same repository says the integration changes have not
yet been compiled, tested, exported, or verified with live transactions.
The adapter is a separate manual Sepolia deployment with no verified
deployment record in the reviewed source. The dApp, backend, and indexer
integration is not present there.

The official registries have address entries for Celo Sepolia (`11142220`)
and Celo Mainnet (`42220`); this is not evidence of CeloHT Mainnet activation.
The deployment manifest flags the Celo Sepolia Validation implementation as
not source-verified. No external security audit is claimed.

## Readiness matrix

| Area | Evidence/status | Remaining gate |
|---|---|---|
| ERC-8004 integration | Interfaces, configuration, and metadata helpers exist in the linked contract repository. The repository says this change has not been compiled, tested, or exercised live. | Compile, run tests and chain preflight, confirm registry bindings, then complete wallet-signed test transactions and record receipts. |
| Agent identity | Official Identity Registry and separate CeloHT/ERC-8004 ID-link source are documented. | Deploy and source-verify the link adapter on Sepolia; prove ownership, stale-link, unlink/relink, and transfer cases. |
| Agent reputation | Interface includes feedback, reads, summaries, revocation, and responses. | Demonstrate wallet-signed feedback, correct filters, revocation, event indexing, evidence verification, and abuse handling. |
| Agent validation | Interface supports requests, responses, and summaries. Sepolia Validation implementation source is flagged unverified in the manifest. | Verify implementation and registry binding; test independent request/response transactions, history, zero-score handling, and evidence provenance. |
| Agent-to-agent payments | Not provided by ERC-8004 or the reviewed CeloHT `payForService` interface. | Requires a separately designed, implemented, tested, and reviewed payment flow. Do not demonstrate as existing functionality. |
| CeloHT service payments | CeloHT service-payment source and Sepolia manifest are separate from ERC-8004. Payment uses the CeloHT agent wallet. | Demonstrate with a real, confirmed Sepolia payment and show that ERC-8004 `agentWallet` does not alter the recipient. |
| Application discovery | No verified CeloHT ERC-8004 directory, backend, or indexer. | Build and test discovery that validates metadata and re-reads current chain state; include reorg handling and privacy-safe display. |
| Mainnet | Official ERC-8004 registry addresses exist on Celo Mainnet. No CeloHT Mainnet activation is demonstrated. | Complete all testnet gates, governance approval, verified deployment/configuration, and production security requirements first. |
| Independent audit | No independent external audit is documented. | Commission an independent review of the deployed integration and related application/indexer flows; remediate findings and publish the scope/result. |

## Demonstration requirements

A credible testnet demonstration should use the supported Celo Sepolia
network, disclose that it is testnet-only, and retain verifiable transaction
hashes and receipts. It should show:

1. CeloHT registration and separate ERC-8004 identity registration, with both
   IDs and their registry context clearly distinguished.
2. A validated registration file whose on-chain URI and token owner are read
   back from the chain.
3. Adapter link creation only after a real Sepolia deployment, plus handling
   for an ERC-721 transfer that makes a link stale.
4. Agent discovery with chain/registry context and current CeloHT status.
5. Wallet-signed feedback, readable provenance, revocation, and clear
   Sybil-related limitations.
6. A validator request and an independent validator response with published
   methodology, evidence, and response history.
7. A CeloHT service payment, if included, showing its existing CeloHT agent
   wallet recipient and explicitly distinguishing it from ERC-8004 metadata.
8. Failure cases: wrong chain/address, invalid metadata, rejected
   authorization, unavailable URI, pending validation, reorganization, and
   unavailable registry.

Mock data, screenshots without transaction evidence, or registry code presence
alone do not demonstrate the integration.

## Mainnet requirements

Before any CeloHT Mainnet activation:

- Confirm the exact code, ABIs, registry addresses, proxy implementations,
  network ID, and verified source from authoritative manifests and live
  explorers.
- Complete compile, unit/integration tests, read-only preflight, and
  wallet-signed end-to-end testnet transactions for identity, linking,
  reputation, validation, discovery, and payments.
- Complete the documented minimum 90-day monitored testnet period and
  publish results.
- Transfer privileged CeloHT roles to the reviewed governance/Safe authority
  and independently confirm the on-chain role state.
- Complete an independent third-party security audit of the deployed
  contracts and relevant dApp, backend, and indexer components; remediate
  findings and publish the audit and remediation record.
- Complete privacy, RPC, indexing/reorg, incident response, and operational
  readiness reviews.
- Obtain the documented governance and release approvals. No single
  configuration file, registry deployment, or successful test substitutes
  for these gates.

## Frontier Pool readiness statement

This documentation does **not** claim that CeloHT currently meets Frontier
Pool readiness requirements for ERC-8004 identity, reputation, validation,
agent-to-agent payments, a production demonstration, Mainnet activation, or
independent security audit. Those areas remain incomplete or unverified as
described above. Readiness should be reassessed only against published
implementation, transaction, deployment, governance, and audit evidence.

## References

- [ERC-8004 integration](./ERC8004_INTEGRATION.md)
- [Developer guide](./AGENT_DEVELOPER_GUIDE.md)
- [Security requirements](./ERC8004_SECURITY.md)
- [CeloHT supported networks](./SUPPORTED_NETWORKS.md)
- [CeloHT smart-contract repository](https://github.com/Celo-HaiTi/celoht-smart-contracts)
