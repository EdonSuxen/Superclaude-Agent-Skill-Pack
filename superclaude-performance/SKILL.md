---
name: superclaude-performance
description: Performance optimization using two specialists — performance-engineer (profiling, critical-path analysis, caching strategy, bundle optimization, database tuning) and analyzer (root cause investigation, bottleneck identification, systematic debugging). Returns before/after benchmarks with targeted optimizations. Activates on "make this faster", "find the bottleneck", "p95 latency", "why is this slow".
version: 1.0.0
tags: [superclaude, claude-code, performance, profiling, optimization, latency, caching, bundle-size, memory, scalability]
category: developer-tools
metadata:
  openclaw:
    emoji: "⚡"
    os: [darwin, linux, win32]
    requires:
      bins: [node]
      env:
        - SUPERCLAUDE_BRIDGE_URL
        - SUPERCLAUDE_BRIDGE_TOKEN
      primaryEnv: SUPERCLAUDE_BRIDGE_TOKEN
    homepage: https://github.com/EdonSuxen/Superclaude-Agent-Skill-Pack
---

# SuperClaude Performance — Measure-First Optimization

Two specialists apply a rigorous measure-first methodology to performance problems. `performance-engineer` profiles and optimizes — flame graphs, critical path analysis, caching strategies, bundle size reduction, database query tuning, and memory leak detection. `analyzer` investigates root causes — systematic hypothesis testing, evidence-based debugging, pattern recognition across similar issues, and regression identification. Together they produce optimizations backed by concrete before/after measurements, not guesswork.

## When to Activate

Activate this skill when the user:

- Has a slow application, API, or page load that needs optimization
- Wants to reduce p95/p99 latency for specific endpoints
- Needs bundle size analysis or frontend performance optimization
- Has memory leaks, CPU spikes, or resource exhaustion issues
- Uses phrases like "make this faster", "find the bottleneck", "p95 latency", "why is this slow"
- Wants to set and enforce performance budgets

Do not activate for: general code review (use `superclaude-code-review`) or infrastructure scaling (use `superclaude-cloud-infra`).

## Agents in This Wave

| Agent | Role | Focus |
|-------|------|-------|
| `performance-engineer` | Lead | Profiling, caching, bundle optimization, database tuning, benchmarks |
| `analyzer` | Specialist | Root cause investigation, bottleneck identification, evidence-based debugging |

Wave strategy: systematic | Synthesis: lead_agent | Model: Sonnet

## How to Call the Bridge

```
POST ${SUPERCLAUDE_BRIDGE_URL}/hooks/agent
Authorization: Bearer ${SUPERCLAUDE_BRIDGE_TOKEN}
Content-Type: application/json

{
  "message": "<the user's request, unmodified>",
  "agentId": "performance",
  "model": "sonnet",
  "thinking": "medium",
  "deliver": true
}
```

## Output Structure

```
# Performance Report

## Profiling Results — performance-engineer
### Measurements (before)
### Bottleneck Analysis
### Optimization Plan (ranked by impact)
### Expected Results (after)

## Root Cause Analysis — analyzer
### Investigation Findings
### Contributing Factors
### Regression Analysis

## Recommended Next Steps
1. [Highest-impact optimization]
2. [Benchmarks to validate improvements]
```

## Examples

**Example 1 — API endpoint latency:**

**User:** Our /api/search endpoint takes 3 seconds. Target is under 200ms.

**Response:** `analyzer` traces the request path and identifies 3 contributing factors: N+1 query pattern (47 DB calls), missing index on search column, and synchronous PDF generation blocking the response. `performance-engineer` applies fixes: batch query with DataLoader (47→2 calls), composite index, and async PDF generation with webhook callback. Result: 3000ms → 140ms.

**Example 2 — Frontend bundle analysis:**

**User:** Our React app takes 8 seconds to load on mobile. Help us optimize.

**Response:** `performance-engineer` analyzes the bundle: 2.4MB JavaScript (moment.js 70KB, lodash 25KB, unused routes 800KB), no code splitting, unoptimized images (3MB). Recommends: date-fns replacement, tree-shaking, route-based code splitting, and responsive image srcset. `analyzer` identifies a render-blocking CSS file and third-party script adding 1.5s to First Contentful Paint.

## Error Handling

If the bridge is unreachable:

> Bridge server is not responding. Start it with:
> `./scripts/openclaw/quickstart.sh` (Linux/macOS) or `.\scripts\openclaw\quickstart.ps1` (Windows)

If one specialist fails, findings from the other are presented with a note about the incomplete analysis.
