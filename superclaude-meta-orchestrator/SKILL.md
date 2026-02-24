---
name: superclaude-meta-orchestrator
description: Technical multi-agent coordination orchestrator for complex tasks requiring 3+ domains, wave mode activation, and intelligent agent delegation. Decomposes large tasks into executable steps, selects optimal specialist agents, coordinates parallel execution waves, and tracks progress across multi-phase projects. Activates on "coordinate agents", "complex task", "wave mode", "multi-domain project", "orchestrate".
version: 1.0.0
tags: [superclaude, claude-code, orchestration, task-decomposition, wave-coordination, multi-agent, agent-delegation, progress-tracking, complex-tasks, parallel-execution]
category: ai
metadata:
  openclaw:
    emoji: "🧠"
    os: [darwin, linux, win32]
    requires:
      bins: [node]
      env:
        - SUPERCLAUDE_BRIDGE_URL
        - SUPERCLAUDE_BRIDGE_TOKEN
      primaryEnv: SUPERCLAUDE_BRIDGE_TOKEN
    homepage: https://github.com/EdonSuxen/Superclaude-Agent-Skill-Pack
---

# SuperClaude Meta-Orchestrator — Multi-Agent Task Coordination

The master coordinator that decomposes complex tasks and delegates to specialist agents. Handles task decomposition (breaking large goals into phased execution plans), agent selection (matching domains to the best specialist from 56 available), wave coordination (running multiple agents in parallel with dependency management), progress tracking across multi-phase projects, and quality gate enforcement at each stage boundary. Activates automatically when task complexity exceeds 0.8 or spans 3+ domains.

## When to Activate

Activate this skill when the user:

- Has a complex task spanning 3+ technical domains (e.g., frontend + backend + infrastructure)
- Needs multi-agent coordination with parallel execution waves
- Wants a large task decomposed into phased, trackable steps
- Needs intelligent agent selection for a multi-part project
- Uses phrases like "coordinate agents", "complex task", "wave mode", "multi-domain project", "orchestrate"

## How to Call the Bridge

```
POST ${SUPERCLAUDE_BRIDGE_URL}/hooks/agent
Authorization: Bearer ${SUPERCLAUDE_BRIDGE_TOKEN}
Content-Type: application/json

{
  "message": "<the user's request, unmodified>",
  "agentId": "meta-orchestrator",
  "model": "opus",
  "thinking": "high",
  "deliver": true
}
```

## Output Structure

```
## Orchestration Plan
### Task Decomposition (phases, stages, steps)
### Agent Selection (specialist assignments with rationale)
### Execution Waves (parallel groups, dependencies)
### Quality Gates (criteria per stage)
### Progress Tracking (status, blockers, next actions)
```

## Example

**User:** Build a complete authentication system for our SaaS app: OAuth2 with Google/GitHub, JWT tokens, role-based access control, and audit logging. We use Next.js, PostgreSQL, and deploy on AWS.

**Response:** Decomposes into 4 phases with 7 specialist agents: Phase 1 (Design) — `architect` designs auth flow + `database-architect` schemas + `security` threat model, parallel wave. Phase 2 (Implement) — `backend-architect` builds OAuth2 + JWT middleware + `api-architect` designs auth API contracts, sequential. Phase 3 (Integrate) — `frontend-architecture-specialist` builds login UI + `devops-engineer` configures AWS Cognito/secrets, parallel wave. Phase 4 (Verify) — `testing-strategist` designs auth test suite + `security` penetration test checklist, parallel wave. Quality gates: Phase 1 requires ADR approval, Phase 2 requires 90%+ test coverage on auth paths, Phase 4 requires zero CRITICAL findings. Total budget: 250K tokens across 4 waves.

## Error Handling

If the bridge is unreachable:

> Bridge server is not responding. Start it with:
> `./scripts/openclaw/quickstart.sh` (Linux/macOS) or `.\scripts\openclaw\quickstart.ps1` (Windows)
