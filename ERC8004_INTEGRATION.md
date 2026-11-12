# ERC-8004 Integration

## Status and scope

ERC-8004 defines interoperable registries for agent identity, reputation, and
validation. It is a draft standard, not a CeloHT application or payment
protocol. CeloHT's intended integration keeps the existing CeloHT Agent
Registry and Service Payments separate and uses the official ERC-8004
registries for portable agent identity and trust signals.

**This integration is not yet demonstrated end to end.** The linked
[CeloHT smart-contract repository](https://github.com/Celo-HaiTi/celoht-smart-contracts)
contains ERC-8004 interfaces, network configuration, registration-file
helpers, and source for an identity-link adapter. Its latest reviewed
[integration evidence](https://github.com/Celo-HaiTi/celoht-smart-contracts/blob/c154568787f69a7ee9763c1418b724728909f5b1/ERC8004_INTEGRATION.md)
and [repository status](https://github.com/Celo-HaiTi/celoht-smart-contracts/blob/c154568787f69a7ee9763c1418b724728909f5b1/README.md)
state that the ERC-8004 changes have not yet been compiled, tested, exported,
or exercised in live transactions. The link adapter is a separate manual
Sepolia deployment and has no deployment record in the reviewed source.
There is no verified dApp, backend, or indexer integration in that repository.

This documentation therefore describes the intended contract boundaries and
the functions present in the reviewed interfaces. It is not a claim that an
agent can currently complete these actions in the CeloHT dApp.

## Registry responsibilities

| Component | Responsibility | Relationship |
|---|---|---|
| ERC-8004 Identity Registry | Mints a transferable ERC-721 agent identity and points to its registration file. | Owns the ERC-8004 `agentId`; this is not the CeloHT agent ID. |
| ERC-8004 Reputation Registry | Records feedback and supports filtering, summaries, revocation, and responses. | Feedback is a trust signal, not a payment or guarantee. |
| ERC-8004 Validation Registry | Records a request to a named validator and the validator's response. | A request is not a completed or independent validation. |
| CeloHT Agent Registry | Records the CeloHT registration, wallet, active state, and a flag reflecting an off-chain verification decision. | Remains the source of CeloHT eligibility and the existing CeloHT agent ID. |
| CeloHT Service Payments | Accepts existing CeloHT service payments and distributes them to the registered agent wallet and treasury. | ERC-8004 identity and wallet metadata do not change its recipient logic. |
| CeloHT identity-link adapter | Source code defines a one-to-one link between CeloHT and ERC-8004 IDs. | The reviewed adapter source is not deployed; the link is not currently usable on-chain. |

The CeloHT verification flag is not an identity document check performed by
either registry. CeloHT identity screening remains an off-chain operational
process. ERC-8004 NFT ownership proves control of that on-chain token, not a
person's legal identity, competence, or trustworthiness.

## Network configuration

| Network | Chain ID | ERC-8004 registry state | CeloHT state |
|---|---:|---|---|
| Celo Sepolia | `11142220` | Official Identity, Reputation, and Validation registry addresses are present in the pinned deployment manifest. The manifest flags the Validation implementation source as unverified. | The contract repository records the existing CeloHT contracts on Sepolia. ERC-8004 integration changes are not yet validated end to end; the identity-link adapter is not deployed. |
| Celo Mainnet | `42220` | Official registry addresses are present in the deployment manifest. | No CeloHT Mainnet activation or integration is demonstrated. Do not use Mainnet for this integration. |

Registry addresses are intentionally not duplicated in this overview. Obtain
them from the pinned
[ERC-8004 deployment manifest](https://github.com/Celo-HaiTi/celoht-smart-contracts/blob/c154568787f69a7ee9763c1418b724728909f5b1/deployments/erc8004.json)
and validate the live chain, code, registry bindings, and explorer source
status before use. Registry deployments on Mainnet do not mean CeloHT has
deployed or activated its own Mainnet contracts.

## Intended flow

1. Register in the CeloHT Agent Registry through its existing wallet and
   registration-fee process.
2. Register a separate ERC-8004 identity in the official Identity Registry.
   The registry assigns a distinct ERC-8004 `agentId`.
3. Publish an ERC-8004 registration file and set its URI on the identity.
4. When deployed and validated, the CeloHT link adapter can associate the two
   IDs after checking the CeloHT registered wallet and ERC-8004 owner/operator
   authorization.
5. Consumers discover identities from on-chain events and read current
   ownership, URI, and metadata. CeloHT-specific status remains sourced from
   the CeloHT registry.
6. Submit reputation feedback or validation requests directly to their
   official ERC-8004 registries. These actions do not modify CeloHT payment
   accounting.

See [Agent identity](./AGENT_IDENTITY.md),
[registration](./AGENT_REGISTRATION.md), [reputation](./AGENT_REPUTATION.md),
[validation](./AGENT_VALIDATION.md), and [payments](./AGENT_PAYMENTS.md) for
the separate flows and constraints.

## Payments are separate

ERC-8004 does not define payment settlement. Its registration file can
advertise x402 support, and feedback files may carry a proof-of-payment
reference, but these fields do not implement x402 or a CeloHT payment route.
CeloHT Service Payments continue to use the wallet in the CeloHT registry.
An ERC-8004 `agentWallet` update does not reroute those payments. Direct
agent-to-agent payments are not implemented by the documented Service
Payments interface.

## Readiness boundary

Before describing the integration as usable, CeloHT must compile and test the
integration, run registry preflight checks, complete real wallet-signed
Sepolia transactions, deploy and verify the link adapter, and demonstrate
discovery and indexing in the application. Production use additionally
requires the mainnet, governance, and independent security-review gates in
[ERC-8004 roadmap](./ERC8004_ROADMAP.md) and
[security guidance](./ERC8004_SECURITY.md).

## References

- [ERC-8004 specification](https://eips.ethereum.org/EIPS/eip-8004) (Draft)
- [Official ERC-8004 contracts](https://github.com/erc-8004/erc-8004-contracts)
- [CeloHT Agent Network](./AGENT_NETWORK.md)
- [CeloHT Smart Contracts](./SMART_CONTRACTS.md)
- [Supported networks](./SUPPORTED_NETWORKS.md)
