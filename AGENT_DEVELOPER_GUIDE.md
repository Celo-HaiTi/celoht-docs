# Agent Developer Guide

## Audience and readiness

This guide describes the contract-level flow for developers evaluating
ERC-8004 with CeloHT. The CeloHT integration source is not yet demonstrated
end to end: the linked smart-contract repository says its ERC-8004 changes
have not yet been compiled/tested or exercised in live transactions; the
identity-link adapter is not deployed; and the dApp, backend, and indexer
integration is not present there. Do not treat this guide as a production
integration kit.

## Networks and configuration

| Network | Chain ID | Guidance |
|---|---:|---|
| Celo Sepolia | `11142220` | Test environment only. Run the read-only ERC-8004 preflight and verify the Validation implementation before relying on it. |
| Celo Mainnet | `42220` | Official registry deployments do not mean CeloHT is activated there. Do not submit CeloHT integration transactions. |

Load current registry and CeloHT contract addresses and ABIs only from the
authoritative versioned deployment manifests in the
[CeloHT smart-contract repository](https://github.com/Celo-HaiTi/celoht-smart-contracts).
The manifest is not a substitute for checking the live chain, code, registry
bindings, and explorer verification status. Never copy addresses from
untrusted metadata.

The reviewed repository provides `erc8004Config.ts` for chain-scoped
configuration and ABI definitions, and the read-only `check:erc8004` script
for validating registry deployments. These have not been verified by this
documentation task. Do not insert private keys into frontend code, metadata,
or RPC URLs.

## Registration and metadata

1. Have the intended wallet register with the CeloHT Agent Registry, if it is
   not registered. Read the on-chain `registrationFee()`; authorize only the
   required USDm amount if the fee is nonzero.
2. Call the official Identity Registry's `register()` from the intended NFT
   owner. Record its independent ERC-8004 ID from the confirmed transaction.
3. Create and validate the metadata with the contract repository's
   `createAgentRegistrationFile()` / `validateAgentRegistrationFile()` and
   JSON schema. Publish it at a durable URI, then set the URI with
   `setAgentURI()`.
4. Read back `ownerOf()` and `tokenURI()`, resolve and validate the metadata,
   and check that its chain/registry/ID reference matches the identity.
5. Do not advertise a CeloHT/ERC-8004 link until the identity-link adapter
   has been deployed, source-verified, and tested. Its intended function is
   `linkAgentIdentity(celoHTAgentId, erc8004AgentId)`.

The CeloHT and ERC-8004 IDs are separate values. `agentWallet` does not
replace the CeloHT registered wallet.

## Discovery

Use ERC-8004 events (`Registered`, `Transfer`, `URIUpdated`, and
`MetadataSet`) to build a candidate index, then resolve current identity
state from the correct chain and registry. Verify the registration file
before displaying it. For CeloHT status, read the CeloHT Agent Registry
separately. If the identity-link adapter becomes available, re-check
`isLinkOwnerCurrent()` and do not trust link events as current ownership.

There is no verified CeloHT ERC-8004 indexer or directory UI. The planned
API in [API_REFERENCE.md](./API_REFERENCE.md) is not an available discovery
service.

## Feedback and validation

- Feedback: use `giveFeedback()` with the ERC-8004 ID and defined value scale;
  read history and summaries with `readFeedback()`, `readAllFeedback()`, and
  `getSummary()`. Apply reviewer filters and disclose aggregation rules.
  Owner/operator feedback is rejected by the registry.
- Validation: an authorized owner/operator requests validation with
  `validationRequest()` and evidence URI/hash. The named validator submits
  `validationResponse()`. Read the event history as well as current status;
  a request is not a validation result.
- Both transactions are signed by the connected wallet. The contract
  repository's interfaces and configuration list these methods, but no
  CeloHT integration write has been demonstrated.

## Service payments

For an existing CeloHT service, the contract interface is
`payForService(serviceType, celoHTAgentId)`. Use the CeloHT ID, not the
ERC-8004 ID. Read the configured price and current split, approve the verified
USDm spender if needed, submit through the wallet, and verify confirmed
payment/distribution events. ERC-8004 feedback does not settle payment.

The current CeloHT payment interface does not provide direct agent-to-agent
payments. The CeloHT dApp payment UX and the ERC-8004 integration should not
be described as available until the application and live transaction flow
are demonstrated.

## References

- [Integration overview](./ERC8004_INTEGRATION.md)
- [Registration](./AGENT_REGISTRATION.md)
- [Identity](./AGENT_IDENTITY.md)
- [Reputation](./AGENT_REPUTATION.md)
- [Validation](./AGENT_VALIDATION.md)
- [Payments](./AGENT_PAYMENTS.md)
- [Security](./ERC8004_SECURITY.md)
- [Official ERC-8004 specification](https://eips.ethereum.org/EIPS/eip-8004)
