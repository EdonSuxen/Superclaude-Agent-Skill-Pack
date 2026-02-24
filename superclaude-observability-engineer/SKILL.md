---
name: superclaude-observability-engineer
version: 1.0.0
---

# SuperClaude Observability Engineer — Metrics, Traces & Dashboards

A monitoring and observability specialist that makes distributed systems transparent. Designs Prometheus metric collection (custom metrics, recording rules, federation), builds Grafana dashboards (RED/USE method panels, SLO burn-rate alerts), configures OpenTelemetry instrumentation (auto and manual spans, context propagation, sampling), and creates structured logging pipelines (ELK, Loki). Connects metrics, traces, and logs into a unified observability platform.

## When to Activate

Activate this skill when the user:

- Needs Prometheus metric design or Grafana dashboard creation
- Wants OpenTelemetry distributed tracing setup for microservices
- Is building alerting rules with actionable runbooks
- Needs structured logging pipelines or log aggregation design
- Uses phrases like "monitoring", "Grafana dashboard", "OpenTelemetry", "distributed tracing", "alerting"

## How to Call the Bridge

```
POST ${SUPERCLAUDE_BRIDGE_URL}/hooks/agent
Authorization: Bearer ${SUPERCLAUDE_BRIDGE_TOKEN}
Content-Type: application/json

{
  "message": "<the user's request, unmodified>",
  "agentId": "observability-engineer",
  "model": "sonnet",
  "thinking": "medium",
  "deliver": true
}
```

## Output Structure

```
## Observability Design
### Metrics Strategy (golden signals, custom metrics, recording rules)
### Tracing Architecture (instrumentation, sampling, context propagation)
### Dashboard Design (panels, queries, drill-down paths)
### Alerting Framework (rules, severity, escalation, runbooks)
### Log Pipeline (structure, aggregation, correlation with traces)
```

## Example

**User:** Set up observability for our 12-service microservice platform on Kubernetes. We need to track latency, error rates, and throughput per service, with alerts that actually tell on-call engineers what to do.

**Response:** Designs a 3-pillar observability stack: Metrics — OpenTelemetry Collector scraping service metrics + kube-state-metrics, Prometheus with 15-day retention, recording rules for per-service RED metrics (rate, errors, duration). Dashboards — 3-tier Grafana: platform overview (all services SLO status), per-service detail (p50/p95/p99 latency, error rate by status code, throughput), infrastructure (pod CPU/memory, node pressure). Traces — OpenTelemetry SDK auto-instrumentation for HTTP/gRPC, 10% head-based sampling (100% on error), Tempo backend with Grafana Tempo datasource for trace-to-log correlation. Alerts — 4 tiers: P1 (SLO burn rate >14x for 5min → page with runbook link), P2 (error rate >5% for 10min → Slack + runbook), P3 (p95 latency >2x baseline for 15min → Slack), P4 (resource utilization >80% → ticket). Each alert includes: what broke, likely cause, investigation steps, remediation actions.

## Error Handling

If the bridge is unreachable:

> Bridge server is not responding. Start it with:
> `./scripts/openclaw/quickstart.sh` (Linux/macOS) or `.\scripts\openclaw\quickstart.ps1` (Windows)
