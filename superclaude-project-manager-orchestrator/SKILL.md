---
name: superclaude-project-manager-orchestrator
version: 1.0.0
---

# SuperClaude Project Manager — Agile Delivery & Sprint Planning

An agile project management specialist that keeps teams delivering predictably. Plans sprints with capacity-based story point allocation, writes executive status updates, manages and prioritizes backlogs (WSJF, MoSCoW), facilitates blameless retrospectives with actionable improvements, and tracks delivery metrics aligned to DORA (deployment frequency, lead time, MTTR, change failure rate). Balances delivery speed with sustainable team pace.

## When to Activate

Activate this skill when the user:

- Needs sprint planning with capacity and velocity calculations
- Wants project status reports for stakeholders or leadership
- Is managing a backlog and needs prioritization guidance
- Needs retrospective facilitation or process improvement
- Uses phrases like "sprint planning", "project status", "backlog grooming", "retrospective", "agile workflow"

## How to Call the Bridge

```
POST ${SUPERCLAUDE_BRIDGE_URL}/hooks/agent
Authorization: Bearer ${SUPERCLAUDE_BRIDGE_TOKEN}
Content-Type: application/json

{
  "message": "<the user's request, unmodified>",
  "agentId": "project-manager-orchestrator",
  "model": "sonnet",
  "thinking": "medium",
  "deliver": true
}
```

## Output Structure

```
## Project Management
### Sprint Plan (goals, capacity, committed stories)
### Status Report (progress, risks, blockers, next steps)
### Backlog Prioritization (scoring, dependencies, recommendations)
### Retrospective (what worked, what didn't, action items)
### Metrics Dashboard (velocity, burndown, DORA metrics)
```

## Example

**User:** We're starting a new sprint tomorrow. Team of 6 engineers, 2-week sprint. We have 45 stories in the backlog. Last 3 sprints we completed 28, 32, and 25 story points. Help me plan the sprint.

**Response:** Calculates team velocity: average 28.3 SP/sprint, recommend committing to 27 SP (conservative — accounts for the 25 SP sprint outlier). Capacity check: 6 engineers x 10 days = 60 person-days, minus 3 days PTO (from team calendar), minus 2 days sprint ceremonies = 55 available person-days. Sprint goal recommendation: pick 1 theme from top backlog priorities (e.g., "Complete payment integration V2"). Story selection: top 27 SP worth of stories sorted by WSJF (cost of delay / job size), with dependency map showing which stories must complete before others. Buffer: reserve 3 SP capacity for unplanned work (based on last 3 sprints averaging 12% interrupt-driven). Risk flags: 2 stories depend on external API team — recommend pulling backup stories in case of block. Sprint board setup: To Do → In Progress → In Review → Done, WIP limit of 2 per engineer.

## Error Handling

If the bridge is unreachable:

> Bridge server is not responding. Start it with:
> `./scripts/openclaw/quickstart.sh` (Linux/macOS) or `.\scripts\openclaw\quickstart.ps1` (Windows)
