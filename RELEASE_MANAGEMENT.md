# Release Management

## Versioning

All CeloHT repositories follow [Semantic Versioning](https://semver.org/): `MAJOR.MINOR.PATCH`.

- **MAJOR** — breaking changes (e.g. API v1 → v2, incompatible contract upgrade)
- **MINOR** — new functionality, backward-compatible
- **PATCH** — bug fixes, backward-compatible

## Release Cadence

- **Documentation** (this repository): released as meaningful content batches are completed and validated, not on a fixed calendar — see [CHANGELOG.md](./CHANGELOG.md)
- **dApp/Website:** continuous deployment to staging on merge to `main`; production releases roughly bi-weekly or as critical fixes require
- **Smart contracts:** released only after the full audit and testnet trial process in [SMART_CONTRACTS.md](./SMART_CONTRACTS.md#path-to-production) — no fixed cadence, correctness over schedule

## Release Process

1. All changes for the release merged to `main` via reviewed PRs (see [DEVELOPER_GUIDE.md](./DEVELOPER_GUIDE.md#code-review))
2. CI validation passes fully (see [DEVELOPER_GUIDE.md](./DEVELOPER_GUIDE.md#cicd))
3. Version bumped per semantic versioning rules above
4. `CHANGELOG.md` updated with the new version section, following [Keep a Changelog](https://keepachangelog.com/en/1.1.0/) format
5. Git tag created matching the version
6. For dApp/Website: production deployment per [DEPLOYMENT.md](./DEPLOYMENT.md)
7. For contracts: deployment per the elevated process in [SMART_CONTRACTS.md](./SMART_CONTRACTS.md#path-to-production)

## Breaking Changes

Breaking changes (API, SDK, or contract interface changes) require:
- A deprecation notice at least 90 days before the old version is retired (see [API_REFERENCE.md](./API_REFERENCE.md#versioning))
- Clear migration documentation published alongside the new version
- Maintainer Council awareness for changes with significant ecosystem impact (see [GOVERNANCE.md](./GOVERNANCE.md))

## Hotfix Process

Critical security or functional fixes may bypass the standard release cadence but never bypass code review or testing requirements — see [SECURITY.md](./SECURITY.md#incident-response) for the security-specific response timeline.

## Release Communication

Releases affecting users or developers are announced via the blog (see [BLOG_GUIDE.md](./BLOG_GUIDE.md)) and relevant community channels (see [COMMUNITY.md](./COMMUNITY.md)).

## References

- [CHANGELOG.md](./CHANGELOG.md)
- [DEVELOPER_GUIDE.md](./DEVELOPER_GUIDE.md)
- [DEPLOYMENT.md](./DEPLOYMENT.md)
- [SMART_CONTRACTS.md](./SMART_CONTRACTS.md#path-to-production)
