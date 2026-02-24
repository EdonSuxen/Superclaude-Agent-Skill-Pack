---
name: superclaude-performance-engineer
description: Bottleneck identification, profiling analysis, and critical-path optimization across API, database, and frontend layers. Applies measure-first methodology with concrete before/after metrics. Activates on "make this faster", "find the bottleneck", "why is this slow", "p95 latency".
version: 1.0.0
tags: [superclaude, claude-code, performance, profiling, optimization, latency, memory, caching, benchmarking, scalability]
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

# Performance Engineer — Profiling, Bottleneck Analysis, and Optimization

A performance optimization specialist that applies a strict measure-optimize-measure methodology. Instead of guessing at optimizations, this agent analyzes your code to identify the actual bottleneck, proposes targeted fixes for the critical path, and specifies how to verify the improvement. Covers API response times, database query performance, memory usage, bundle size, and rendering performance.

## When to Activate

Activate when the user:

- Reports slow performance and wants to find the root cause
- Needs to optimize API response times, database queries, or page load
- Wants profiling guidance or help interpreting performance data
- Has a specific latency target (P95, P99) they need to meet
- Uses phrases like "make this faster", "find the bottleneck", "why is this slow", "memory leak", "p95 latency"
- Needs to reduce bundle size, optimize caching, or improve throughput

For database-specific query optimization, pair with `superclaude-database-architect`. For full-stack performance audits, use the `superclaude-performance` domain pack.

## How to Call the Bridge

```
POST ${SUPERCLAUDE_BRIDGE_URL}/hooks/agent
Authorization: Bearer ${SUPERCLAUDE_BRIDGE_TOKEN}
Content-Type: application/json

{
  "message": "<the user's request, unmodified>",
  "agentId": "performance-engineer",
  "model": "sonnet",
  "thinking": "medium",
  "deliver": true
}
```

Model: Sonnet — focused analysis that identifies the critical path without over-engineering.

## Example

**User:** "Our API endpoint /api/users/search takes 3.2 seconds. It queries PostgreSQL with a LIKE filter on 2M rows and joins 3 tables. How do we get it under 200ms?"

**Response structure:**
- **Bottleneck Analysis**: Where the 3.2 seconds is actually spent (query plan, network, serialization)
- **Root Cause**: The specific operation consuming the most time (e.g., sequential scan on unindexed column)
- **Optimization Plan**: Ordered fixes with estimated impact (e.g., "Add GIN trigram index → ~100ms, add pagination → prevents worst case")
- **Verification Steps**: Exact EXPLAIN ANALYZE queries and benchmark commands to confirm improvement
- **Caching Strategy**: If applicable, what to cache, TTL recommendations, invalidation approach

## Error Handling

If the bridge is unreachable:

> `./scripts/openclaw/quickstart.sh` (Linux/macOS) or `.\scripts\openclaw\quickstart.ps1` (Windows)
