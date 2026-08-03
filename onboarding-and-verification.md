# Agent Operations Manual: Onboarding & Verification

*Detailed operational companion to [../AGENT_NETWORK.md](../AGENT_NETWORK.md). This manual covers the step-by-step procedures behind the lifecycle summary there.*

## Purpose

This manual gives Regional Coordinators and the Agent Network Working Group a consistent, repeatable process for bringing a new agent from candidate to certified, active status.

## Step-by-Step Onboarding Procedure

### Step 1: Candidate Identification
- Sourced via community nomination, existing merchant/shop-owner outreach, or direct application through the dApp's agent onboarding flow (see [../DAPP.md](../DAPP.md#agent-interaction))
- Regional Coordinator conducts an initial suitability conversation: fixed community location, existing trust standing, availability

### Step 2: Application Submission
Candidate submits, via the dApp:
- Full legal name and government-issued ID
- Physical business/operating location (verified address)
- Two community or partner-organization references
- Wallet address to be associated with their agent identity

### Step 3: Identity & Background Verification
- ID verification against submitted documents
- Reference checks — Regional Coordinator personally contacts both references
- Cross-check against any existing fraud/misconduct flags in the compliance system

### Step 4: Digital Identity Creation
Upon passing verification, a digital identity record is created linking:
- The candidate's wallet address
- A hashed region identifier (not raw location — see [../SMART_CONTRACTS.md](../SMART_CONTRACTS.md#design-principles))
- Verification timestamp

This record is what will populate the on-chain [AgentRegistry](../SMART_CONTRACTS.md#agentregistry--reference-specification) once training is complete.

### Step 5: Training
Candidate completes the full training curriculum — see [training-curriculum.md](./training-curriculum.md) for the detailed syllabus.

### Step 6: Certification Assessment
- Written/verbal competency assessment covering all training modules
- Practical assessment: candidate correctly walks a Regional Coordinator through a simulated cash-in and cash-out transaction, including the confirmation-matching step (see [../USER_GUIDE.md](../USER_GUIDE.md#using-an-agent-cash-in--cash-out))
- Minimum passing standard: 90% on written assessment, full correctness on practical assessment

### Step 7: Activation
- Regional Coordinator submits final approval to the Agent Network Working Group
- Governance multisig (per [../GOVERNANCE.md](../GOVERNANCE.md)) executes `setAgentStatus(agentAddress, Active, regionHash, recertifyBy)` on the [AgentRegistry contract](../SMART_CONTRACTS.md#agentregistry--reference-specification)
- Agent receives dashboard access (see [dashboards.md](./dashboards.md))

## Recertification

Agents must recertify annually (see the `recertifyBy` field in the [AgentRegistry](../SMART_CONTRACTS.md#agentregistry--reference-specification)). Recertification repeats Steps 5–6 in abbreviated form, focused on policy updates and any new fraud patterns identified since initial certification.

## Offboarding

Voluntary exit or policy-violation offboarding both result in `setAgentStatus(agentAddress, Offboarded, ...)`, immediately removing the agent's "Verified" status from the public directory. See [risk-management.md](./risk-management.md#offboarding-triggers) for violation-based offboarding criteria.

## References

- [../AGENT_NETWORK.md](../AGENT_NETWORK.md)
- [training-curriculum.md](./training-curriculum.md)
- [risk-management.md](./risk-management.md)
- [dashboards.md](./dashboards.md)
- [emergency-procedures.md](./emergency-procedures.md)
