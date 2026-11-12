# Agent Validation

## What validation records

The ERC-8004 Validation Registry records a request for a named validator and
the validator's response. It provides a common on-chain record and evidence
references; it does not itself execute a task, select an independent
validator, establish credentials, or guarantee that the validator's
conclusion is correct.

The reviewed CeloHT interface includes `validationRequest`,
`validationResponse`, `getValidationStatus`, `getSummary`,
`getAgentValidations`, and `getValidatorRequests`. The CeloHT integration has
not yet passed compile/test or live-transaction validation. In particular,
the CeloHT deployment manifest flags the Celo Sepolia Validation
implementation source as unverified; verify the proxy implementation and
identity-registry binding before relying on that network's Validation
Registry.

## Request and response

1. An ERC-8004 identity owner or approved operator calls
   `validationRequest(validatorAddress, agentId, requestURI, requestHash)`.
   The request URI should provide all inputs, outputs, and instructions needed
   for review. The request hash commits to the exact evidence payload bytes.
2. The designated validator independently reviews or re-executes the work,
   then calls
   `validationResponse(requestHash, response, responseURI, responseHash, tag)`.
   Only the requested validator may respond. The response is in the range
   0-100; optional response URI/hash fields point to the evidence.
3. Read the current status and preserve request/response events. A response
   may be updated, so the latest status alone does not represent the full
   judgment history.

The request hash must be unique for the deployed implementation. Use a
request-specific context or nonce when hashing repeated evidence; never
recycle a prior hash. The exact payload encoding and hash should be documented
so another party can reproduce it.

## Interpreting status and summaries

`getValidationStatus(requestHash)` returns the recorded validator, agent,
response, response hash, tag, and update time. An initial response value of
zero can be ambiguous with an answered zero score if the implementation does
not expose an explicit answered flag. Use the `ValidationResponse` event
history to distinguish a pending request from an actual zero response.

`getSummary` can aggregate answered requests using validator and tag filters.
Publish the validator set, methodology, evidence URI/hash, conflict policy,
and update history with any displayed summary. An on-chain request alone is
not a completed validation.

## Independence and evidence

The requester selects the validator; the registry does not enforce
independence, expertise, economic security, or correctness. ERC-8004 does not
provide validator staking, slashing, or incentives. CeloHT applications must
disclose conflicts and methods and avoid implying independent review unless
the validator and process support that claim.

Index `ValidationRequest` and `ValidationResponse` events by chain, registry,
request hash, agent, and validator. Preserve the transaction/block/log
provenance and handle chain reorganizations. Resolve evidence and verify its
hash before presenting it. Do not display a validation success until a
confirmed response event exists.

No CeloHT validator network, validation UI, indexer, or live validation
transaction is demonstrated by this documentation. The Sepolia Validation
implementation verification gap is a blocker for relying on that deployment.

## References

- [Integration overview](./ERC8004_INTEGRATION.md)
- [Security guidance](./ERC8004_SECURITY.md)
- [ERC-8004 Validation Registry](https://eips.ethereum.org/EIPS/eip-8004#validation-registry)
