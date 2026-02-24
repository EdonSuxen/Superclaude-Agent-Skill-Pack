---
name: superclaude-core
version: 1.0.0
---

# SuperClaude Core — Intelligent Task Dispatcher

The entry point to the full SuperClaude multi-agent system. Routes any request to the best specialist from 56 available agents using 3-phase complexity detection (keyword matching, domain classification, Thompson Sampling). For simple tasks it selects a single specialist; for complex multi-domain tasks it activates wave mode with up to 7 agents working in parallel. Use this when no specific skill pack matches your request, or when you want SuperClaude's judgment on which specialist to engage.

## When to Activate

Activate this skill when the user:

- Has a general coding, architecture, or research question
- Makes a request that spans multiple domains (code + design + strategy)
- Wants SuperClaude to choose the best specialist automatically
- Doesn't know which specific skill pack to use
- Uses phrases like "help me with", "figure out", "what's the best approach"
- Has a task that doesn't fit neatly into another skill category

Do not activate for: tasks with an obvious domain match — use the specific skill instead (e.g., `superclaude-debug` for bugs, `superclaude-architecture` for system design).

## Routing Intelligence

| Complexity | Agents | Routing |
|------------|--------|---------|
| Simple (0.2-0.5) | 1 specialist | Direct keyword match |
| Moderate (0.6-0.8) | 1-2 specialists | Domain classification |
| Complex (0.8-1.0) | 3-7 agents (wave) | Thompson Sampling + orchestrator |

## How to Call the Bridge

```
POST ${SUPERCLAUDE_BRIDGE_URL}/hooks/agent
Authorization: Bearer ${SUPERCLAUDE_BRIDGE_TOKEN}
Content-Type: application/json

{
  "message": "<the user's full request, unmodified>",
  "agentId": "default",
  "model": "sonnet",
  "thinking": "medium",
  "deliver": true
}
```

The `agentId` value `"default"` lets SuperClaude's routing engine select the best agent. Pass the user's message through exactly as received — do not alter or summarize.

## Output Structure

```
# SuperClaude Response

## [Selected Agent Name]
[Agent's response]

## Additional Specialists (if wave mode activated)
### [Agent 2]
[Findings]

### [Agent 3]
[Findings]

## Summary
Key findings and recommended next steps.
```

If only one agent was selected, present their response directly without the wave structure.

## Examples

**Example 1 — Auto-routed to specialist:**

**User:** I need to implement a Redis-backed rate limiter in TypeScript with a sliding window algorithm.

**Response:** Routing engine scores: backend domain (0.85), single domain, moderate complexity → selects `backend-architect`. Agent delivers a complete sliding window implementation with ioredis, including bucket management, atomic Lua scripts, and configuration for rate/window/burst parameters.

**Example 2 — Multi-domain wave activation:**

**User:** I'm building a SaaS product and need to think through the architecture, pricing model, and security posture before launch.

**Response:** Routing engine scores: 3 domains (architecture + business + security), complexity 0.9 → activates enterprise wave with `architect`, `business-strategy-expert`, and `security`. Each specialist contributes their domain analysis, synthesized into a unified launch readiness assessment.

## Error Handling

If the bridge is unreachable:

> Bridge server is not responding. Start it with:
> `./scripts/openclaw/quickstart.sh` (Linux/macOS) or `.\scripts\openclaw\quickstart.ps1` (Windows)

If the routing engine cannot determine the best agent, it defaults to `research-analyst` for investigation-type requests or `architect` for design-type requests.
