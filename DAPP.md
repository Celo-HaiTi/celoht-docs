CeloHT dApp

«Status: This document defines the current intended product scope and architecture of the CeloHT dApp. Implementation status for any specific feature must be verified against the "celoht-dapp" repository, its README, CHANGELOG, tests, and current deployment/configuration evidence. This specification must not be interpreted as proof that every described feature is currently production-ready.»

Purpose

The CeloHT dApp is the application interface connecting users with CeloHT's supported financial, educational, agent, and reforestation functionality across on-chain and off-chain services.

The dApp is an application product, not a marketing landing page.

CeloHT has no native token and is not an investment product.

Core Product Areas

The current dApp scope is organized around:

- Wallet / Finance
- Education
- Agents
- Reforestation
- Activity / History

Features must only be presented as available when supported by the current implementation and required infrastructure.

---

User Flows

New User Onboarding

1. Explain CeloHT in plain language, including the No-Token Policy where relevant.
2. Connect a supported wallet.
3. Provide access to relevant educational content.
4. Allow the user to access supported financial, agent, or reforestation functionality.
5. Clearly communicate network, transaction, and configuration requirements before blockchain actions.

The onboarding flow must not imply that unsupported functionality is available.

Sending / Receiving USDm

Where the functionality is implemented and configured:

1. User selects the relevant send or receive action.
2. For receiving, the dApp may generate a payment QR code when supported.
3. For sending, the user can provide the recipient address through supported input methods.
4. The user enters the USDm amount.
5. The dApp displays relevant transaction information, including the network fee where it can be reliably determined.
6. The connected wallet requests transaction authorization.
7. The dApp displays transaction status and confirmation information based on verifiable blockchain state.

The dApp must never represent a transaction as successful before reliable confirmation is available.

Agent Interaction

Where agent functionality is implemented:

1. User accesses the agent directory.
2. User views available agent identity and verification information.
3. User initiates a supported agent-related workflow.
4. Relevant backend, indexer, blockchain, or verification dependencies are checked.
5. The dApp displays the resulting status using verified data.

Agent availability, verification, compliance, and transaction status must not be fabricated.

---

Authentication

- Basic wallet-based authentication may use a signature challenge.
- CeloHT does not require a custodial password-based wallet system for basic wallet interaction.
- Optional profile functionality may be used for supported application features such as education progress.
- Authentication and session behavior must follow the current backend and security implementation.

The dApp must never request seed phrases or private keys.

---

Wallet Connection

Wallet or method| State| Evidence / constraint
MiniPay| SUPPORTED when available| Supported when the dApp is opened inside MiniPay and the expected injected provider is available.
Valora| SUPPORTED| Supported through WalletConnect where the required integration is configured. Valora is a recommended wallet option but is not affiliated with CeloHT.
WalletConnect-compatible wallets| SUPPORTED when configured| Support depends on the wallet, WalletConnect configuration, network compatibility, and current implementation.
Custodial CeloHT wallet| UNSUPPORTED| CeloHT does not custody user private keys or request seed phrases/private keys.

Wallet compatibility does not by itself prove that backend, KYC, indexed-data, smart-contract, or Mainnet workflows are production-ready.

WalletConnect configuration must use the appropriate environment configuration, including:

"NEXT_PUBLIC_WALLETCONNECT_PROJECT_ID"

No secret or credential should be committed to the repository.

---

Supported Networks

The current network scope is:

Network| Purpose| Chain ID
Celo Mainnet| Production network| 42220
Celo Sepolia| Test / development network| 11142220

The dApp must clearly identify the active network.

Unsupported networks must not silently proceed with transactions.

Production Mainnet functionality must only be described as production-ready after the required external integration and security validation has been completed.

---

Assets

USDm

USDm is the current stable-asset terminology used by CeloHT for supported financial flows.

CELO

CELO is the Celo network asset used for network gas fees and applicable Celo network functions.

CeloHT Native Token

CeloHT does not have a native token.

CeloHT must not be presented as having:

- A CeloHT token
- Tokenomics
- An ICO
- A token sale
- An investment token

Historical Asset References

If historical asset terminology appears elsewhere in the documentation, it must not be presented as the current CeloHT asset model.

---

Education

Education is a core CeloHT product area.

The dApp may provide:

- Blockchain education
- Celo education
- Financial education
- Structured courses
- Learning modules
- Course progress
- Certificates where implemented and verified
- Recommended learning content

Education progress and certificates must be based on actual application data.

The dApp must not display fabricated:

- Student counts
- Completion rates
- Course counts
- Certificates
- Education impact statistics

---

Agents

Agents are a core CeloHT product area.

Supported functionality may include:

- Agent discovery
- Agent registration
- Agent profiles
- Agent identity information
- Agent verification
- Agent-related transactions
- Relevant DID or verification references where implemented

Agent information must come from a reliable source.

A displayed agent must not automatically be interpreted as verified unless the underlying verification state supports that claim.

---

Reforestation

Reforestation is a core CeloHT product area.

Where implemented, the dApp may support:

- Reforestation participation
- Donations or contributions
- Reforestation-related transactions
- Relevant records
- Certificates where implemented
- Activity/history associated with contributions

The dApp must not invent or fabricate:

- Trees financed
- Trees planted
- Planting locations
- Survival rates
- Partners
- Certificates
- Environmental impact metrics

Any public impact claim must be backed by an appropriate source of truth and reporting methodology.

---

Activity / History

The dApp may provide an activity or transaction-history surface for supported functionality.

Depending on implementation, this may include:

- Blockchain transactions
- Payment activity
- Reforestation contributions
- Agent-related activity
- Relevant indexed events

Activity data must be based on verifiable application, indexer, or blockchain data.

Pending, failed, and confirmed transactions must be clearly distinguished.

---

Impact Measurement and Public Reporting

CeloHT may maintain impact measurement and public reporting across its ecosystem.

This includes areas such as:

- Education outcomes
- Agent activity
- Reforestation activity
- Financial or ecosystem activity where reliable measurement is available

However:

«The CeloHT dApp does not require or define an Impact Dashboard.»

Impact measurement and public reporting are separate from the dApp's core product scope.

Appropriate reporting surfaces may include:

- Public reports
- CeloHT documentation
- Research materials
- Website reporting pages
- Verified public metrics

The existence of public impact reporting does not create a requirement for an Impact Dashboard inside the dApp.

---

Application Navigation

The dApp should remain focused on its core application functions.

Primary product areas:

- Wallet
- Learn
- Agents
- Reforest
- Activity / History

On mobile, the primary bottom navigation may focus on:

- Wallet
- Learn
- Agents
- Reforest

Activity/history should remain accessible through the appropriate application flows.

The dApp should not add unnecessary marketing or decorative surfaces merely to increase visual complexity.

---

Offline and Connectivity Behavior

Offline functionality must only be documented where it is actually implemented and tested.

Potential offline-friendly behavior may include:

- Cached education content
- Previously loaded static content
- Locally available payment information
- Clear pending states when connectivity is interrupted

Blockchain transactions must not be represented as submitted or completed while offline unless the actual implementation provides a reliable transaction-submission mechanism.

The dApp must never leave the user uncertain about whether a transaction was actually submitted.

---

Accessibility

The dApp should target WCAG 2.2 AA accessibility practices where applicable.

Accessibility requirements include:

- Keyboard accessibility where relevant
- Screen-reader compatibility
- Sufficient text readability
- Scalable text
- Accessible controls
- Clear transaction states
- Clear error messages
- Responsive layouts

Accessibility claims should be validated through actual testing rather than documentation alone.

---

Localization

The current localization target is:

- Kreyòl
- English
- French
- Spanish

Kreyòl is a primary language for the CeloHT audience.

Localization strings should be centrally managed where supported by the implementation.

The dApp must avoid partial or misleading translations in critical transaction and security flows.

Translation completion percentages must not be fabricated.

---

API and Data Integrations

The dApp may interact with:

- Celo blockchain/RPC infrastructure
- CeloHT backend/API services
- Supabase-backed services
- Indexer services
- Smart contracts
- Wallet integrations
- External verification services where explicitly supported

The exact integration status must be verified against current implementation and configuration.

A documented integration must not automatically be interpreted as a production-ready integration.

---

Architecture

The conceptual application architecture is:

CeloHT dApp
    |
    +--------------------+
    |                    |
    v                    v
Wallet / Blockchain   Backend / API
                           |
                           v
                       Supabase
                           |
                           v
                        Indexer
                           |
                           v
                    Celo RPC / Chain
                           |
                           v
                    Smart Contracts

Not every user flow necessarily passes through every layer.

Direct blockchain interactions should use verified network, asset, contract, and wallet configuration.

Backend and indexed-data flows must clearly distinguish cached/indexed information from direct blockchain state.

---

Backend Dependencies

Backend-dependent functionality may require:

- Supabase configuration
- Authentication/session configuration
- Rate limiting
- Redis/Upstash infrastructure
- Indexer availability
- Celo RPC availability
- Appropriate environment variables

Required external infrastructure must be configured and tested before a dependent feature is described as production-ready.

No secret values should be stored in "DAPP.md".

---

Supabase Dependencies

Where Supabase is used:

- Database configuration must be environment-specific.
- Required migrations must be applied in the correct order.
- Authentication/session behavior must be validated.
- Production credentials must never be committed.
- Staging and production environments must remain clearly separated.

---

Indexer Dependencies

Where indexed blockchain data is required, the indexer should provide reliable handling for:

- RPC connectivity
- Event indexing
- Confirmations
- Backfill
- Incremental synchronization
- Checkpointing
- Retry behavior
- Duplicate events
- Restart recovery
- Reorganization recovery

The dApp must not treat unavailable or stale indexer data as current confirmed blockchain state.

---

Smart Contract Integration

Smart-contract functionality must use verified:

- Contract addresses
- ABIs
- Network configuration
- Transaction parameters
- Deployment information

No placeholder contract addresses should be presented as real deployments.

No Mainnet or Celo Sepolia deployment should be described as verified without repository or deployment evidence.

---

Security

The dApp follows a fail-closed approach for security-sensitive operations.

Security requirements include:

- Never request seed phrases or private keys.
- Never store user private keys.
- Reject unsupported networks.
- Reject or block unverified assets.
- Validate transaction parameters before signing.
- Clearly display transaction status.
- Never claim success before reliable confirmation.
- Do not expose backend secrets in frontend code.
- Do not commit credentials.
- Protect authentication/session flows.
- Protect against wallet phishing and impersonation.
- Protect against transaction confirmation spoofing.

Security-sensitive functionality may require independent security review before production use.

---

Error Handling

The application should clearly handle, where applicable:

- Wallet connection rejection
- Unsupported wallet
- Wrong network
- RPC failure
- Transaction rejection
- Transaction failure
- Backend unavailable
- Supabase unavailable
- Indexer unavailable
- Missing environment configuration
- Unverified asset
- Contract interaction failure
- Stale indexed data

Errors should be understandable to users and should never be silently converted into successful states.

---

Performance

Performance should prioritize:

- Fast initial application loading
- Efficient blockchain RPC usage
- Efficient API requests
- Appropriate caching
- Responsive transaction status updates
- Mobile performance
- Graceful behavior under unreliable connectivity

Performance targets must be based on measured application behavior rather than unsupported claims.

---

Production Readiness

Implementation status must be classified separately from documentation status.

Implemented

The functionality exists in the codebase and has supporting local verification.

Configured

The functionality exists but requires valid environment or external-service configuration.

Pending Validation

The functionality requires real staging infrastructure, blockchain, wallet, backend, Supabase, indexer, or external-service validation.

Audit Required

The functionality requires security review or independent audit before production use.

Production Ready

Use this designation only when the relevant implementation, integration, security, and operational requirements have been verified.

Passing a local build, lint, typecheck, or unit tests alone does not establish production readiness.

---

Validation Requirements

Validation should cover the complete relevant flow:

Frontend

- Build
- Typecheck
- Lint
- Tests
- Responsive behavior
- Accessibility

Wallets

- MiniPay
- Valora
- WalletConnect-compatible wallets

Blockchain

- Celo Sepolia
- Celo Mainnet where applicable

Backend

- API integration
- Authentication
- Session handling
- Rate limiting
- Error handling

Supabase

- Database connectivity
- Required migrations
- Authentication/session behavior
- Staging integration

Indexer

- RPC connectivity
- PostgreSQL integration
- Backfill
- Incremental synchronization
- Restart recovery
- Reorganization recovery
- Duplicate-event handling

Smart Contracts

- Address verification
- ABI verification
- Transaction testing
- Security review where required

End-to-End

Where applicable, validate:

dApp
  -> Wallet
  -> Backend/Auth
  -> Supabase
  -> Indexer
  -> Celo RPC
  -> Smart Contracts
  -> Confirmed user-visible state

---

Known Limitations

Any feature that depends on external infrastructure must be explicitly identified as such.

Examples include:

- Missing staging credentials
- Missing Supabase configuration
- Missing Redis/Upstash configuration
- Missing Celo RPC configuration
- Missing indexer infrastructure
- Pending contract verification
- Pending independent security review
- Pending end-to-end validation

Do not replace these limitations with simulated success states.

---

Documentation Rules

This document must remain synchronized with:

- Current dApp implementation
- "CANONICAL_TRUTH.md"
- Current wallet strategy
- Current network configuration
- Current asset terminology
- Current smart-contract deployments
- Current backend/indexer architecture
- Current governance documentation

When the implementation changes, update this specification.

When the canonical product direction changes, review this specification for contradictions.

---

References

- "CANONICAL_TRUTH.md"
- "README.md"
- "ARCHITECTURE.md"
- "SMART_CONTRACTS.md"
- "API_REFERENCE.md"
- "AGENT_NETWORK.md"
- "SECURITY.md"
- "GOVERNANCE.md"
- "METRICS.md"
- "NO_TOKEN_POLICY.md"

Only references that actually exist in the documentation repository should be retained.

---

Canonical Product Scope Summary

CeloHT dApp currently centers on:

Wallet / Finance • Education • Agents • Reforestation • Activity

Impact measurement and public reporting remain important ecosystem functions, but they are not an Impact Dashboard requirement for the dApp.

CeloHT has no native token, does not custody user private keys, and must not represent unverified functionality or data as production-ready.