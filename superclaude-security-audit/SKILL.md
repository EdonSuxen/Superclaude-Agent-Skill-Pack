---
name: superclaude-security-audit
version: 1.0.0
---

# SuperClaude Security Audit — Three-Specialist Wave

This skill triggers a coordinated three-agent wave: `security` (manual threat modeling), `devsecops-automation-engineer` (automated scanning and CI/CD gates), and `compliance-auditor` (regulatory compliance mapping). Each specialist audits independently, then findings are merged into a prioritized security report.

## When to Activate

Activate this skill when the user:

- Requests a security audit, threat model, or vulnerability assessment
- Asks about compliance status (GDPR, SOC 2, HIPAA, PCI-DSS)
- Mentions penetration testing preparation or security review
- Uses phrases like "security audit", "is this secure", "compliance check", "threat model"
- Wants to prepare for a security certification or audit

## How to Call the Bridge

```
POST ${SUPERCLAUDE_BRIDGE_URL}/hooks/agent
Authorization: Bearer ${SUPERCLAUDE_BRIDGE_TOKEN}
Content-Type: application/json

{
  "message": "<the user's security request, unmodified>",
  "agentId": "security-audit",
  "model": "opus",
  "thinking": "high",
  "deliver": true
}
```

## Handling the Response

Structure the output as a security report:

```
# Security Audit Report

## Critical Findings
- [Cross-specialist critical issues, ranked by severity]

## Threat Model — security
### Attack Vectors Identified
- ...
### Risk Assessment
- ...

## Automated Scan Results — devsecops-automation-engineer
### SAST Findings
- ...
### Dependency Vulnerabilities
- ...
### CI/CD Security Gaps
- ...

## Compliance Status — compliance-auditor
### Regulatory Coverage
- ...
### Gaps Requiring Remediation
- ...

## Remediation Priority
Ordered list of actions ranked by risk reduction per effort.
```

## Error Handling

If the bridge is unreachable:

> Bridge server is not responding. Start it with:
> `cd integrations/openclaw && npx tsx bridge-server.ts`

If the bridge returns **HTTP 400**: the delegation graph has a structural problem — duplicate node IDs, unknown agentId, missing node reference, or a dependency cycle. Check your graph definition before retrying.

If the bridge returns **HTTP 500**: a runtime error occurred during agent execution. Individual specialist results may still be partially available — present any findings received with a note about the failed stage.

If one specialist fails, present findings from the others with a note about the incomplete analysis.

## Example Conversations

**Example 1 — Full audit:**

**User:** Run a security audit on our authentication system before we go to production.

**Skill action:** POST to bridge with `agentId: "security-audit"`. Three specialists analyze in parallel: security identifies auth vulnerabilities, devsecops scans for misconfigurations, compliance checks regulatory alignment.

**Example 2 — Compliance check:**

**User:** We need to pass SOC 2 Type II. What gaps do we have?

**Skill action:** POST to bridge with `agentId: "security-audit"`. compliance-auditor maps current state to SOC 2 controls; security identifies risks; devsecops recommends automated evidence collection.
