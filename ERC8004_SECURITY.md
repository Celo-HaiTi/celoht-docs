# ERC-8004 Security

## Security status

No independent security audit of the CeloHT ERC-8004 integration is
documented. The linked CeloHT smart-contract repository reports that its
ERC-8004 changes have not yet been compiled, tested, or exercised in live
transactions. Its integration security review is a scoped engineering review,
not an independent audit or production certification.

The official registry deployments are separate from CeloHT contracts. The
pinned CeloHT deployment manifest records their addresses and source-status
flags. It marks the Celo Sepolia Validation implementation source as
unverified. Verify the proxy implementation and its binding to the intended
Identity Registry before relying on that registry. Mainnet registry presence
does not make the CeloHT integration production-ready.

## Wallet ownership and permissions

- Distinguish the CeloHT registered wallet, the ERC-721 identity owner,
  approved operators, and optional ERC-8004 `agentWallet`.
- Require the expected owner/operator authorization for identity URI and
  metadata changes and validation requests.
- `agentWallet` changes require the standard EIP-712 proof for an EOA or
  ERC-1271 for a smart-contract wallet. Do not treat this as NFT transfer or
  CeloHT wallet reassignment.
- ERC-721 transfers can clear `agentWallet` and make an existing CeloHT
  identity link stale. Re-read state and check live link authorization.
- Keep identity and verification data minimal. Do not publish government
  identifiers, private contact details, secrets, or sensitive user records in
  public metadata or feedback.

## Transaction signing and permissions

Transactions must be reviewed and signed in the user's wallet. A backend may
prepare data or index confirmed events; it must not claim to have signed on a
user's behalf or create success-shaped records before chain confirmation.
Review the chain, target contract, function, token, allowance/spender, and
amount before signing. Do not store private keys or seed phrases in
application code or public RPC configuration.

The CeloHT identity-link adapter source checks the CeloHT wallet and ERC-8004
owner/operator authorization and enforces one-to-one links. The source is not
deployed or validated in a live integration; these checks must not be treated
as active protection until deployment and tests are verified.

## Contract and RPC verification

Before constructing a write-capable client:

1. Require the expected chain ID (`11142220` for Celo Sepolia; `42220` for
   Celo Mainnet).
2. Load addresses and ABIs from the pinned authoritative manifest; reject
   unknown networks and arbitrary address overrides.
3. Check non-empty code at all three ERC-8004 registries and confirm
   Reputation and Validation point to the configured Identity Registry.
4. Check proxy implementation addresses and implementation source status,
   not only whether the proxy has code or a verified proxy shell.
5. Confirm the deployment manifest and explorer status are current before
   signing. Re-run checks if the registry implementation changes.

Use a reputable HTTPS RPC provider or self-operated RPC. Protect provider
credentials; avoid logging query credentials. A bad or misconfigured RPC can
report a wrong chain, stale state, or misleading receipt. For important
actions, cross-check chain ID, transaction hash, and resulting state against
an independent explorer or provider. Handle confirmation depth and
reorganizations.

## Metadata, evidence, and privacy

Validate the registration file against the published schema and verify that
its `agentId` and registry reference match the on-chain token and chain.
Treat all fields and service URLs as untrusted input. Sanitize for display,
avoid fetching arbitrary URLs from privileged server contexts, apply size and
content-type limits, and guard against unsafe links and server-side request
forgery.

URIs and hashes do not guarantee that data will remain available, be truthful,
or be safe to render. Verify hashes over the exact payload bytes and use
durable content addressing where appropriate. Public chain events and
metadata are persistent; do not put personal or confidential information
on-chain or in public content.

## Reputation and validation abuse

ERC-8004 reputation is permissionless and can be Sybil-manipulated. Do not
present raw totals or averages as verified trust. Define and disclose
reviewer filters, preserve revocations and responses, and do not infer
successful payment from a feedback item.

The requester selects a validation address; the registry cannot ensure
independence, expertise, economic security, or correct results. Disclose
validator identity, conflicts, methodology, evidence hashes, and any updated
responses. A request is not a successful validation. Preserve the full event
history because a latest response can replace a prior response.

## Known limitations and release gates

- ERC-8004 integration has not passed compile/test or live write validation
  in the reviewed CeloHT repository.
- The identity-link adapter has no verified deployment record.
- Celo Sepolia Validation implementation source verification is flagged
  incomplete in the CeloHT manifest.
- No CeloHT dApp, backend, indexer, metadata storage, or reorg-handling
  integration is demonstrated by this documentation repository.
- Reputation and validator independence remain application-level risks.
- No independent external audit is claimed, and CeloHT Mainnet activation is
  not demonstrated.

See [SECURITY.md](./SECURITY.md), the [integration overview](./ERC8004_INTEGRATION.md),
and [roadmap readiness gates](./ERC8004_ROADMAP.md).

## References

- [ERC-8004 security considerations](https://eips.ethereum.org/EIPS/eip-8004#security-considerations)
- [CeloHT security policy](./SECURITY.md)
- [CeloHT threat model](./THREAT_MODEL.md)
