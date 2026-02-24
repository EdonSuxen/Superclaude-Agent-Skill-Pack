---
name: superclaude-business-strategy-expert
version: 1.0.0
---

# SuperClaude Business Strategist — Market Positioning & Analysis

A strategic planning specialist that transforms business questions into actionable strategy. Handles market positioning using Porter's Five Forces, competitive analysis with capability mapping, pricing strategy (value-based, cost-plus, penetration), go-to-market planning, and business model design (Business Model Canvas). Prioritizes evidence-based recommendations over opinion, always grounding strategy in market data and competitive dynamics.

## When to Activate

Activate this skill when the user:

- Needs market analysis or competitive landscape assessment
- Wants to develop a pricing strategy for a product or service
- Is planning a go-to-market launch and needs strategic guidance
- Needs business model evaluation or pivot analysis
- Uses phrases like "market analysis", "pricing strategy", "go-to-market", "competitive landscape"

## How to Call the Bridge

```
POST ${SUPERCLAUDE_BRIDGE_URL}/hooks/agent
Authorization: Bearer ${SUPERCLAUDE_BRIDGE_TOKEN}
Content-Type: application/json

{
  "message": "<the user's request, unmodified>",
  "agentId": "business-strategy-expert",
  "model": "sonnet",
  "thinking": "medium",
  "deliver": true
}
```

## Output Structure

```
## Strategic Analysis
### Market Assessment (size, growth, dynamics)
### Competitive Positioning (capability map, differentiation)
### Strategic Recommendations (prioritized options)
### Risk Analysis (threats, mitigation)
### Action Plan (90-day roadmap)
```

## Example

**User:** We're a developer tools startup competing against GitHub Copilot and Cursor. How should we position ourselves?

**Response:** Maps competitive landscape across 5 dimensions (AI quality, IDE integration, pricing, enterprise features, community). Identifies 2 underserved segments: regulated industries needing on-premise AI and open-source teams needing free tier. Recommends Blue Ocean strategy targeting compliance-first positioning with SOC 2 certification as moat. Pricing: freemium with $19/seat/mo pro tier undercutting incumbents. 90-day plan: ship compliance features, target 3 enterprise pilots, launch developer community.

## Error Handling

If the bridge is unreachable:

> Bridge server is not responding. Start it with:
> `./scripts/openclaw/quickstart.sh` (Linux/macOS) or `.\scripts\openclaw\quickstart.ps1` (Windows)
