# SDK

> **Status:** Specification for the planned `@celoht/sdk` package — see [ROADMAP.md](./ROADMAP.md). Verify current published version against npm before relying on specific APIs.

## Installation

```bash
npm install @celoht/sdk
```

## Initialization

```typescript
import { CeloHT } from '@celoht/sdk';

const client = new CeloHT({
  network: 'alfajores', // or 'mainnet'
  apiUrl: 'https://api.celoht.com/v1',
});
```

## Education Module

```typescript
const modules = await client.education.listModules();
const progress = await client.education.getProgress(userAddress);
await client.education.completeModule(userAddress, moduleId);
```

## Agent Network Module

```typescript
const nearby = await client.agents.nearby({ lat: 18.5944, lng: -72.3074, radiusKm: 10 });
const status = await client.agents.getStatus(agentAddress); // cross-references on-chain AgentRegistry
```

## Metrics Module

```typescript
const summary = await client.metrics.summary();
const reforestation = await client.metrics.reforestation();
```

## Contract Bindings

```typescript
import { getAgentRegistry } from '@celoht/sdk/contracts';

const registry = getAgentRegistry(client);
const isActive = await registry.isActiveAgent(agentAddress); // direct on-chain read
```

## Error Handling

```typescript
try {
  await client.education.completeModule(userAddress, moduleId);
} catch (err) {
  if (err.code === 'RATE_LIMITED') {
    // see API_REFERENCE.md#rate-limits
  } else if (err.code === 'UNAUTHORIZED') {
    // re-authenticate via wallet signature
  } else {
    throw err;
  }
}
```

## TypeScript Types

The SDK ships with full TypeScript definitions matching the schemas in [API_REFERENCE.md](./API_REFERENCE.md). No `@types/celoht-sdk` package is needed separately — types are bundled.

## Planned: Python SDK

A Python SDK (`celoht-sdk-py`) is planned for the medium-term roadmap (see [ROADMAP.md](./ROADMAP.md#medium-term-6–18-months)), primarily to support NGO and research partner data integrations.

## References

- [API_REFERENCE.md](./API_REFERENCE.md)
- [CLI.md](./CLI.md)
- [DEVELOPER_GUIDE.md](./DEVELOPER_GUIDE.md)
- [SMART_CONTRACTS.md](./SMART_CONTRACTS.md)
