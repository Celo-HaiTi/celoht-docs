# Agent Payments

## CeloHT service payments remain separate

ERC-8004 does not define a payment or settlement protocol. CeloHT's existing
`CeloHTServicePayments` contract is a separate service-payment mechanism and
uses the wallet recorded in the CeloHT Agent Registry. The ERC-8004
`agentWallet` field and the ERC-8004/CeloHT identity link do not update that
recipient.

The reviewed service-payment interface exposes
`payForService(serviceType, agentId)`, `priceOf(serviceType)`, and
`getPayment(paymentId)`. In the contract source, a paid service pulls USDm
from the customer to the registered agent wallet and treasury. The default
agent share is 80% and is configurable by an authorized role; the treasury
receives the remainder. Read the live price and split before presenting a
quote. Reforestation assistance is configured as free in the reviewed
implementation. These source-level facts are not proof that the dApp exposes
or supports a working user payment flow.

## Intended customer payment sequence

This describes the contract boundary, not a verified CeloHT dApp walkthrough:

1. Select an active CeloHT agent and read the current service price and
   payment-token configuration from the authoritative deployment record.
2. Connect a wallet on the intended chain and verify the chain ID and
   contract code.
3. If the payment amount is nonzero, approve the required USDm allowance from
   the wallet to the verified Service Payments contract.
4. Call `payForService` with the service type and **CeloHT** agent ID. The
   contract checks that the agent exists and is active, then performs the
   configured distribution.
5. Wait for a confirmed receipt and reconcile the `ServicePaid` and
   `PaymentDistributed` events and the stored payment record. Do not show
   success before confirmation.

The current contract source and deployment manifest are maintained in the
[CeloHT smart-contract repository](https://github.com/Celo-HaiTi/celoht-smart-contracts).
The ERC-8004 integration itself has not yet been compiled/tested or proven by
live transactions. Consult
[CeloHT's deployment and payment evidence](https://github.com/Celo-HaiTi/celoht-smart-contracts/blob/c154568787f69a7ee9763c1418b724728909f5b1/deployments/celoSepolia.json)
and verify it again before any use.

## ERC-8004 wallet and payment metadata

ERC-8004 identity metadata may advertise an agent wallet. That metadata has
its own signature and ownership rules, and can be reset on NFT transfer. It
does not modify the CeloHT registry's wallet-bound agent entry or the
Service Payments recipient. An application must not substitute `agentWallet`
for the CeloHT wallet when paying for a CeloHT service.

The registration-file field `x402Support` is an advertisement. ERC-8004
feedback can include a proof-of-payment reference, but neither implements
x402. CeloHT's documented service-payment interface does not implement
agent-to-agent payments; those require a separately designed and reviewed
payment flow.

## Safety checks

- Never hardcode an address from an unverified message; load the
  chain-specific deployment manifest and confirm code and source.
- Verify the connected chain before approval or payment.
- Review the wallet prompt for the token, spender, amount, and transaction
  before signing.
- Treat token approvals as authority to spend; prefer the smallest required
  amount where supported and revoke unused approvals.
- Confirm actual on-chain receipt and payment distribution rather than
  trusting frontend status or an ERC-8004 feedback entry.

## References

- [Integration overview](./ERC8004_INTEGRATION.md)
- [Agent registration](./AGENT_REGISTRATION.md)
- [CeloHT Smart Contracts](./SMART_CONTRACTS.md)
- [CeloHT security policy](./SECURITY.md)
