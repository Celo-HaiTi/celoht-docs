# Smart Contracts

> **Status: Reference specification.** The Solidity code in this document is a reference implementation illustrating CeloHT's intended on-chain design. It has **not** been professionally audited or deployed to mainnet, and must not be treated as production-ready or security-verified until it has completed the process in [Path to Production](#path-to-production). Marking this clearly is a deliberate choice — claiming unaudited contract code is "production-ready" would itself be a security risk to anyone relying on this documentation.
>
> **Compilation note:** this code was written to standard Solidity 0.8.x conventions but was not compiled or executed in this documentation environment (no `solc`/network access here) — a maintainer must run `npx hardhat compile && npx hardhat test` locally before relying on it. See [DEVELOPER_GUIDE.md](./DEVELOPER_GUIDE.md#local-setup).

## Purpose & Scope

CeloHT's on-chain footprint is intentionally minimal: only data that benefits from public verifiability lives on-chain. Two core contracts are specified:

1. **AgentRegistry** — records agent verification status, publicly and immutably
2. **TransactionLog** — optional, opt-in transparent logging of Agent Network transaction summaries (no personal data on-chain)

## Design Principles

- **Non-custodial:** these contracts never hold user funds. Payments move directly wallet-to-wallet via native cUSD transfers.
- **Minimal on-chain data:** no personally identifiable information is stored on-chain — only hashed identifiers and status flags.
- **Upgradeable with governance gating:** contract upgrades require multi-signature approval from addresses controlled by the Maintainer Council (see [GOVERNANCE.md](./GOVERNANCE.md)), not a single deployer key.
- **No token logic of any kind** — these contracts contain no minting, staking, or transferable-asset logic, consistent with [NO_TOKEN_POLICY.md](./NO_TOKEN_POLICY.md).

## AgentRegistry — Reference Specification

```solidity
// SPDX-License-Identifier: Apache-2.0
pragma solidity ^0.8.24;

/// @title CeloHT Agent Registry
/// @notice Publicly verifiable registry of Agent Network verification status.
/// @dev Reference implementation — see SMART_CONTRACTS.md "Path to Production"
///      before any mainnet deployment. Not audited.
contract AgentRegistry {
    address public governance; // multisig controlled per GOVERNANCE.md

    enum Status { Unregistered, Pending, Active, Suspended, Offboarded }

    struct Agent {
        Status status;
        bytes32 regionHash;      // hashed region identifier, not raw location
        uint64  certifiedAt;     // unix timestamp of last certification
        uint64  recertifyBy;     // unix timestamp recertification deadline
    }

    mapping(address => Agent) private agents;

    event AgentStatusChanged(address indexed agent, Status status);
    event GovernanceTransferred(address indexed previousGovernance, address indexed newGovernance);

    modifier onlyGovernance() {
        require(msg.sender == governance, "AgentRegistry: caller is not governance");
        _;
    }

    constructor(address _governance) {
        require(_governance != address(0), "AgentRegistry: zero governance address");
        governance = _governance;
    }

    /// @notice Register or update an agent's status. Only callable by governance
    ///         (the multisig controlled per the process in GOVERNANCE.md), following
    ///         off-chain verification per AGENT_NETWORK.md.
    function setAgentStatus(
        address agentAddress,
        Status status,
        bytes32 regionHash,
        uint64 recertifyBy
    ) external onlyGovernance {
        require(agentAddress != address(0), "AgentRegistry: zero agent address");
        agents[agentAddress] = Agent({
            status: status,
            regionHash: regionHash,
            certifiedAt: uint64(block.timestamp),
            recertifyBy: recertifyBy
        });
        emit AgentStatusChanged(agentAddress, status);
    }

    /// @notice Publicly check whether an address is a currently active, verified agent.
    function isActiveAgent(address agentAddress) external view returns (bool) {
        Agent memory a = agents[agentAddress];
        return a.status == Status.Active && block.timestamp <= a.recertifyBy;
    }

    /// @notice Read full agent record.
    function getAgent(address agentAddress) external view returns (Agent memory) {
        return agents[agentAddress];
    }

    /// @notice Transfer governance control (e.g. multisig rotation per GOVERNANCE.md).
    function transferGovernance(address newGovernance) external onlyGovernance {
        require(newGovernance != address(0), "AgentRegistry: zero new governance address");
        emit GovernanceTransferred(governance, newGovernance);
        governance = newGovernance;
    }
}
```

### Reference Test Suite (Hardhat / Chai — illustrative)

```javascript
// test/AgentRegistry.test.js
// NOTE: illustrative reference tests. Run locally with `npx hardhat test`
// after `npm install` — requires network access to install Hardhat, which
// this documentation environment does not have. See DEVELOPER_GUIDE.md.

const { expect } = require("chai");
const { ethers } = require("hardhat");

describe("AgentRegistry", function () {
  let registry, governance, agent, other;

  beforeEach(async function () {
    [governance, agent, other] = await ethers.getSigners();
    const Registry = await ethers.getContractFactory("AgentRegistry");
    registry = await Registry.deploy(governance.address);
  });

  it("sets deployer-specified governance address on deployment", async function () {
    expect(await registry.governance()).to.equal(governance.address);
  });

  it("allows governance to activate an agent", async function () {
    const regionHash = ethers.keccak256(ethers.toUtf8Bytes("region-1"));
    const recertifyBy = Math.floor(Date.now() / 1000) + 365 * 24 * 60 * 60;

    await registry.connect(governance).setAgentStatus(agent.address, 2 /* Active */, regionHash, recertifyBy);

    expect(await registry.isActiveAgent(agent.address)).to.equal(true);
  });

  it("rejects status updates from a non-governance address", async function () {
    const regionHash = ethers.keccak256(ethers.toUtf8Bytes("region-1"));
    const recertifyBy = Math.floor(Date.now() / 1000) + 365 * 24 * 60 * 60;

    await expect(
      registry.connect(other).setAgentStatus(agent.address, 2, regionHash, recertifyBy)
    ).to.be.revertedWith("AgentRegistry: caller is not governance");
  });

  it("treats an agent as inactive after their recertification deadline passes", async function () {
    const regionHash = ethers.keccak256(ethers.toUtf8Bytes("region-1"));
    const pastDeadline = Math.floor(Date.now() / 1000) - 1;

    await registry.connect(governance).setAgentStatus(agent.address, 2, regionHash, pastDeadline);

    expect(await registry.isActiveAgent(agent.address)).to.equal(false);
  });
});
```

## Path to Production

Before any deployment beyond a public testnet, CeloHT requires:

1. Independent third-party security audit (see [SECURITY.md](./SECURITY.md#audit-readiness))
2. Public testnet deployment with a minimum 90-day monitored trial period
3. Governance multisig fully configured per [GOVERNANCE.md](./GOVERNANCE.md) — no single-key deployer control on mainnet
4. Published audit report and remediation record
5. Maintainer Council sign-off per the RFC process in [GOVERNANCE.md](./GOVERNANCE.md)

## References

- [ARCHITECTURE.md](./ARCHITECTURE.md)
- [SECURITY.md](./SECURITY.md)
- [DEVELOPER_GUIDE.md](./DEVELOPER_GUIDE.md)
- [AGENT_NETWORK.md](./AGENT_NETWORK.md#registration--verification)
