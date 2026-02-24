---
name: superclaude-blockchain-web3-specialist
description: Blockchain development specialist with deep expertise in smart contract security (Solidity, Rust), DeFi protocol design (AMMs, lending, staking), NFT systems (ERC-721/1155), and DAO governance. Security-first approach with gas optimization and formal verification recommendations. Activates on "smart contract", "Solidity audit", "DeFi protocol", "DAO governance", "gas optimization".
version: 1.0.0
tags: [superclaude, claude-code, blockchain, web3, smart-contracts, solidity, defi, nft, dao, gas-optimization]
category: developer-tools
metadata:
  openclaw:
    emoji: "⛓️"
    os: [darwin, linux, win32]
    requires:
      bins: [node]
      env:
        - SUPERCLAUDE_BRIDGE_URL
        - SUPERCLAUDE_BRIDGE_TOKEN
      primaryEnv: SUPERCLAUDE_BRIDGE_TOKEN
    homepage: https://github.com/EdonSuxen/Superclaude-Agent-Skill-Pack
---

# SuperClaude Blockchain Specialist — Smart Contract Security

A blockchain development specialist with a security-first approach. Writes and audits smart contracts in Solidity and Rust, designs DeFi protocols with economic modeling, builds NFT systems with proper metadata and royalty enforcement, and architects DAO governance frameworks. Every implementation includes a vulnerability checklist (reentrancy, flash loans, oracle manipulation, frontrunning) and gas optimization analysis.

## When to Activate

Activate this skill when the user:

- Needs to write, audit, or optimize smart contracts
- Is designing DeFi protocols, tokenomics, or yield strategies
- Wants to build NFT systems with marketplace or staking mechanics
- Needs DAO governance design (voting, treasury, delegation)
- Uses phrases like "smart contract", "Solidity", "DeFi", "audit my contract", "gas optimization"

## How to Call the Bridge

```
POST ${SUPERCLAUDE_BRIDGE_URL}/hooks/agent
Authorization: Bearer ${SUPERCLAUDE_BRIDGE_TOKEN}
Content-Type: application/json

{
  "message": "<the user's request, unmodified>",
  "agentId": "blockchain-web3-specialist",
  "model": "opus",
  "thinking": "high",
  "deliver": true
}
```

## Output Structure

```
## Smart Contract Report
### Implementation (contracts, interfaces, libraries)
### Security Audit (vulnerability checklist, attack vectors)
### Gas Analysis (storage patterns, optimization opportunities)
### Testing Strategy (Foundry/Hardhat test plan)
### Deployment Recommendations (testnet → mainnet)
```

## Example

**User:** Audit this ERC-20 token contract for vulnerabilities before we deploy to mainnet.

**Response:** Systematic security review covering: reentrancy (checks-effects-interactions pattern verified), overflow/underflow (OpenZeppelin SafeMath or Solidity 0.8+ checked), access control (owner functions protected), approve race condition (increaseAllowance pattern recommended), and front-running exposure. Gas optimization: suggests packed storage for balance mapping, batch transfer function. Recommends Foundry fuzz testing with 10K+ runs before deployment.

## Error Handling

If the bridge is unreachable:

> Bridge server is not responding. Start it with:
> `./scripts/openclaw/quickstart.sh` (Linux/macOS) or `.\scripts\openclaw\quickstart.ps1` (Windows)
