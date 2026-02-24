---
name: superclaude-full-stack
description: Maximum-power 7-agent enterprise wave for complex multi-domain tasks — architect (system design), backend-architect (APIs), frontend-architecture-specialist (UI/state), database-architect (data layer), testing-strategist (quality), security (hardening), and performance-engineer (optimization). The most comprehensive SuperClaude skill. Activates on "full system review", "end-to-end design", "complete architecture", "technical due diligence".
version: 1.0.0
tags: [superclaude, claude-code, full-stack, enterprise, engineering-team, system-design, technical-review, architecture, end-to-end]
category: developer-tools
metadata:
  openclaw:
    emoji: "🚀"
    os: [darwin, linux, win32]
    requires:
      bins: [node]
      env:
        - SUPERCLAUDE_BRIDGE_URL
        - SUPERCLAUDE_BRIDGE_TOKEN
      primaryEnv: SUPERCLAUDE_BRIDGE_TOKEN
    homepage: https://github.com/EdonSuxen/Superclaude-Agent-Skill-Pack
---

# SuperClaude Full-Stack — 7-Agent Enterprise Wave

The most comprehensive SuperClaude skill. Deploys 7 specialist agents simultaneously — `architect` (system design and ADRs), `backend-architect` (APIs, microservices, event-driven patterns), `frontend-architecture-specialist` (component architecture, state management, performance), `database-architect` (schema design, query optimization), `testing-strategist` (test pyramid, quality gates), `security` (threat modeling, OWASP), and `performance-engineer` (bottleneck analysis, budgets). Use this for tasks that span the entire technology stack.

## When to Activate

Activate this skill when the user:

- Needs a comprehensive technical review across the full stack
- Wants to design a complete system architecture from scratch
- Is preparing for technical due diligence (fundraising, acquisition)
- Has a feature that touches frontend, backend, database, and infrastructure
- Uses phrases like "full system review", "end-to-end design", "complete architecture"
- Needs expert guidance across 3+ technology domains simultaneously

Do not activate for: single-domain tasks — use the specific skill instead (e.g., `superclaude-architecture` for design-only, `superclaude-security-audit` for security-only).

## Agents in This Wave

| Agent | Role | Focus |
|-------|------|-------|
| `architect` | Lead | System design, ADRs, technology selection, service boundaries |
| `backend-architect` | Specialist | APIs, microservices, event-driven, reliability |
| `frontend-architecture-specialist` | Specialist | Component architecture, state management, SSR/RSC |
| `database-architect` | Specialist | Schema design, query optimization, migrations |
| `testing-strategist` | Specialist | Test pyramid, quality gates, coverage strategy |
| `security` | Specialist | Threat modeling, OWASP, compliance |
| `performance-engineer` | Specialist | Bottleneck analysis, budgets, optimization |

Wave strategy: enterprise | Synthesis: consensus | Model: Opus

## How to Call the Bridge

```
POST ${SUPERCLAUDE_BRIDGE_URL}/hooks/agent
Authorization: Bearer ${SUPERCLAUDE_BRIDGE_TOKEN}
Content-Type: application/json

{
  "message": "<the user's request, unmodified>",
  "agentId": "full-stack",
  "model": "opus",
  "thinking": "high",
  "deliver": true
}
```

## Output Structure

```
# Full-Stack Analysis

## System Architecture — architect
### Proposed Structure
### Key Design Decisions

## Backend — backend-architect
### API Design and Service Architecture
### Data Flow and Integration

## Frontend — frontend-architecture-specialist
### Component Architecture
### State Management Strategy

## Database — database-architect
### Schema Design
### Query Patterns and Indexing

## Quality Strategy — testing-strategist
### Test Pyramid
### Quality Gates

## Security — security
### Threat Model
### Security Controls

## Performance — performance-engineer
### Bottleneck Analysis
### Performance Budgets

## Recommended Next Steps
1. [Critical path items]
2. [Follow-up improvements]
```

## Examples

**Example 1 — New system design:**

**User:** I need to design a real-time collaboration platform for document editing. 100K concurrent users, CRDT-based, React frontend, PostgreSQL backend.

**Response:** `architect` designs the CRDT synchronization topology and service boundaries. `backend-architect` plans the WebSocket layer with Redis pub/sub. `frontend-architect` designs the editor component tree with operational transform integration. `database-architect` designs the document storage schema with versioning. `testing-strategist` creates a concurrency test plan. `security` identifies collaboration-specific threats (data leakage, permission escalation). `performance-engineer` sets latency budgets (50ms sync, 200ms persistence).

**Example 2 — Technical due diligence:**

**User:** We're preparing for Series A due diligence. Give me a complete technical assessment of our platform.

**Response:** All 7 specialists produce a comprehensive technical review: architecture soundness and scalability ceiling, API design and backward compatibility, frontend UX and accessibility posture, data integrity and backup strategy, test coverage and quality gates, security posture and compliance gaps, and performance benchmarks with growth projections. Synthesized into an executive summary with a risk-ranked remediation roadmap.

## Error Handling

If the bridge is unreachable:

> Bridge server is not responding. Start it with:
> `./scripts/openclaw/quickstart.sh` (Linux/macOS) or `.\scripts\openclaw\quickstart.ps1` (Windows)

With 7 agents, partial failures are more likely. Present all successful results and note any agents that did not complete. Findings from successful agents remain valid.
