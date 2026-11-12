# Agent Identity

## Two registries, two identities

CeloHT and ERC-8004 serve different purposes:

- The **CeloHT Agent Registry** records a CeloHT agent ID, the wallet that
  registered it, active status, and a `verified` flag set by an authorized
  role to reflect an off-chain verification result.
- The **ERC-8004 Identity Registry** mints an ERC-721 identity. Its token ID
  is the ERC-8004 `agentId`; its URI points to a registration file. The NFT
  owner can transfer the identity and may authorize an operator.

The IDs are independent and must never be treated as interchangeable. In the
reviewed CeloHT contract source, the CeloHT agent ID is wallet-bound; the
ERC-8004 identity is a transferable token. The proposed identity-link adapter
maps one ID from each registry but does not merge, transfer, or synchronize
their state. Its source is not yet deployed.

## What identity verification means

ERC-8004 identity proves that a wallet controls an ERC-721 token at a specific
registry on a specific chain. It does **not** attest to the token owner's
government identity, training, service quality, or safety. CeloHT's
verification process remains off-chain; its registry flag is an administrative
record of that process, not the process itself.

The ERC-8004 registration file can publish a human-readable name, description,
image, services, and trust mechanisms. Treat these as owner-published claims.
Validate the file and verify its relationship to the on-chain token; do not
present advertised capabilities as independently confirmed.

## Wallet and ownership fields

The ERC-8004 identity owner is the ERC-721 owner. URI and metadata changes
must be authorized by the owner or an approved operator, as enforced by the
Identity Registry. The optional ERC-8004 `agentWallet` is a payment/contact
wallet field, not proof of legal identity and not the CeloHT registered
wallet.

Changing `agentWallet` requires a signature from the proposed wallet using
the standard's EIP-712 flow for externally owned accounts or ERC-1271 for
smart-contract wallets. When the ERC-721 token is transferred, the standard
registry clears the previous `agentWallet`; it must be verified again by the
new owner.

If a CeloHT/ERC-8004 link is used after the adapter is deployed, consumers
must check its live authorization/ownership status. A token transfer can make
the stored link stale without transferring the CeloHT registration. Do not
rely on a past link event alone.

## Chain-scoped discovery

An ERC-8004 identity reference includes the EVM namespace, chain ID, Identity
Registry address, and token ID. Therefore, an `agentId` without its chain and
registry context is not a globally unique identifier.

Discoveries should combine registry events with current reads:

- Follow `Registered`, ERC-721 `Transfer`, `URIUpdated`, and `MetadataSet`
  events.
- Re-read current ownership, URI, relevant metadata, and CeloHT status from
  the respective registries.
- Treat event-derived indexes as rebuildable views, not authoritative current
  ownership.
- Do not infer identity or service verification from the presence of an NFT.

The CeloHT API documentation is a planned interface, and no CeloHT dApp
directory or indexer for ERC-8004 is verified by this documentation
repository.

## References

- [Integration overview](./ERC8004_INTEGRATION.md)
- [Registration flow](./AGENT_REGISTRATION.md)
- [CeloHT Agent Network](./AGENT_NETWORK.md)
- [ERC-8004 identity specification](https://eips.ethereum.org/EIPS/eip-8004#identity-registry)
