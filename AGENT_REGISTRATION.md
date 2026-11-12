# Agent Registration

## Registration is a two-registry process

An agent registered with CeloHT does not automatically receive an ERC-8004
identity, and an ERC-8004 identity is not a CeloHT agent registration.
Registration in both systems results in two distinct IDs.

The CeloHT `registerAgent()` function assigns the CeloHT ID to the connected
wallet. The reviewed implementation charges the current on-chain registration
fee in USDm when the fee is nonzero; read `registrationFee()` and check the
token allowance before calling. The amount is not a fixed value in this guide.
The CeloHT `verified` state is managed separately and reflects an off-chain
process.

The ERC-8004 Identity Registry's `register()` functions mint the transferable
identity token. The `agentId` returned by that registry is the ERC-8004 ID,
not the CeloHT ID. The CeloHT registration fee is separate from the ERC-8004
identity transaction. The ERC-8004 transaction requires network gas; verify
any registry-specific charge before submitting it.

## Intended Celo Sepolia sequence

This sequence documents the reviewed interface and contract source, not a
working CeloHT application flow. The CeloHT contract repository reports that
the integration has not yet been compiled, tested, or exercised in live
transactions; the identity-link adapter is not deployed.

1. Connect the agent's wallet to Celo Sepolia (`11142220`). Load registry
   addresses from the pinned [ERC-8004 deployment manifest](https://github.com/Celo-HaiTi/celoht-smart-contracts/blob/c154568787f69a7ee9763c1418b724728909f5b1/deployments/erc8004.json),
   not from user input or registration-file content.
2. Complete the existing CeloHT registration if needed. Read the current
   fee, confirm USDm allowance and balance, and verify the resulting
   `AgentRegistered` event and CeloHT record.
3. Call the official Identity Registry `register()` function from the
   intended owner wallet. Obtain the ERC-8004 `agentId` from the receipt/event
   and verify current ownership with `ownerOf(agentId)`.
4. Build the registration file using the ERC-8004 ID, identity registry, and
   chain. The reviewed helper exports `createAgentRegistrationFile()` and
   `validateAgentRegistrationFile()`; they validate/build JSON only and do
   not publish it or sign a transaction.
5. Validate the file against the
   [registration schema](https://github.com/Celo-HaiTi/celoht-smart-contracts/blob/c154568787f69a7ee9763c1418b724728909f5b1/schemas/erc8004-agent-registration.schema.json).
   Publish it at a durable HTTPS or content-addressed URI. Avoid personal or
   sensitive information.
6. Call `setAgentURI(agentId, uri)` from the owner or an approved operator.
   Resolve the URI and confirm that the file's `registrations` entry matches
   the chain ID, Identity Registry, and token ID. Check both `tokenURI()` and
   `ownerOf()` against current chain state.
7. Once the CeloHT identity-link adapter has been deployed and verified, the
   intended link action is `linkAgentIdentity(celoHTAgentId, erc8004AgentId)`.
   The CeloHT-registered wallet must also be an ERC-8004 owner or approved
   operator. The adapter has no verified deployment address or demonstrated
   transaction at this time; do not assume the call is available.

Because the ERC-8004 token ID is assigned by the `register()` transaction,
publishing a file that embeds that ID is generally a separate step. A user
interface must not label a profile complete until the URI is set, resolved,
and validated.

## Registration file requirements

The current CeloHT helper schema requires `type`, `name`, `description`,
`image`, `services`, `x402Support`, `active`, and at least one `registrations`
entry. The `type` is the ERC-8004 registration-v1 URI. Each registration
reference contains `agentId` and `agentRegistry` in the
`eip155:<chainId>:<identityRegistry>` form. `supportedTrust` is optional.
This format is not evidence that a service endpoint, x402 payment, or trust
mechanism is live.

Use the CeloHT smart-contract repository's builder and schema as the source
for implementation details; this documentation does not include executable
transaction code because the integration has not passed its compile/test
gate.

## Ownership and discovery checks

- Only the wallet connected to the expected chain should authorize changes.
- Confirm token owner/operator permissions before changing the URI or metadata.
- Re-check ownership and link validity on every security-sensitive read.
- Index `Registered`, `Transfer`, `URIUpdated`, `MetadataSet`,
  `AgentRegistered`, and, after deployment, adapter link/unlink events.
- Preserve chain ID, registry address, transaction hash, block, and log index
  for indexed records.
- Never infer success from a submitted transaction alone; check the confirmed
  receipt and read the resulting contract state.

## References

- [Agent identity](./AGENT_IDENTITY.md)
- [Integration overview](./ERC8004_INTEGRATION.md)
- [Security guidance](./ERC8004_SECURITY.md)
- [ERC-8004 registration specification](https://eips.ethereum.org/EIPS/eip-8004#agent-uri-and-agent-registration-file)
