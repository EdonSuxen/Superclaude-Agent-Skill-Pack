---
name: superclaude-backend-architect
description: Server-side architecture, microservices design, API patterns, and reliability engineering. Applies reliability-first principles with circuit breakers, retries, and graceful degradation. Activates on "design this API", "microservices vs monolith", "backend architecture", "handle load spikes".
version: 1.0.0
tags: [superclaude, claude-code, backend, microservices, api, nodejs, reliability, event-driven, scalability, architecture]
category: developer-tools
metadata:
  openclaw:
    emoji: "⚙️"
    os: [darwin, linux, win32]
    requires:
      bins: [node]
      env:
        - SUPERCLAUDE_BRIDGE_URL
        - SUPERCLAUDE_BRIDGE_TOKEN
      primaryEnv: SUPERCLAUDE_BRIDGE_TOKEN
    homepage: https://github.com/EdonSuxen/Superclaude-Agent-Skill-Pack
---

# Backend Architect — Server-Side Architecture and Reliability Engineering

A server-side architecture specialist focused on reliability above all else. Designs microservices, monoliths, and hybrid architectures with built-in resilience patterns: circuit breakers, retry policies, graceful degradation, and back-pressure handling. Makes the hard decisions about service boundaries, communication patterns (sync vs async vs event-driven), and data consistency strategies that determine whether your system survives production traffic.

## When to Activate

Activate when the user:

- Needs to design or restructure a backend service architecture
- Asks about microservices vs monolith for their specific use case
- Wants to add reliability patterns (circuit breakers, retries, bulkheads)
- Needs help with service decomposition or bounded context boundaries
- Uses phrases like "design this API", "microservices vs monolith", "backend architecture", "how to handle load spikes", "service decomposition"
- Is designing event-driven systems, message queues, or async processing pipelines

For API contract design (OpenAPI, GraphQL schema), use `superclaude-api-architect`. For database schema design, use `superclaude-database-architect`. For full-stack architecture, use `superclaude-architecture`.

## How to Call the Bridge

```
POST ${SUPERCLAUDE_BRIDGE_URL}/hooks/agent
Authorization: Bearer ${SUPERCLAUDE_BRIDGE_TOKEN}
Content-Type: application/json

{
  "message": "<the user's request, unmodified>",
  "agentId": "backend-architect",
  "model": "sonnet",
  "thinking": "medium",
  "deliver": true
}
```

Model: Sonnet — backend architecture decisions require clear trade-off analysis without over-abstraction.

## Example

**User:** "We have a monolith handling orders, payments, and inventory. Orders are 500 RPS with spikes to 2000. Payments are failing and taking down the whole system. Should we decompose?"

**Response structure:**
- **Architecture Decision**: Decompose or not, with specific rationale tied to the failure mode described
- **Service Boundaries**: Where to split (e.g., extract payments first as it's the fault domain)
- **Communication Pattern**: Sync (REST/gRPC) vs async (message queue) for each service boundary
- **Reliability Patterns**: Circuit breaker on payment calls, bulkhead isolation, retry with backoff
- **Data Strategy**: How to handle the transaction boundary across services (saga, outbox pattern)
- **Migration Plan**: Strangler fig approach with specific extraction steps

## Error Handling

If the bridge is unreachable:

> `./scripts/openclaw/quickstart.sh` (Linux/macOS) or `.\scripts\openclaw\quickstart.ps1` (Windows)
