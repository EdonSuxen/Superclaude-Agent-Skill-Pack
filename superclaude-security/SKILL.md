---
name: superclaude-security
description: Threat modeling and vulnerability assessment using STRIDE methodology and OWASP Top 10 analysis. Identifies attack vectors, evaluates risk, and produces prioritized remediation plans. Activates on "is this secure", "find vulnerabilities", "threat model", "security review before launch".
version: 1.0.0
tags: [superclaude, claude-code, security, owasp, threat-modeling, vulnerability, stride, penetration-testing, code-review, risk-assessment]
category: security
metadata:
  openclaw:
    emoji: "🛡️"
    os: [darwin, linux, win32]
    requires:
      bins: [node]
      env:
        - SUPERCLAUDE_BRIDGE_URL
        - SUPERCLAUDE_BRIDGE_TOKEN
      primaryEnv: SUPERCLAUDE_BRIDGE_TOKEN
    homepage: https://github.com/EdonSuxen/Superclaude-Agent-Skill-Pack
---

# Security Specialist — Threat Modeling and Vulnerability Assessment

A dedicated security engineer that applies STRIDE threat modeling, OWASP Top 10 analysis, and defense-in-depth principles to your codebase. Unlike generic security advice, this agent examines your actual code structure, identifies concrete attack vectors, evaluates risk by severity and exploitability, and produces a prioritized remediation plan with specific code-level fixes.

## When to Activate

Activate when the user:

- Asks whether their code or system is secure before shipping
- Wants a threat model for a new feature, API, or architecture
- Needs to identify vulnerabilities in authentication, authorization, or data handling
- Requests a security review of a pull request or code change
- Uses phrases like "is this secure", "find vulnerabilities", "threat model this", "security review"
- Needs to prepare for a penetration test or security certification

For automated SAST/DAST scanning and CI/CD security gates, use `superclaude-devsecops-automation-engineer`. For a full three-specialist audit, use the `superclaude-security-audit` domain pack.

## How to Call the Bridge

```
POST ${SUPERCLAUDE_BRIDGE_URL}/hooks/agent
Authorization: Bearer ${SUPERCLAUDE_BRIDGE_TOKEN}
Content-Type: application/json

{
  "message": "<the user's request, unmodified>",
  "agentId": "security",
  "model": "opus",
  "thinking": "high",
  "deliver": true
}
```

Model: Opus with high thinking — security analysis requires maximum reasoning depth to identify non-obvious attack vectors and chained vulnerabilities.

## Example

**User:** "Review our JWT authentication middleware for security issues. We're using RS256 with refresh tokens stored in httpOnly cookies."

**Response structure:**
- **Threat Model**: STRIDE analysis of the auth flow (Spoofing, Tampering, Repudiation, Information Disclosure, Denial of Service, Elevation of Privilege)
- **Vulnerability Findings**: Ranked by severity (Critical/High/Medium/Low) with CVSS-style scoring
- **Attack Vectors**: Concrete exploitation scenarios (token theft, replay, key confusion)
- **Remediation Plan**: Ordered by risk reduction per effort, with code-level fixes

## Error Handling

If the bridge is unreachable:

> `./scripts/openclaw/quickstart.sh` (Linux/macOS) or `.\scripts\openclaw\quickstart.ps1` (Windows)
