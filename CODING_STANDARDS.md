# Coding Standards

## General Principles

- Readability over cleverness — code is reviewed by contributors with varying experience levels, consistent with CeloHT's welcoming, education-first culture (see [CODE_OF_CONDUCT.md](./CODE_OF_CONDUCT.md))
- No secrets, credentials, or private keys in source code, ever — see [SECURITY.md](./SECURITY.md#secrets-management)
- Every function handling money movement or agent verification requires a code comment explaining *why*, not just what

## TypeScript / Frontend

- Strict mode required (`"strict": true` in `tsconfig.json`)
- No `any` type without an inline comment justifying it
- Components follow a consistent file structure: types → component → styles/exports
- All user-facing strings routed through the localization layer — no hardcoded English strings in components (see [TRANSLATION_GUIDE.md](./TRANSLATION_GUIDE.md))

```typescript
// Good
interface AgentStatusProps {
  agentAddress: string;
  status: AgentStatus;
}

export function AgentStatusBadge({ agentAddress, status }: AgentStatusProps) {
  // Verified badge reflects on-chain AgentRegistry status directly —
  // see SMART_CONTRACTS.md#agentregistry--reference-specification
  return status === 'Active' ? <VerifiedBadge /> : <UnverifiedBadge />;
}
```

## Solidity

- NatSpec comments required on all public/external functions — see the example in [SMART_CONTRACTS.md](./SMART_CONTRACTS.md#agentregistry--reference-specification)
- Explicit visibility modifiers always (no implicit `public`)
- Custom errors preferred over long `require` string messages where gas matters, balanced against clarity for auditors — comment the tradeoff where non-obvious
- No unbounded loops over dynamically-sized on-chain arrays (gas/DoS risk)

## Testing Requirements

- New logic requires new tests in the same PR — no "tests to follow" PRs, consistent with [DEVELOPER_GUIDE.md](./DEVELOPER_GUIDE.md#testing)
- Smart contract changes require both positive (expected behavior) and negative (access control, edge case) test cases — see the reference test suite in [SMART_CONTRACTS.md](./SMART_CONTRACTS.md#reference-test-suite-hardhat--chai--illustrative)

## Commit & PR Conventions

- Commit messages: `type(scope): short description` (e.g. `fix(agent-registry): correct recertification deadline check`)
- PRs follow the template in `.github/PULL_REQUEST_TEMPLATE.md`
- One logical change per PR — large, mixed-concern PRs are split on review request

## Linting & Formatting

- ESLint + Prettier for TypeScript/JavaScript, configuration committed to each repository
- `solhint` for Solidity
- CI blocks merge on lint failure — see [DEVELOPER_GUIDE.md](./DEVELOPER_GUIDE.md#cicd)

## References

- [DEVELOPER_GUIDE.md](./DEVELOPER_GUIDE.md)
- [SMART_CONTRACTS.md](./SMART_CONTRACTS.md)
- [SECURITY.md](./SECURITY.md)
