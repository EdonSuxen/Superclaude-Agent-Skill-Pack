---
name: superclaude-growth
description: Growth strategy using two specialists — growth-marketing-strategist (acquisition funnels, A/B testing, campaign optimization, viral loops, retention strategies) and data-analyst-expert (funnel analytics, cohort analysis, experiment design, KPI dashboards). Returns data-backed growth plans with measurable experiments. Activates on "improve conversion", "growth strategy", "A/B test", "reduce churn".
version: 1.0.0
tags: [superclaude, claude-code, growth-marketing, ab-testing, conversion, retention, funnel-analysis, analytics, experimentation, acquisition]
category: productivity
metadata:
  openclaw:
    emoji: "📈"
    os: [darwin, linux, win32]
    requires:
      bins: [node]
      env:
        - SUPERCLAUDE_BRIDGE_URL
        - SUPERCLAUDE_BRIDGE_TOKEN
      primaryEnv: SUPERCLAUDE_BRIDGE_TOKEN
    homepage: https://github.com/EdonSuxen/Superclaude-Agent-Skill-Pack
---

# SuperClaude Growth — Data-Driven Growth Strategy

Two specialists combine marketing creativity with analytical rigor. `growth-marketing-strategist` designs growth experiments — acquisition channels, viral loop mechanics, onboarding optimization, retention hooks, and referral programs. `data-analyst-expert` provides the analytical foundation — funnel analysis to identify drop-off points, cohort analysis for retention patterns, experiment sample size calculations, and KPI dashboards to track impact. Together they produce growth plans that are creative yet measurable.

## When to Activate

Activate this skill when the user:

- Needs a growth strategy for user acquisition or retention
- Wants to design and analyze A/B tests or experiments
- Has conversion funnel issues and needs optimization recommendations
- Is planning campaigns, referral programs, or viral mechanics
- Uses phrases like "improve conversion", "growth strategy", "A/B test", "reduce churn"
- Needs to build growth dashboards or track product-led growth metrics

Do not activate for: pure data pipeline work (use `superclaude-data`) or business strategy without growth focus (use `superclaude-product`).

## Agents in This Wave

| Agent | Role | Focus |
|-------|------|-------|
| `growth-marketing-strategist` | Lead | Acquisition, retention, viral loops, campaigns, experiment design |
| `data-analyst-expert` | Specialist | Funnel analytics, cohort analysis, statistical significance, KPIs |

Wave strategy: adaptive | Synthesis: consensus | Model: Sonnet

## How to Call the Bridge

```
POST ${SUPERCLAUDE_BRIDGE_URL}/hooks/agent
Authorization: Bearer ${SUPERCLAUDE_BRIDGE_TOKEN}
Content-Type: application/json

{
  "message": "<the user's request, unmodified>",
  "agentId": "growth",
  "model": "sonnet",
  "thinking": "medium",
  "deliver": true
}
```

## Output Structure

```
# Growth Strategy Report

## Growth Plan — growth-marketing-strategist
### Channel Strategy
### Experiment Designs (hypothesis, variant, metric)
### Retention Mechanics
### Referral/Viral Loop Design

## Analytics Framework — data-analyst-expert
### Funnel Analysis
### Cohort Retention Curves
### Sample Size & Duration Calculations
### KPI Dashboard Design

## Recommended Next Steps
1. [Highest-impact experiment to run first]
2. [Metrics to instrument]
```

## Examples

**Example 1 — SaaS onboarding optimization:**

**User:** Only 15% of signups reach our aha moment. Help us improve onboarding.

**Response:** `growth-marketing-strategist` identifies 3 interventions: interactive product tour instead of video, personalized first-run experience based on user role, and activation email sequence targeting day 1/3/7 milestones. `data-analyst-expert` builds a cohort analysis showing where users drop off, calculates sample sizes for A/B tests, and designs the experiment tracking plan.

**Example 2 — Referral program design:**

**User:** Design a referral program for our mobile app.

**Response:** `growth-marketing-strategist` designs a two-sided incentive: referrer gets premium month, invitee gets extended trial, with viral coefficient targets and share mechanic options (deep links, QR codes). `data-analyst-expert` models the expected viral coefficient, calculates break-even CAC, and sets up tracking for referral attribution.

## Error Handling

If the bridge is unreachable:

> Bridge server is not responding. Start it with:
> `./scripts/openclaw/quickstart.sh` (Linux/macOS) or `.\scripts\openclaw\quickstart.ps1` (Windows)

If one specialist fails, findings from the other are presented with a note about the incomplete analysis.
