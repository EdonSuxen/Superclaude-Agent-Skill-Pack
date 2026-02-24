---
name: superclaude-compliance
version: 1.0.0
---

# SuperClaude Compliance — Regulatory Readiness & Policy Automation

Two specialists cover compliance from both the regulatory and technical angles. `compliance-auditor` maps your codebase and infrastructure against regulatory frameworks — GDPR data processing requirements, SOC 2 trust service criteria, HIPAA safeguards, and PCI-DSS controls. `devsecops-automation-engineer` translates those requirements into automated enforcement — SAST/DAST scanning rules, CI/CD gate policies, dependency vulnerability checks, and evidence collection automation. Together they produce audit-ready compliance reports with automated guardrails.

## When to Activate

Activate this skill when the user:

- Needs to assess compliance readiness for SOC 2, GDPR, HIPAA, or PCI-DSS
- Is preparing for an external audit and needs a gap analysis
- Wants to automate compliance checks in CI/CD pipelines
- Needs to implement data processing agreements or privacy controls
- Uses phrases like "SOC 2 readiness", "GDPR compliance", "audit preparation", "compliance gaps"
- Requires evidence collection automation for ongoing compliance

Do not activate for: security vulnerability scanning without compliance context (use `superclaude-security-audit`) or general security hardening (use `superclaude-security`).

## Agents in This Wave

| Agent | Role | Focus |
|-------|------|-------|
| `compliance-auditor` | Lead | GDPR/SOC 2/HIPAA/PCI-DSS mapping, audit readiness, gap analysis |
| `devsecops-automation-engineer` | Specialist | Automated policy enforcement, scanning rules, CI/CD security gates |

Wave strategy: systematic | Synthesis: lead_agent | Model: Opus

## How to Call the Bridge

```
POST ${SUPERCLAUDE_BRIDGE_URL}/hooks/agent
Authorization: Bearer ${SUPERCLAUDE_BRIDGE_TOKEN}
Content-Type: application/json

{
  "message": "<the user's request, unmodified>",
  "agentId": "compliance",
  "model": "opus",
  "thinking": "high",
  "deliver": true
}
```

## Output Structure

```
# Compliance Assessment Report

## Regulatory Analysis — compliance-auditor
### Framework Coverage Matrix
### Control Gaps (ranked by risk)
### Evidence Requirements
### Remediation Timeline

## Automated Enforcement — devsecops-automation-engineer
### CI/CD Policy Gates
### Scanning Configuration
### Evidence Collection Automation

## Recommended Next Steps
1. [Critical gaps to close first]
2. [Automation to implement]
```

## Examples

**Example 1 — SOC 2 Type II preparation:**

**User:** We need to pass SOC 2 Type II in 6 months. What gaps do we have?

**Response:** `compliance-auditor` maps current state against all 5 trust service criteria, identifies 23 control gaps (8 critical: no access reviews, no incident response plan, missing encryption at rest). `devsecops-automation-engineer` configures automated evidence collection — access logs to S3, Semgrep rules for secret detection, and weekly dependency scans.

**Example 2 — GDPR data handling:**

**User:** Review our user data handling for GDPR compliance.

**Response:** `compliance-auditor` traces data flows, identifies 5 gaps: no consent management, incomplete data processing records, missing data deletion pipeline, inadequate breach notification process. `devsecops-automation-engineer` implements PII detection in logs via regex rules and automated data retention enforcement.

## Error Handling

If the bridge is unreachable:

> Bridge server is not responding. Start it with:
> `./scripts/openclaw/quickstart.sh` (Linux/macOS) or `.\scripts\openclaw\quickstart.ps1` (Windows)

If one specialist fails, findings from the other are presented with a note about the incomplete analysis.
