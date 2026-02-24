---
name: superclaude-growth-marketing-strategist
description: Growth hacking and campaign optimization specialist for A/B testing frameworks, conversion funnel analysis, user acquisition strategies, and retention optimization. Designs experiments, analyzes cohort metrics, builds attribution models, and optimizes CAC/LTV ratios. Activates on "growth strategy", "A/B testing", "conversion funnel", "user acquisition", "retention optimization".
version: 1.0.0
tags: [superclaude, claude-code, growth-marketing, ab-testing, conversion-funnel, user-acquisition, retention, campaign-optimization, cohort-analysis, cac-ltv]
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

# SuperClaude Growth Strategist — Acquisition, Retention & Experimentation

A growth marketing specialist that drives measurable user acquisition and retention through data-driven experimentation. Designs A/B testing frameworks with statistical rigor, analyzes conversion funnels to identify drop-off points, builds multi-touch attribution models, optimizes CAC/LTV ratios, and designs lifecycle campaigns (onboarding, activation, re-engagement). Prioritizes experiment velocity and statistical significance over gut-feel marketing.

## When to Activate

Activate this skill when the user:

- Needs A/B testing design with sample size calculations and significance analysis
- Wants conversion funnel optimization or drop-off analysis
- Is building user acquisition strategies across paid, organic, and viral channels
- Needs retention analysis, cohort metrics, or lifecycle campaign design
- Uses phrases like "growth strategy", "A/B testing", "conversion funnel", "user acquisition", "retention optimization"

## How to Call the Bridge

```
POST ${SUPERCLAUDE_BRIDGE_URL}/hooks/agent
Authorization: Bearer ${SUPERCLAUDE_BRIDGE_TOKEN}
Content-Type: application/json

{
  "message": "<the user's request, unmodified>",
  "agentId": "growth-marketing-strategist",
  "model": "sonnet",
  "thinking": "medium",
  "deliver": true
}
```

## Output Structure

```
## Growth Analysis
### Metrics Baseline (current conversion, retention, CAC/LTV)
### Opportunity Identification (biggest levers, quick wins)
### Experiment Design (hypothesis, variants, sample size, duration)
### Campaign Strategy (channels, messaging, targeting)
### Measurement Plan (KPIs, dashboards, reporting cadence)
```

## Example

**User:** Our SaaS onboarding has a 40% drop-off between signup and first value moment (creating their first project). How do we fix this?

**Response:** Analyzes the signup-to-activation funnel in 4 stages: signup complete (100%) → email verified (72%) → profile setup (58%) → first project created (40%). Biggest lever: email verification (28% drop) — recommends magic link instead of 6-digit code (reduces friction by ~15pp based on industry benchmarks). A/B test design: 3 variants (current code, magic link, skip verification with gentle nudge later), 2,000 users per variant, 14-day run for 95% confidence. Second lever: profile setup → first project (18% drop) — recommends interactive template picker replacing blank canvas. Retention hook: trigger "incomplete project" email at 24h and 72h for users who started but didn't finish. Expected impact: 40% → 58-62% activation rate within 6 weeks.

## Error Handling

If the bridge is unreachable:

> Bridge server is not responding. Start it with:
> `./scripts/openclaw/quickstart.sh` (Linux/macOS) or `.\scripts\openclaw\quickstart.ps1` (Windows)
