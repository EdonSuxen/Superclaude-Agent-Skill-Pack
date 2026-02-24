---
name: superclaude-product-manager
description: Product strategy and roadmap specialist for PRDs, user stories, feature prioritization, and stakeholder alignment. Writes product requirement documents, designs user story maps, applies RICE/ICE scoring frameworks, builds product roadmaps, and facilitates trade-off decisions between user value and engineering effort. Activates on "PRD", "product roadmap", "user stories", "feature prioritization", "product spec".
version: 1.0.0
tags: [superclaude, claude-code, product-management, prd, user-stories, roadmap, feature-prioritization, rice-scoring, stakeholder-alignment, product-strategy]
category: productivity
metadata:
  openclaw:
    emoji: "📋"
    os: [darwin, linux, win32]
    requires:
      bins: [node]
      env:
        - SUPERCLAUDE_BRIDGE_URL
        - SUPERCLAUDE_BRIDGE_TOKEN
      primaryEnv: SUPERCLAUDE_BRIDGE_TOKEN
    homepage: https://github.com/EdonSuxen/Superclaude-Agent-Skill-Pack
---

# SuperClaude Product Manager — PRDs, Roadmaps & Prioritization

A product strategy specialist that bridges user needs and engineering execution. Writes PRDs with clear acceptance criteria, designs user story maps for feature discovery, applies RICE/ICE scoring for objective prioritization, builds quarterly and annual roadmaps, and facilitates trade-off decisions between user value, engineering effort, and business impact. Prioritizes user value and business outcomes over feature count.

## When to Activate

Activate this skill when the user:

- Needs a PRD or product specification document
- Wants user stories with acceptance criteria for a feature
- Is prioritizing a feature backlog using scoring frameworks
- Needs a product roadmap or release planning
- Uses phrases like "PRD", "product roadmap", "user stories", "feature prioritization", "product spec"

## How to Call the Bridge

```
POST ${SUPERCLAUDE_BRIDGE_URL}/hooks/agent
Authorization: Bearer ${SUPERCLAUDE_BRIDGE_TOKEN}
Content-Type: application/json

{
  "message": "<the user's request, unmodified>",
  "agentId": "product-manager",
  "model": "sonnet",
  "thinking": "medium",
  "deliver": true
}
```

## Output Structure

```
## Product Specification
### Problem Statement (user pain, business opportunity)
### Solution Design (user flows, feature scope, out-of-scope)
### User Stories (persona, action, value, acceptance criteria)
### Prioritization (RICE/ICE scoring, effort estimates)
### Success Metrics (KPIs, targets, measurement plan)
```

## Example

**User:** Write a PRD for adding team workspaces to our project management SaaS. Currently everyone shares one workspace. Enterprise customers are asking for team-level separation.

**Response:** PRD structure: Problem — enterprise customers (40% of revenue) can't separate projects by team, causing permission confusion and information overload (15% of support tickets). Solution — hierarchical workspaces: Organization → Team Workspaces → Projects, with team-scoped permissions (admin, member, viewer), cross-workspace project linking, and workspace-level dashboard. User stories: "As a team lead, I want to create a workspace for my team so that we only see relevant projects" (acceptance: create workspace, invite members, set default permissions). 8 stories total, RICE scored. Out of scope: workspace templates, workspace analytics (V2). Migration: existing projects default to "General" workspace, admin assigns to teams. Success metrics: support ticket reduction 15% → 5%, enterprise plan upgrade rate +10%, workspace adoption >80% within 60 days. Timeline: 6-week build (2 sprints backend, 2 frontend, 1 migration, 1 polish).

## Error Handling

If the bridge is unreachable:

> Bridge server is not responding. Start it with:
> `./scripts/openclaw/quickstart.sh` (Linux/macOS) or `.\scripts\openclaw\quickstart.ps1` (Windows)
