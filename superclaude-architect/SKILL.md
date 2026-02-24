---
name: superclaude-architect
description: Holistic systems architecture specialist using C4 modeling, Architecture Decision Records (ADRs), and trade-off analysis. Designs maintainable, scalable systems with clear service boundaries, technology selection rationale, and migration paths. Activates on "design a system", "architecture review", "how should I structure", "write an ADR".
version: 1.0.0
tags: [superclaude, claude-code, architecture, system-design, c4-modeling, adr, scalability, service-boundaries, trade-off-analysis]
category: developer-tools
metadata:
  openclaw:
    emoji: "🏗️"
    os: [darwin, linux, win32]
    requires:
      bins: [node]
      env:
        - SUPERCLAUDE_BRIDGE_URL
        - SUPERCLAUDE_BRIDGE_TOKEN
      primaryEnv: SUPERCLAUDE_BRIDGE_TOKEN
    homepage: https://github.com/EdonSuxen/Superclaude-Agent-Skill-Pack
---

# SuperClaude Architect — Holistic Systems Design

A systems architecture specialist that designs maintainable software at every scale. Uses C4 modeling (Context, Container, Component, Code) for visual architecture, produces ADRs for key decisions, and provides rigorous trade-off analysis between competing approaches. Prioritizes maintainability over cleverness, scalability over premature optimization, and explicit decisions over implicit assumptions.

## When to Activate

Activate this skill when the user:

- Needs to design a new system or service from scratch
- Wants a trade-off analysis between architectural approaches (monolith vs microservices, sync vs async)
- Requests an Architecture Decision Record (ADR) for a technical choice
- Asks how to structure, organize, or decompose a codebase
- Uses phrases like "design a system", "architecture review", "how should I structure this"

## How to Call the Bridge

```
POST ${SUPERCLAUDE_BRIDGE_URL}/hooks/agent
Authorization: Bearer ${SUPERCLAUDE_BRIDGE_TOKEN}
Content-Type: application/json

{
  "message": "<the user's request, unmodified>",
  "agentId": "architect",
  "model": "opus",
  "thinking": "high",
  "deliver": true
}
```

## Output Structure

```
## Architecture Recommendation
### Proposed Structure (C4 context + container diagrams)
### Key Design Decisions (ADR format: context, decision, consequences)
### Trade-off Analysis (approach comparison table)
### Migration Path (if evolving existing system)
### Recommended Next Steps
```

## Example

**User:** We have a monolithic Django app serving 50K users. We want to extract the payment system into its own service. How should we approach this?

**Response:** Produces a C4 container diagram showing the extraction boundary. ADR documents the decision to use event-driven communication (Kafka) over synchronous HTTP, with consequences listed. Trade-off table compares strangler fig vs big bang migration. Recommends starting with a shared database pattern and gradually migrating to event sourcing over 3 phases.

## Error Handling

If the bridge is unreachable:

> Bridge server is not responding. Start it with:
> `./scripts/openclaw/quickstart.sh` (Linux/macOS) or `.\scripts\openclaw\quickstart.ps1` (Windows)
