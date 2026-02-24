---
name: superclaude-green-tech-sustainability-expert
description: Green technology and sustainability expert specializing in carbon measurement, energy-efficient architecture, ESG reporting, and sustainable software practices. Measures software carbon intensity, optimizes cloud resource utilization, designs green CI/CD pipelines, and generates ESG compliance reports. Activates on "carbon footprint", "energy efficiency", "ESG reporting", "green computing", "sustainable software".
version: 1.0.0
tags: [superclaude, claude-code, sustainability, green-tech, carbon-footprint, energy-efficiency, esg-reporting, sustainable-software, green-cloud, sci-measurement]
category: developer-tools
metadata:
  openclaw:
    emoji: "🌿"
    os: [darwin, linux, win32]
    requires:
      bins: [node]
      env:
        - SUPERCLAUDE_BRIDGE_URL
        - SUPERCLAUDE_BRIDGE_TOKEN
      primaryEnv: SUPERCLAUDE_BRIDGE_TOKEN
    homepage: https://github.com/EdonSuxen/Superclaude-Agent-Skill-Pack
---

# SuperClaude Sustainability Expert — Green Technology & ESG

A sustainability specialist that reduces the environmental impact of software systems. Measures Software Carbon Intensity (SCI) per the Green Software Foundation methodology, optimizes cloud resource utilization for energy efficiency, designs carbon-aware workload scheduling (shift compute to low-carbon grid regions), builds green CI/CD pipelines (minimize build waste), and generates ESG reporting dashboards. Balances environmental responsibility with business performance.

## When to Activate

Activate this skill when the user:

- Needs to measure or reduce their software's carbon footprint
- Wants energy-efficient architecture or green cloud optimization
- Is preparing ESG reports or sustainability compliance documentation
- Needs carbon-aware scheduling or green software design patterns
- Uses phrases like "carbon footprint", "energy efficiency", "ESG reporting", "green computing", "sustainable software"

## How to Call the Bridge

```
POST ${SUPERCLAUDE_BRIDGE_URL}/hooks/agent
Authorization: Bearer ${SUPERCLAUDE_BRIDGE_TOKEN}
Content-Type: application/json

{
  "message": "<the user's request, unmodified>",
  "agentId": "green-tech-sustainability-expert",
  "model": "sonnet",
  "thinking": "medium",
  "deliver": true
}
```

## Output Structure

```
## Sustainability Assessment
### Carbon Measurement (SCI score, energy consumption, emissions)
### Optimization Opportunities (resource efficiency, scheduling, architecture)
### Implementation Roadmap (quick wins, medium-term, strategic)
### ESG Reporting (metrics, frameworks, compliance mapping)
### Monitoring & Targets (dashboards, reduction goals, tracking)
```

## Example

**User:** Our SaaS platform runs on AWS us-east-1. We need to measure our carbon footprint and find ways to reduce it for our ESG report. We spend about $50K/month on AWS.

**Response:** Estimates baseline carbon using AWS Customer Carbon Footprint Tool + SCI methodology: $50K/mo AWS spend in us-east-1 (PJM grid, 0.38 kgCO2/kWh) ≈ 8.2 tonnes CO2e/month. Immediate wins (30% reduction): migrate batch workloads to Graviton (40% more energy-efficient), enable S3 Intelligent-Tiering (reduce storage energy), rightsize EC2 instances (typical 30% overprovisioned). Medium-term (additional 20%): shift non-latency-sensitive workloads to us-west-2 (cleaner grid, 0.09 kgCO2/kWh), implement carbon-aware autoscaling using WattTime API. ESG report section: scope 2 emissions from cloud compute, scope 3 from data transfer, year-over-year reduction targets. Dashboard: Grafana panel showing SCI per transaction, monthly emissions trend, cost-per-tonne-saved metric.

## Error Handling

If the bridge is unreachable:

> Bridge server is not responding. Start it with:
> `./scripts/openclaw/quickstart.sh` (Linux/macOS) or `.\scripts\openclaw\quickstart.ps1` (Windows)
