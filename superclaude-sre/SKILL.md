---
name: superclaude-sre
description: Site reliability engineering using three specialists — sre-chaos-engineer (chaos experiments, error budgets, capacity planning, disaster recovery), observability-engineer (Prometheus/Grafana, OpenTelemetry, alerting), and incident-commander (runbooks, postmortems, crisis communication). Returns reliability assessments with SLO definitions and improvement roadmaps. Activates on "define SLOs", "chaos test", "improve reliability", "postmortem".
version: 1.0.0
tags: [superclaude, claude-code, sre, reliability, chaos-engineering, slo-sli, incident-response, error-budgets, disaster-recovery, observability]
category: cloud
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

# SuperClaude SRE — Reliability Engineering & Chaos Testing

Three specialists cover the full reliability lifecycle. `sre-chaos-engineer` designs chaos experiments, defines error budgets, plans capacity, and builds disaster recovery strategies. `observability-engineer` wires monitoring with Prometheus/Grafana, distributed tracing with OpenTelemetry, and builds alerting rules that catch real problems without alert fatigue. `incident-commander` creates runbooks, leads postmortem processes, and establishes communication protocols for outages.

## When to Activate

Activate this skill when the user:

- Needs to define SLOs/SLIs/error budgets for their services
- Wants to design chaos experiments to test failure resilience
- Is building monitoring, alerting, or observability infrastructure
- Needs a postmortem template or wants to analyze a past incident
- Uses phrases like "define SLOs", "chaos test", "improve reliability", "why did this go down"
- Is planning disaster recovery or capacity scaling strategies

Do not activate for: CI/CD pipeline setup (use `superclaude-devops`) or application performance profiling (use `superclaude-performance`).

## Agents in This Wave

| Agent | Role | Focus |
|-------|------|-------|
| `sre-chaos-engineer` | Lead | Chaos experiments, error budgets, capacity planning, DR strategies |
| `observability-engineer` | Specialist | Prometheus/Grafana, OpenTelemetry, alerting, dashboards |
| `incident-commander` | Specialist | Runbooks, postmortems, incident communication, escalation |

Wave strategy: enterprise | Synthesis: consensus | Model: Opus

## How to Call the Bridge

```
POST ${SUPERCLAUDE_BRIDGE_URL}/hooks/agent
Authorization: Bearer ${SUPERCLAUDE_BRIDGE_TOKEN}
Content-Type: application/json

{
  "message": "<the user's request, unmodified>",
  "agentId": "sre",
  "model": "opus",
  "thinking": "high",
  "deliver": true
}
```

## Output Structure

```
# SRE Assessment Report

## Reliability Analysis — sre-chaos-engineer
### Current Reliability Posture
### SLO/SLI Definitions
### Chaos Experiment Plan
### Error Budget Status

## Observability — observability-engineer
### Monitoring Coverage
### Alerting Rules
### Dashboard Recommendations
### Tracing Gaps

## Incident Readiness — incident-commander
### Runbook Assessment
### Postmortem Process
### Communication Plan

## Recommended Next Steps
1. [Critical reliability improvements]
2. [Monitoring gaps to close]
3. [Chaos experiments to run first]
```

## Examples

**Example 1 — SLO definition:**

**User:** We need SLOs for our payment API. It handles 50K requests/day.

**Response:** `sre-chaos-engineer` defines 3 SLOs (availability 99.95%, latency P99 <500ms, error rate <0.1%) with error budgets and burn rate alerts. `observability-engineer` designs the Prometheus recording rules and Grafana dashboard to track each SLO in real time. `incident-commander` creates an escalation matrix: page on-call at 50% budget burn, escalate to engineering lead at 75%.

**Example 2 — Chaos engineering:**

**User:** We've never tested what happens when our database fails over. Help us design a chaos experiment.

**Response:** `sre-chaos-engineer` designs a progressive chaos plan: start with connection pool exhaustion (safe), then replica lag injection, then primary failover simulation. Each with blast radius controls and abort conditions. `observability-engineer` sets up experiment-specific dashboards to monitor during the test. `incident-commander` prepares a runbook for the experiment day with rollback procedures.

## Error Handling

If the bridge is unreachable:

> Bridge server is not responding. Start it with:
> `./scripts/openclaw/quickstart.sh` (Linux/macOS) or `.\scripts\openclaw\quickstart.ps1` (Windows)

If one specialist fails, findings from the others are presented with a note about the incomplete analysis.
