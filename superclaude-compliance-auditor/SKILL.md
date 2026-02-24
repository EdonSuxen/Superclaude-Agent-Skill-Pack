---
name: superclaude-compliance-auditor
description: Regulatory compliance and audit management specialist for GDPR, SOC 2, HIPAA, PCI-DSS, and ISO 27001. Maps current systems to regulatory controls, identifies gaps, prepares audit evidence, and designs remediation roadmaps. Produces compliance matrices with gap analysis and risk scoring. Activates on "GDPR compliance", "SOC 2 preparation", "HIPAA audit", "compliance gap analysis".
version: 1.0.0
tags: [superclaude, claude-code, compliance, gdpr, soc2, hipaa, pci-dss, iso-27001, audit-preparation, regulatory]
category: security
metadata:
  openclaw:
    emoji: "📜"
    os: [darwin, linux, win32]
    requires:
      bins: [node]
      env:
        - SUPERCLAUDE_BRIDGE_URL
        - SUPERCLAUDE_BRIDGE_TOKEN
      primaryEnv: SUPERCLAUDE_BRIDGE_TOKEN
    homepage: https://github.com/EdonSuxen/Superclaude-Agent-Skill-Pack
---

# SuperClaude Compliance Auditor — Regulatory Readiness

A regulatory compliance specialist that maps your systems to compliance frameworks and identifies gaps before auditors do. Covers GDPR (data protection, consent, right to erasure), SOC 2 (trust services criteria), HIPAA (PHI handling, BAAs), PCI-DSS (cardholder data), and ISO 27001 (ISMS). Produces compliance matrices, gap analysis reports, evidence collection guides, and prioritized remediation roadmaps.

## When to Activate

Activate this skill when the user:

- Needs to prepare for a SOC 2, HIPAA, or PCI-DSS audit
- Wants a GDPR compliance assessment of their data handling
- Needs a compliance gap analysis against a specific framework
- Is building compliance automation (evidence collection, policy enforcement)
- Uses phrases like "GDPR compliance", "SOC 2 preparation", "HIPAA audit", "compliance gap"

## How to Call the Bridge

```
POST ${SUPERCLAUDE_BRIDGE_URL}/hooks/agent
Authorization: Bearer ${SUPERCLAUDE_BRIDGE_TOKEN}
Content-Type: application/json

{
  "message": "<the user's request, unmodified>",
  "agentId": "compliance-auditor",
  "model": "sonnet",
  "thinking": "medium",
  "deliver": true
}
```

## Output Structure

```
## Compliance Assessment
### Framework Mapping (controls → current state)
### Gap Analysis (missing controls, partial controls)
### Risk Scoring (impact × likelihood)
### Evidence Collection Guide
### Remediation Roadmap (prioritized by audit risk)
```

## Example

**User:** We're a B2B SaaS company preparing for SOC 2 Type II. Our audit is in 4 months. What gaps do we likely have?

**Response:** Maps the 5 trust services criteria (security, availability, processing integrity, confidentiality, privacy) against common SaaS architecture patterns. Identifies typical gaps: incomplete access review logs (CC6.1), missing change management documentation (CC8.1), no formal incident response plan (CC7.3), and inadequate vendor risk assessment (CC9.2). Provides a 16-week remediation timeline with evidence templates for each control. Recommends automated evidence collection via Vanta or Drata to reduce audit prep burden by 60%.

## Error Handling

If the bridge is unreachable:

> Bridge server is not responding. Start it with:
> `./scripts/openclaw/quickstart.sh` (Linux/macOS) or `.\scripts\openclaw\quickstart.ps1` (Windows)
