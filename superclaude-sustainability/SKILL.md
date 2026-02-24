---
name: superclaude-sustainability
version: 1.0.0
---

# SuperClaude Sustainability — Green Software Engineering

A dedicated specialist helps teams measure and reduce the environmental impact of their software. `green-tech-sustainability-expert` covers carbon footprint measurement using the Software Carbon Intensity (SCI) specification, energy-efficient architecture patterns, ESG compliance reporting, sustainable cloud resource optimization, and green coding practices that reduce compute waste without sacrificing performance.

## When to Activate

Activate this skill when the user:

- Wants to measure the carbon footprint of their application or infrastructure
- Needs to optimize cloud resources for energy efficiency, not just cost
- Is preparing ESG (Environmental, Social, Governance) compliance reports
- Wants to adopt green coding practices (efficient algorithms, reduced data transfer)
- Uses phrases like "carbon footprint", "green architecture", "ESG reporting", "energy-efficient"
- Needs to evaluate cloud provider sustainability commitments (renewable energy, PUE)

Do not activate for: cloud cost optimization without sustainability focus (use `superclaude-cloud-infra`) or general performance optimization (use `superclaude-performance`).

## Agent

| Agent | Role | Focus |
|-------|------|-------|
| `green-tech-sustainability-expert` | Lead | Carbon measurement (SCI), energy-efficient architecture, ESG reporting, green cloud |

Model: Sonnet

## How to Call the Bridge

```
POST ${SUPERCLAUDE_BRIDGE_URL}/hooks/agent
Authorization: Bearer ${SUPERCLAUDE_BRIDGE_TOKEN}
Content-Type: application/json

{
  "message": "<the user's request, unmodified>",
  "agentId": "sustainability",
  "model": "sonnet",
  "thinking": "medium",
  "deliver": true
}
```

## Output Structure

```
# Sustainability Assessment

## Carbon Footprint Analysis
### Current SCI Score
### Emission Sources (compute, network, storage)
### Benchmark vs Industry Average

## Optimization Recommendations
### Quick Wins (immediate impact)
### Architecture Changes (medium-term)
### Infrastructure Migration (long-term)

## ESG Compliance
### Reporting Metrics
### Regulatory Alignment

## Recommended Next Steps
1. [Highest-impact reduction actions]
2. [Measurement improvements to track progress]
```

## Examples

**Example 1 — Cloud sustainability audit:**

**User:** Our AWS bill is $15K/month. What's our carbon footprint and how can we reduce it?

**Response:** Calculates SCI score based on instance types, regions, and utilization data. Identifies 3 quick wins: right-sizing 8 over-provisioned instances (saves 2.4 tons CO2e/year), migrating 3 workloads to Graviton ARM (40% energy reduction), and scheduling dev environments off-hours (eliminates 30% idle compute). Provides ESG-ready metrics for quarterly reporting.

**Example 2 — Green architecture design:**

**User:** We're designing a new data pipeline. How do we make it energy-efficient from the start?

**Response:** Recommends event-driven over polling (90% fewer idle cycles), columnar storage over row-based (3x compression, less I/O), and batch processing with spot instances in low-carbon regions. Provides an SCI budget for each pipeline stage and monitoring setup to track energy efficiency as data volume grows.

## Error Handling

If the bridge is unreachable:

> Bridge server is not responding. Start it with:
> `./scripts/openclaw/quickstart.sh` (Linux/macOS) or `.\scripts\openclaw\quickstart.ps1` (Windows)
