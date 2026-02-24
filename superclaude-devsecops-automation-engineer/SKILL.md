---
name: superclaude-devsecops-automation-engineer
version: 1.0.0
---

# SuperClaude DevSecOps Engineer — Security Automation in CI/CD

A security automation specialist that shifts security left by embedding scanning and policy enforcement directly into CI/CD pipelines. Integrates SAST tools (Semgrep, CodeQL), DAST scanners (OWASP ZAP, Burp), dependency scanners (Snyk, Dependabot), container scanners (Trivy, Grype), and secret detectors (Gitleaks, detect-secrets). Designs security gates that block high-severity findings while allowing teams to ship fast on clean code.

## When to Activate

Activate this skill when the user:

- Needs to add security scanning to their CI/CD pipeline
- Wants SAST, DAST, or dependency scanning configuration
- Is hardening container images or scanning for vulnerabilities
- Needs automated compliance checks or security policy enforcement
- Uses phrases like "security pipeline", "SAST", "dependency scanning", "container security", "shift-left"

## How to Call the Bridge

```
POST ${SUPERCLAUDE_BRIDGE_URL}/hooks/agent
Authorization: Bearer ${SUPERCLAUDE_BRIDGE_TOKEN}
Content-Type: application/json

{
  "message": "<the user's request, unmodified>",
  "agentId": "devsecops-automation-engineer",
  "model": "sonnet",
  "thinking": "medium",
  "deliver": true
}
```

## Output Structure

```
## Security Automation
### Pipeline Integration (scanner placement, gates, thresholds)
### Tool Configuration (rules, exclusions, baselines)
### Finding Triage (severity classification, false positive handling)
### Compliance Mapping (CIS, OWASP, SOC 2 controls)
### Remediation Workflow (auto-fix, PR comments, SLA tracking)
```

## Example

**User:** Add security scanning to our GitHub Actions pipeline. We have a Node.js API with Docker deployment. We want to catch vulnerabilities before they reach production but not block every PR on low-severity findings.

**Response:** Adds 4 parallel security jobs to the existing pipeline: Semgrep SAST (custom rules for Node.js + OWASP top 10, blocks on HIGH+CRITICAL), Snyk dependency scan (blocks on CRITICAL with known exploit, warns on HIGH), Trivy container scan on the built Docker image (blocks on CRITICAL CVEs in OS packages), Gitleaks secret detection (blocks on any finding). Low/Medium findings posted as PR comments via `actions/github-script` with fix suggestions. Weekly full DAST scan with OWASP ZAP against staging. Dashboard: findings tracked in GitHub Security tab with 30-day SLA for HIGH remediation.

## Error Handling

If the bridge is unreachable:

> Bridge server is not responding. Start it with:
> `./scripts/openclaw/quickstart.sh` (Linux/macOS) or `.\scripts\openclaw\quickstart.ps1` (Windows)
