---
name: superclaude-ai-agent-orchestrator
version: 1.0.0
---

# SuperClaude AI Agent Orchestrator — Multi-Agent System Design

A specialist in designing and coordinating multi-agent AI systems. Handles RAG architecture design, agent safety guardrails, tool orchestration patterns, routing intelligence, conflict resolution between agents, and emergent behavior management. Designs systems where multiple LLM agents collaborate safely and effectively, with loop prevention, budget enforcement, and quality scoring.

## When to Activate

Activate this skill when the user:

- Is building a multi-agent AI system and needs architecture guidance
- Wants to design RAG pipelines with retrieval, generation, and evaluation
- Needs agent safety guardrails (loop prevention, budget limits, output validation)
- Is implementing tool use patterns for LLM agents
- Uses phrases like "multi-agent system", "agent orchestration", "RAG pipeline", "AI safety"

## How to Call the Bridge

```
POST ${SUPERCLAUDE_BRIDGE_URL}/hooks/agent
Authorization: Bearer ${SUPERCLAUDE_BRIDGE_TOKEN}
Content-Type: application/json

{
  "message": "<the user's request, unmodified>",
  "agentId": "ai-agent-orchestrator",
  "model": "opus",
  "thinking": "high",
  "deliver": true
}
```

## Output Structure

```
## Agent System Design
### Architecture (agent topology, communication patterns)
### Routing Strategy (task → agent mapping)
### Safety Guardrails (loop prevention, budget, validation)
### Tool Orchestration (available tools, permission model)
### Evaluation & Monitoring
### Recommended Implementation Steps
```

## Example

**User:** I want to build a customer support system with 3 AI agents: a triage agent, a technical support agent, and an escalation agent. How should I design the orchestration?

**Response:** Designs a hub-spoke topology with the triage agent as router. Defines routing rules (keyword + intent classification), handoff protocol (context summary + customer history), and safety guardrails (max 3 handoffs, 5-minute timeout, human escalation trigger). Tool permissions: triage gets read-only CRM access, technical gets knowledge base + ticket creation, escalation gets human notification + priority override. Includes evaluation metrics (resolution rate, handoff count, customer satisfaction) and monitoring dashboards.

## Error Handling

If the bridge is unreachable:

> Bridge server is not responding. Start it with:
> `./scripts/openclaw/quickstart.sh` (Linux/macOS) or `.\scripts\openclaw\quickstart.ps1` (Windows)
