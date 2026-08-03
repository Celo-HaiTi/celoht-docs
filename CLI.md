# CLI

> **Status:** Specification for the planned `celoht-cli` developer tool — see [ROADMAP.md](./ROADMAP.md) for delivery timeline. Verify current implementation status in the `celoht-cli` repository before relying on specific commands.

## Purpose

The CeloHT CLI helps developers interact with CeloHT's smart contracts, API, and local development environment without leaving the terminal.

## Installation

```bash
npm install -g @celoht/cli
```

## Configuration

```bash
celoht config set network alfajores
celoht config set api-url https://api.celoht.com/v1
```

## Core Commands

### Agent Registry

```bash
# Check an agent's verification status
celoht agent status <address>

# List agents in a region (requires governance credentials for write access)
celoht agent list --region <region-hash>
```

### Development

```bash
# Scaffold a new CeloHT-integrated project
celoht init my-project

# Run local contract tests (wraps `npx hardhat test`)
celoht test

# Compile contracts (wraps `npx hardhat compile`)
celoht compile
```

### API Interaction

```bash
# Query impact metrics
celoht metrics summary

# List education modules
celoht education list
```

## Example Session

```bash
$ celoht config set network alfajores
✔ Network set to alfajores

$ celoht agent status 0xAbC123...
Status: Active
Region: (hashed)
Certified: 2026-03-01
Recertify by: 2027-03-01

$ celoht metrics summary
People trained:      4,200
Wallets created:      3,100
Active agents:            47
Trees planted:        18,500 (15,200 confirmed surviving)
```

## Exit Codes

| Code | Meaning |
|---|---|
| 0 | Success |
| 1 | General error |
| 2 | Configuration error (e.g. missing network setting) |
| 3 | Network/API error |
| 4 | Authentication error |

## References

- [DEVELOPER_GUIDE.md](./DEVELOPER_GUIDE.md)
- [API_REFERENCE.md](./API_REFERENCE.md)
- [SDK.md](./SDK.md)
