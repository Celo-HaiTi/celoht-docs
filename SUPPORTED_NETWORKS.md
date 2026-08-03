# Supported Networks

## Overview

CeloHT operates exclusively on the Celo blockchain and its standard network tiers. CeloHT does not support or plan to support other blockchain networks — this is a deliberate scope decision to keep the system simple, auditable, and consistent with the non-custodial, minimal-footprint design in [ARCHITECTURE.md](./ARCHITECTURE.md#design-principles).

## Networks

| Network | Chain ID | Purpose | Status |
|---|---|---|---|
| Celo Alfajores (testnet) | 44787 | Development, staging, agent training simulations | Active |
| Celo Mainnet | 42220 | Production | Live only after audit process (see [SMART_CONTRACTS.md](./SMART_CONTRACTS.md#path-to-production)) |

## RPC Endpoints

Developers should use their own RPC provider or a public Celo RPC endpoint; CeloHT does not operate a proprietary RPC service. See [DEVELOPER_GUIDE.md](./DEVELOPER_GUIDE.md#environment-variables) for configuration.

## Why Not Multi-Chain

A multi-chain approach would increase attack surface, complicate the audit process, and fragment the Agent Network's verification model (a single [AgentRegistry](./SMART_CONTRACTS.md#agentregistry--reference-specification) is simpler to reason about and monitor than several). If this changes in the future, it would go through the full RFC process in [GOVERNANCE.md](./GOVERNANCE.md#decision-making-process), given the architectural significance.

## Network Configuration Reference

```
Alfajores:
  Chain ID: 44787
  Currency: CELO
  Explorer: (public Celo Alfajores explorer)

Mainnet:
  Chain ID: 42220
  Currency: CELO
  Explorer: (public Celo Mainnet explorer)
```

## References

- [CELO.md](./CELO.md)
- [ARCHITECTURE.md](./ARCHITECTURE.md)
- [DEVELOPER_GUIDE.md](./DEVELOPER_GUIDE.md)
- [DEPLOYMENT.md](./DEPLOYMENT.md)
