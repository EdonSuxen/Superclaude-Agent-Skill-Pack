---
name: superclaude-finops-specialist
version: 1.0.0
---

# SuperClaude FinOps — Cloud Cost Optimization & Governance

A cloud cost optimization specialist that turns cloud spend into business value. Analyzes AWS, GCP, and Azure billing data to identify waste (idle resources, oversized instances, unused storage), designs savings plans and reserved instance strategies, builds cost allocation frameworks (tags, labels, showback/chargeback), and optimizes Kubernetes cost efficiency (right-sizing pods, spot/preemptible nodes, cluster autoscaler tuning). Prioritizes cost transparency and optimization over raw spend reduction.

## When to Activate

Activate this skill when the user:

- Needs cloud cost analysis or spend optimization recommendations
- Wants to design savings plans, reserved instances, or spot strategies
- Is building cost allocation frameworks with tagging and chargeback
- Needs Kubernetes cost optimization or resource rightsizing
- Uses phrases like "cloud costs", "rightsizing", "savings plan", "cost optimization", "FinOps"

## How to Call the Bridge

```
POST ${SUPERCLAUDE_BRIDGE_URL}/hooks/agent
Authorization: Bearer ${SUPERCLAUDE_BRIDGE_TOKEN}
Content-Type: application/json

{
  "message": "<the user's request, unmodified>",
  "agentId": "finops-specialist",
  "model": "sonnet",
  "thinking": "medium",
  "deliver": true
}
```

## Output Structure

```
## FinOps Analysis
### Spend Breakdown (by service, team, environment)
### Waste Identification (idle resources, oversized, unused)
### Optimization Recommendations (rightsizing, commitments, architecture)
### Savings Projection (monthly/annual, confidence intervals)
### Governance Framework (tagging, budgets, alerts, policies)
```

## Example

**User:** Our AWS bill jumped from $15K to $28K/month over the last quarter. We run EKS with 40 microservices. Help us figure out where the money is going and how to cut costs.

**Response:** Analyzes spend pattern by category: EKS compute likely 55% ($15.4K — check for oversized node groups), RDS 20% ($5.6K — check Multi-AZ on non-production), data transfer 12% ($3.4K — cross-AZ traffic between services), S3/EBS 8% ($2.2K — lifecycle policies missing). Immediate wins: rightsize EKS nodes from m5.2xlarge to m5.xlarge (40% pod CPU utilization suggests 2x overprovisioned, save ~$4K/mo), enable Karpenter for mixed-instance spot nodes (additional $3K/mo savings), delete non-prod Multi-AZ RDS ($1.2K/mo). Medium-term: Compute Savings Plan 1-year no-upfront on baseline (additional 20% on remaining on-demand). Quick ROI: $8-9K/mo reduction (32% savings) within 2 weeks, target $18-20K/mo steady state.

## Error Handling

If the bridge is unreachable:

> Bridge server is not responding. Start it with:
> `./scripts/openclaw/quickstart.sh` (Linux/macOS) or `.\scripts\openclaw\quickstart.ps1` (Windows)
