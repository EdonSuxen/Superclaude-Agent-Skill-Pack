---
name: superclaude-web3
description: Blockchain and decentralized application development using SuperClaude's blockchain-web3-specialist — smart contract development (Solidity, Rust), DeFi protocol design, NFT systems, DAO governance, security auditing for on-chain code, and gas optimization. Returns security-first implementations with formal verification recommendations. Activates on "smart contract", "DeFi protocol", "NFT", "DAO governance", "gas optimization".
version: 1.0.0
tags: [superclaude, claude-code, blockchain, smart-contracts, defi, web3, solidity, ethereum, nft, dao-governance]
category: developer-tools
metadata:
  openclaw:
    emoji: "🔗"
    os: [darwin, linux, win32]
    requires:
      bins: [node]
      env:
        - SUPERCLAUDE_BRIDGE_URL
        - SUPERCLAUDE_BRIDGE_TOKEN
      primaryEnv: SUPERCLAUDE_BRIDGE_TOKEN
    homepage: https://github.com/EdonSuxen/Superclaude-Agent-Skill-Pack
---

# SuperClaude Web3 — Blockchain & Decentralized Applications

A dedicated specialist covers the full Web3 development lifecycle with a security-first approach. `blockchain-web3-specialist` handles smart contract development in Solidity and Rust, DeFi protocol design (AMMs, lending, staking), NFT systems (ERC-721/1155, metadata, marketplaces), DAO governance frameworks, security auditing for on-chain code (reentrancy, flash loans, oracle manipulation), and gas optimization patterns that reduce transaction costs without sacrificing safety.

## When to Activate

Activate this skill when the user:

- Needs to write, audit, or optimize smart contracts (Solidity or Rust)
- Is designing DeFi protocols (AMMs, lending pools, yield strategies)
- Wants to build NFT systems with metadata, marketplace, or royalty logic
- Needs DAO governance design (voting mechanisms, treasury management)
- Uses phrases like "smart contract", "DeFi", "NFT", "DAO", "gas optimization", "audit my contract"
- Is evaluating blockchain architectures (L1 vs L2, rollups, bridges)

Do not activate for: traditional backend APIs (use `superclaude-api-design`) or general cryptography (use `superclaude-security-audit`).

## Agent

| Agent | Role | Focus |
|-------|------|-------|
| `blockchain-web3-specialist` | Lead | Solidity/Rust contracts, DeFi, NFTs, DAOs, security auditing, gas optimization |

Model: Sonnet

## How to Call the Bridge

```
POST ${SUPERCLAUDE_BRIDGE_URL}/hooks/agent
Authorization: Bearer ${SUPERCLAUDE_BRIDGE_TOKEN}
Content-Type: application/json

{
  "message": "<the user's request, unmodified>",
  "agentId": "web3",
  "model": "sonnet",
  "thinking": "medium",
  "deliver": true
}
```

## Output Structure

```
# Web3 Development Report

## Smart Contract Design
### Architecture (contracts, interfaces, libraries)
### Security Analysis (vulnerability checklist)
### Gas Optimization (storage patterns, calldata encoding)

## Protocol Design (if applicable)
### Mechanism Design
### Economic Model
### Attack Surface Analysis

## Recommended Next Steps
1. [Security audit priorities]
2. [Testing strategy (Foundry/Hardhat)]
3. [Deployment plan (testnet → mainnet)]
```

## Examples

**Example 1 — DeFi lending protocol:**

**User:** Design a simple lending protocol where users deposit ETH as collateral and borrow USDC.

**Response:** Designs a minimal lending pool with overcollateralization (150%), liquidation at 120% health factor, and interest rate model (utilization-based curve). Security analysis covers reentrancy protection (checks-effects-interactions), oracle manipulation (Chainlink + TWAP fallback), and flash loan attack vectors. Gas optimization stores user positions in packed structs and batches oracle reads.

**Example 2 — NFT collection with royalties:**

**User:** I want to launch a 10K PFP collection with on-chain royalties and a staking mechanism.

**Response:** Implements ERC-721A for gas-efficient batch minting (80% cheaper than standard 721), EIP-2981 royalties (5% enforced via operator filter), and a staking contract that yields ERC-20 tokens based on staking duration. Metadata stored on IPFS with provenance hash committed pre-reveal. Security review covers mint function access control, randomness for reveal (Chainlink VRF), and staking reward calculation overflow protection.

## Error Handling

If the bridge is unreachable:

> Bridge server is not responding. Start it with:
> `./scripts/openclaw/quickstart.sh` (Linux/macOS) or `.\scripts\openclaw\quickstart.ps1` (Windows)
