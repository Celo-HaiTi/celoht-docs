# Agent Reputation

## Purpose and limits

The ERC-8004 Reputation Registry records feedback associated with an
ERC-8004 `agentId`. It does not replace CeloHT's Agent Registry, verify
real-world identity, settle a payment, or guarantee an agent's future
behavior. Feedback is an input to a trust decision, not a certification.

The interface reviewed in the CeloHT smart-contract repository includes
`giveFeedback`, `readFeedback`, `readAllFeedback`, `getSummary`,
`revokeFeedback`, and `appendResponse`. The CeloHT integration changes have
not yet passed their compile/test or live transaction checks; confirm the
current target registry and ABI before any write.

## Submitting feedback

The standard `giveFeedback(agentId, value, valueDecimals, tag1, tag2,
endpoint, feedbackURI, feedbackHash)` call records a signed fixed-point score
and optional context:

- `value` is signed; `valueDecimals` represents the decimal scale and must be
  in the supported 0-18 range.
- Tags support filtering and are selected by the application; they do not
  make a score objective.
- `feedbackURI` can point to optional off-chain detail. Use a content-
  addressed URI or pair the URI with the content's `keccak256` hash.
- The feedback submitter must not be the agent owner or an approved operator.
  The registry enforces this rule; client-side checks are only for usability.

Feedback writes are wallet-signed calls to the official Reputation Registry.
The registry does not prove that the reviewer used a service or that the
feedback is truthful. Where a real CeloHT service payment is relevant, link
only to a confirmed transaction and preserve its chain and receipt evidence.
Do not fabricate payment evidence or infer payment from a UI state.

## Reading, revocation, and aggregation

`readFeedback` reads a specific item; `readAllFeedback` can filter by client
addresses and tags; `getSummary` returns an aggregate. ERC-8004 requires
client-address filtering for `getSummary` to reduce unfiltered Sybil/spam
aggregation. A summary is only meaningful with a stated reviewer selection,
tag policy, revocation policy, and explanation of how the score is
interpreted.

A client can revoke its own feedback with `revokeFeedback`. Revocation does
not erase the event history. `appendResponse` supports a response and
evidence pointer, but does not adjudicate a dispute or remove a rating.
Feedback indices are per agent/client and 1-based in the reviewed client
interface.

Index `NewFeedback`, `FeedbackRevoked`, and `ResponseAppended` events with
chain, Reputation Registry, agent ID, client address, and feedback index.
Preserve block, transaction, and log provenance; re-check current state
after a reorganization and validate off-chain evidence against its URI/hash.

## Abuse controls and known limitations

The standard makes feedback and reviewer addresses public, but does not
prevent Sybil accounts, collusion, purchased ratings, or misleading metadata.
Mitigations are application and governance responsibilities: disclose reviewer
selection, avoid presenting raw averages as trusted rankings, preserve
revocation and response history, and apply transparent filtering rules.
Do not claim a unique-person reputation system unless one is separately
implemented and demonstrated.

No CeloHT reputation UI, backend, indexer, or feedback transaction has been
verified here. ERC-8004 feedback does not escrow, refund, or settle USDm.

## References

- [Integration overview](./ERC8004_INTEGRATION.md)
- [CeloHT payments](./AGENT_PAYMENTS.md)
- [Security guidance](./ERC8004_SECURITY.md)
- [ERC-8004 Reputation Registry](https://eips.ethereum.org/EIPS/eip-8004#reputation-registry)
