---
name: superclaude-incident-response
version: 1.0.0
---

# SuperClaude Incident Response — Triage, Recovery & Prevention

Two specialists handle production incidents from detection through prevention. `incident-commander` manages the response — severity classification, stakeholder communication, restoration steps, runbook execution, and blameless postmortem facilitation. `observability-engineer` provides the technical investigation — correlating logs across services, tracing request paths through distributed systems, identifying metric anomalies, and building dashboards to prevent recurrence. Together they restore service fast and ensure the same incident doesn't happen twice.

## When to Activate

Activate this skill when the user:

- Is dealing with a production outage or degraded service
- Needs to write or review a postmortem after an incident
- Wants to create runbooks for common failure scenarios
- Needs help setting up on-call procedures or incident response processes
- Uses phrases like "production is down", "incident postmortem", "outage response", "create a runbook"
- Wants to improve Mean Time to Recovery (MTTR)

Do not activate for: monitoring setup without incident context (use `superclaude-observability`) or SRE practices without active incident (use `superclaude-sre`).

## Agents in This Wave

| Agent | Role | Focus |
|-------|------|-------|
| `incident-commander` | Lead | Triage, communication, restoration, runbooks, postmortem facilitation |
| `observability-engineer` | Specialist | Log correlation, trace analysis, metric anomalies, dashboard creation |

Wave strategy: adaptive | Synthesis: lead_agent | Model: Opus

## How to Call the Bridge

```
POST ${SUPERCLAUDE_BRIDGE_URL}/hooks/agent
Authorization: Bearer ${SUPERCLAUDE_BRIDGE_TOKEN}
Content-Type: application/json

{
  "message": "<the user's request, unmodified>",
  "agentId": "incident-response",
  "model": "opus",
  "thinking": "high",
  "deliver": true
}
```

## Output Structure

```
# Incident Response Report

## Triage & Response — incident-commander
### Severity Classification
### Immediate Actions
### Communication Template
### Restoration Steps

## Technical Investigation — observability-engineer
### Log Analysis
### Trace Correlation
### Metric Anomalies
### Root Cause Identification

## Prevention
### Postmortem (5 Whys)
### Action Items (with owners and deadlines)
### Monitoring Improvements
```

## Examples

**Example 1 — Active production outage:**

**User:** Our API is returning 500s for 30% of requests. Started 10 minutes ago.

**Response:** `incident-commander` classifies as SEV-1, drafts stakeholder communication, and outlines restoration steps (rollback last deploy, enable circuit breaker, scale up healthy instances). `observability-engineer` correlates error logs with the deployment timestamp, identifies a database connection pool exhaustion after a schema migration, and recommends immediate connection limit increase.

**Example 2 — Postmortem writing:**

**User:** Write a postmortem for yesterday's 2-hour checkout outage.

**Response:** `incident-commander` structures the blameless postmortem: timeline, impact (2,400 failed checkouts, $180K estimated revenue loss), 5-Whys root cause chain, and 6 action items with owners. `observability-engineer` adds the technical appendix: Grafana dashboard screenshots, trace waterfall showing the timeout cascade, and new alerts to add.

## Error Handling

If the bridge is unreachable:

> Bridge server is not responding. Start it with:
> `./scripts/openclaw/quickstart.sh` (Linux/macOS) or `.\scripts\openclaw\quickstart.ps1` (Windows)

If one specialist fails, findings from the other are presented with a note about the incomplete analysis.
