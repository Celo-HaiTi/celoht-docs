# Operations Runbooks

These runbooks describe the evidence-based operational boundary for CeloHT. They are procedures for the current testnet-oriented system, not proof that production infrastructure exists. Record the incident, affected network, component, operator, timestamps, and evidence for every action.

## Deployment

1. Confirm the target is Celo Sepolia (`11142220`); Mainnet is unavailable until an official Mainnet manifest, audit, governance authority, and approval exist.
2. Run the owning repository checks: contracts compile/tests, indexer typecheck/tests/build, backend typecheck/lint/tests/build, admin checks, and dApp contract sync/typecheck/lint/tests/build.
3. Review the contracts deployment manifest and verify USDm, treasury, contract addresses, deployment blocks, and verification status.
4. Deploy only through the owning repository’s reviewed scripts with an explicitly configured environment and funded deployer.
5. Update the traceable deployment metadata and synchronize the dApp ABIs/addresses and indexer manifest.
6. Record the release commit, network, transaction hashes, operator, and verification result.

## Rollback

- **dApp/admin/backend:** redeploy the last known-good artifact after preserving logs and identifying the bad release.
- **Indexer:** stop the worker, preserve the checkpoint, correct the configuration or code, then resume from the last safe checkpoint. Reconcile affected rows before marking recovery complete.
- **Database:** use the Supabase backup and migration rollback procedure owned by the database operators. Do not edit indexed rows manually without an audit record.
- **Contracts:** deployed bytecode is not rolled back. Disable the affected application flow, preserve evidence, and follow the contract incident procedure. A replacement deployment requires review and new metadata.

## RPC outage

1. Confirm the failure from the indexer `/health` and `/readyz` checks and a second RPC provider.
2. Stop writes or switch only to an already reviewed RPC configuration; never bypass network and chain-ID validation.
3. Keep user-facing state as pending or unavailable; do not fabricate confirmations.
4. Resume indexing from the durable checkpoint after RPC health returns and reconcile the block range.

## Indexer outage

1. Mark indexed metrics unavailable or stale in dependent services.
2. Preserve the last checkpoint, logs, and failing block or transaction.
3. Check ABI, network, RPC, Supabase, and startup validation errors.
4. Restart only after the cause is understood; run a bounded backfill and compare event counts and transaction provenance.

## Database outage

1. Confirm Supabase availability and connection health without exposing service-role credentials.
2. Put writes into an unavailable or retryable state; never route sensitive data to an unapproved store.
3. Restore from the approved backup or provider recovery procedure, then validate RLS, migrations, ownership boundaries, and audit-log integrity.
4. Reconcile indexer checkpoints and backend writes before reopening workflows.

## Compromised admin

1. Disable the affected account/session and rotate exposed credentials or links.
2. Preserve authentication, audit, Supabase, and deployment logs.
3. Review role changes, service-role use, treasury actions, exports, and data access since the last trusted point.
4. Restore least privilege, verify RLS and immutable audit logging, and document affected users or records.

## Incorrect indexed data

1. Identify the source block, transaction hash, log index, and affected derived records.
2. Compare against the verified contract ABI and chain RPC; do not treat backend or dashboard values as on-chain truth.
3. Stop or isolate downstream reports if the error can change a public metric.
4. Correct by replaying from the last safe checkpoint or an approved bounded range, preserving an audit record of the correction.

## Chain reorganization

1. Detect competing block hashes or changed event ancestry at the affected height.
2. Pause finalization and downstream publication for the affected range.
3. Rewind to the last finalized checkpoint supported by the indexer configuration, then rescan.
4. Reconcile transaction, event, and derived rows and record the chosen confirmation policy.

## Contract incident

1. Treat suspected unauthorized calls, incorrect payment splits, role compromise, or unexpected state as a security incident.
2. Stop affected application flows and preserve RPC, deployment, wallet, and audit evidence.
3. Confirm whether the affected deployment is testnet or Mainnet; current CeloHT evidence shows only Celo Sepolia deployment.
4. Use only documented, contract-supported controls. Do not claim a pause or upgrade path unless the deployed contract exposes and the manifest verifies it.
5. Notify maintainers and affected stakeholders, complete independent review, and publish remediation status before restoring a flow.

## Ownership boundary

The indexer owns blockchain-derived tables and checkpoints. The backend owns application workflows, authentication, KYC, admin actions, and audit writes. The admin presents authorized data and must label mock or unavailable states. The dApp signs user transactions and never receives service-role credentials.
