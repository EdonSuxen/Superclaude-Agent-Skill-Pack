---
name: superclaude-architecture
version: 1.0.0
---

# SuperClaude Architecture — Three-Architect Wave

This skill coordinates three SuperClaude architects: `architect` (system-level design, ADRs, long-term maintainability), `backend-architect` (reliability, microservices, event-driven patterns, server-side concerns), and `api-architect` (API design, contracts, REST/GraphQL/gRPC, versioning, developer experience). All three review the problem in parallel and their outputs are merged into a unified recommendation.

## When to Activate

Activate this skill when the user:

- Asks how to design, structure, or organise a system or service
- Requests a technical plan before implementation begins
- Wants trade-off analysis between architectural approaches
- Asks about API design, endpoint structure, or schema contracts
- Mentions microservices, monoliths, event-driven architecture, CQRS, or event sourcing
- Asks for an Architecture Decision Record (ADR)
- Uses phrases like "how should I architect", "what's the best way to structure", "design a system for", "help me plan"
- Wants to evaluate a proposed design before committing to it

## Preparing the Message

Collect as much context as possible from the user's message before calling the bridge:

- What problem the system must solve
- Expected scale (users, requests per second, data volume)
- Technology constraints (existing stack, language, cloud provider)
- Non-functional requirements (latency, uptime, compliance)
- Any existing architecture that must be preserved or integrated with

If the user's message already contains this context, pass it through unchanged. Do not summarise or compress it — the architects benefit from full context.

## How to Call the Bridge

```
POST ${SUPERCLAUDE_BRIDGE_URL}/hooks/agent
Authorization: Bearer ${SUPERCLAUDE_BRIDGE_TOKEN}
Content-Type: application/json

{
  "message": "Architecture request: <user's full message, unmodified>",
  "agentId": "architecture",
  "model": "opus",
  "thinking": "high",
  "deliver": false
}
```

The `agentId` value `"architecture"` maps to the three-architect wave. Do not substitute a different agent ID.

## Handling the Response

Parse the `results` array. Each entry corresponds to one architect. Map `persona` values to human-readable labels:

| persona | Label |
|---|---|
| architect | System Architecture |
| backend-architect | Backend and Infrastructure |
| api-architect | API Design and Contracts |

If `combined` is provided and the personas are clearly delineated within it, you may use it directly with the labels applied. Otherwise, render each specialist's output under its own section.

## Formatting the Output

```
# Architecture Recommendation

## Decision Summary
One paragraph stating the recommended approach and the primary reason for choosing it over alternatives.

## Trade-off Analysis
| Approach | Pros | Cons | Recommended? |
|---|---|---|---|
| ... | ... | ... | Yes/No |

## System Architecture (architect)
### Proposed Structure
- ...
### Key Design Decisions
- Decision: [what] — Rationale: [why]
### ADR References
- ADR-001: [title] — [one-line summary]

## Backend and Infrastructure (backend-architect)
### Reliability Considerations
- ...
### Scalability Approach
- ...
### Data Layer Recommendations
- ...

## API Design and Contracts (api-architect)
### Endpoint Structure
- ...
### Versioning Strategy
- ...
### Developer Experience Notes
- ...

## Recommended Next Steps
1. [Immediate action]
2. [Short-term action]
3. [Longer-term consideration]
```

Always include the Trade-off Analysis table. If only one approach was considered, note that and explain why no alternatives were evaluated.

## Error Handling

If the bridge is unreachable:

> Bridge server is not responding. Start it with:
> `./scripts/openclaw/quickstart.sh` (Linux/macOS) or `.\scripts\openclaw\quickstart.ps1` (Windows)

If one architect's result has `success: false`, render findings from the two that succeeded and note which specialist was unavailable. Do not fabricate the missing section.

If the user's request lacks sufficient context for a meaningful architecture recommendation, ask one clarifying question before calling the bridge — the single most important piece of missing information (usually: what problem does the system solve, or what is the expected scale).

## Example Conversations

**Example 1 — New system design:**

**User:** I need to design a notification service that can send email, SMS, and push notifications to 2 million users. It needs to be reliable and support retries. We're on AWS with a Node.js backend.

**Skill action:** Passes message unchanged with `agentId: "architecture"`. Presents structured recommendation covering queue-based delivery (backend-architect), API contract for notification triggers (api-architect), and overall service topology (architect).

**Example 2 — API design:**

**User:** Should I use REST or GraphQL for a mobile app backend? We have 5 frontend clients with different data needs.

**Skill action:** Passes message with `agentId: "architecture"`. The api-architect leads the trade-off analysis; architect and backend-architect contribute holistic and operational perspectives.

**Example 3 — Existing system review:**

**User:** Here's our current microservices diagram [description]. We're hitting latency issues between the order service and inventory service. How should we restructure this?

**Skill action:** Passes the description with `agentId: "architecture"`. Architects analyse the latency problem and recommend event-driven decoupling, async patterns, or caching depending on the specifics.
