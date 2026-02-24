---
name: superclaude-observability
version: 1.0.0
---

# SuperClaude Observability — Monitoring, Tracing & SLO Engineering

Two specialists build comprehensive visibility into production systems. `observability-engineer` implements the three pillars — Prometheus metrics with PromQL alerting rules, OpenTelemetry distributed tracing, structured logging with correlation IDs, and Grafana dashboards for every service. `sre-chaos-engineer` validates that observability actually works — defining SLOs/SLIs, running chaos experiments to trigger alerts, managing error budgets, and capacity planning based on real metrics. Together they produce monitoring that catches problems before users do.

## When to Activate

Activate this skill when the user:

- Needs to set up monitoring, logging, or tracing infrastructure
- Wants to define SLOs/SLIs and error budgets for their services
- Is implementing OpenTelemetry or Prometheus/Grafana
- Needs alerting rules that reduce noise while catching real issues
- Uses phrases like "set up monitoring", "add tracing", "define SLOs", "alerting rules"
- Has observability gaps (blind spots in distributed systems)

Do not activate for: active incident response (use `superclaude-incident-response`) or DevOps pipeline setup (use `superclaude-devops`).

## Agents in This Wave

| Agent | Role | Focus |
|-------|------|-------|
| `observability-engineer` | Lead | Prometheus, Grafana, OpenTelemetry, logging, tracing, alerting |
| `sre-chaos-engineer` | Specialist | SLO/SLI definition, chaos experiments, error budgets, capacity planning |

Wave strategy: systematic | Synthesis: consensus | Model: Sonnet

## How to Call the Bridge

```
POST ${SUPERCLAUDE_BRIDGE_URL}/hooks/agent
Authorization: Bearer ${SUPERCLAUDE_BRIDGE_TOKEN}
Content-Type: application/json

{
  "message": "<the user's request, unmodified>",
  "agentId": "observability",
  "model": "sonnet",
  "thinking": "medium",
  "deliver": true
}
```

## Output Structure

```
# Observability Report

## Monitoring Stack — observability-engineer
### Metrics (Prometheus config + key metrics)
### Tracing (OpenTelemetry instrumentation)
### Logging (structured format + correlation)
### Dashboards (Grafana JSON)
### Alerting Rules (with severity and runbook links)

## Reliability Validation — sre-chaos-engineer
### SLO/SLI Definitions
### Error Budget Policy
### Chaos Experiment Plan
### Capacity Projections

## Recommended Next Steps
1. [Instrument highest-traffic services first]
2. [Run first chaos experiment]
```

## Examples

**Example 1 — Full observability stack:**

**User:** Set up monitoring for our 8 microservices running on Kubernetes.

**Response:** `observability-engineer` configures OpenTelemetry SDK for auto-instrumentation, Prometheus ServiceMonitor CRDs for each service, Loki for log aggregation, and 4 Grafana dashboards (overview, per-service, database, and queue depth). `sre-chaos-engineer` defines SLOs (99.9% availability, p95 <200ms), sets up error budget tracking, and designs chaos experiments: pod kill, network latency injection, and dependency failure.

**Example 2 — Alert noise reduction:**

**User:** We get 200 alerts per day and most are false positives. Help fix our alerting.

**Response:** `observability-engineer` audits existing alerts, consolidates 200 into 35 meaningful alerts using multi-signal correlation (error rate + latency + saturation), adds severity tiers, and links each alert to a runbook. `sre-chaos-engineer` validates the reduced alert set catches real failures by running targeted chaos experiments for each SLO.

## Error Handling

If the bridge is unreachable:

> Bridge server is not responding. Start it with:
> `./scripts/openclaw/quickstart.sh` (Linux/macOS) or `.\scripts\openclaw\quickstart.ps1` (Windows)

If one specialist fails, findings from the other are presented with a note about the incomplete analysis.
