---
name: superclaude-product
version: 1.0.0
---

# SuperClaude Product — Strategy & Requirements Engineering

Two specialists bridge the gap between business goals and engineering execution. `product-manager` handles the product craft — PRDs with clear acceptance criteria, user story mapping, RICE/ICE prioritization, feature scoping, and roadmap sequencing. `business-strategy-expert` provides strategic context — competitive landscape analysis, market positioning, pricing strategy, and go-to-market planning. Together they produce product specs that are both user-focused and business-aligned.

## When to Activate

Activate this skill when the user:

- Needs to write a PRD or product specification
- Wants to prioritize a feature backlog using data-driven frameworks
- Is planning a product roadmap and needs sequencing guidance
- Needs competitive analysis or market positioning strategy
- Uses phrases like "write a PRD", "prioritize our backlog", "product roadmap", "build vs buy"
- Is making strategic product decisions (pricing, positioning, GTM)

Do not activate for: growth/marketing execution (use `superclaude-growth`) or technical architecture decisions (use `superclaude-architecture`).

## Agents in This Wave

| Agent | Role | Focus |
|-------|------|-------|
| `product-manager` | Lead | PRDs, user stories, RICE prioritization, roadmap, acceptance criteria |
| `business-strategy-expert` | Specialist | Market positioning, competitive analysis, pricing, GTM strategy |

Wave strategy: adaptive | Synthesis: consensus | Model: Sonnet

## How to Call the Bridge

```
POST ${SUPERCLAUDE_BRIDGE_URL}/hooks/agent
Authorization: Bearer ${SUPERCLAUDE_BRIDGE_TOKEN}
Content-Type: application/json

{
  "message": "<the user's request, unmodified>",
  "agentId": "product",
  "model": "sonnet",
  "thinking": "medium",
  "deliver": true
}
```

## Output Structure

```
# Product Strategy Report

## Product Specification — product-manager
### PRD / Feature Spec
### User Stories with Acceptance Criteria
### Prioritization Framework (RICE scores)
### Roadmap Sequencing

## Business Strategy — business-strategy-expert
### Market Analysis
### Competitive Positioning
### Pricing Recommendations
### Go-to-Market Alignment

## Recommended Next Steps
1. [Immediate product actions]
2. [Validation experiments to run]
```

## Examples

**Example 1 — Feature prioritization:**

**User:** We have 20 feature requests. Help us prioritize for Q2.

**Response:** `product-manager` scores all 20 features using RICE framework (Reach, Impact, Confidence, Effort), groups into must-have/should-have/nice-to-have, and produces a Q2 roadmap with 3 monthly milestones. `business-strategy-expert` overlays competitive urgency — 3 features are table stakes competitors already have, 2 are differentiation opportunities.

**Example 2 — PRD writing:**

**User:** Write a PRD for adding team collaboration features to our note-taking app.

**Response:** `product-manager` writes the PRD: problem statement, user personas (solo → team transition), feature spec (real-time cursors, comments, sharing permissions), user stories with acceptance criteria, and success metrics (DAU/MAU ratio, sharing rate). `business-strategy-expert` adds market context: collaboration is the #1 requested feature in churn surveys, and 3 competitors launched it in the last 6 months.

## Error Handling

If the bridge is unreachable:

> Bridge server is not responding. Start it with:
> `./scripts/openclaw/quickstart.sh` (Linux/macOS) or `.\scripts\openclaw\quickstart.ps1` (Windows)

If one specialist fails, findings from the other are presented with a note about the incomplete analysis.
