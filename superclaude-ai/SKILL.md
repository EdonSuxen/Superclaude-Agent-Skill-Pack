---
name: superclaude-ai
description: AI and ML engineering using two specialists — ai-ml-engineer (model training, inference optimization, MLOps pipelines, responsible AI) and ai-agent-orchestrator (multi-agent system design, RAG architectures, tool orchestration, agent safety). Returns architecture decisions, deployment plans, and evaluation frameworks. Activates on "build an AI agent", "deploy a model", "RAG pipeline", "LLM integration".
version: 1.0.0
tags: [superclaude, claude-code, ai, machine-learning, mlops, llm, rag, model-deployment, agent-orchestration, responsible-ai]
category: ai
metadata:
  openclaw:
    emoji: "🤖"
    os: [darwin, linux, win32]
    requires:
      bins: [node]
      env:
        - SUPERCLAUDE_BRIDGE_URL
        - SUPERCLAUDE_BRIDGE_TOKEN
      primaryEnv: SUPERCLAUDE_BRIDGE_TOKEN
    homepage: https://github.com/EdonSuxen/Superclaude-Agent-Skill-Pack
---

# SuperClaude AI — ML Engineering & Agent Architecture

Two specialists cover the full AI stack. `ai-ml-engineer` handles model training, fine-tuning, inference optimization, MLOps pipeline setup (MLflow, Weights & Biases), and responsible AI practices. `ai-agent-orchestrator` designs multi-agent systems, RAG architectures, tool-use patterns, agent safety guardrails, and LLM integration strategies. Together they produce AI systems that are performant, safe, and maintainable in production.

## When to Activate

Activate this skill when the user:

- Needs to build or deploy an AI/ML system (model training, inference, evaluation)
- Wants to design a multi-agent system or RAG pipeline
- Is integrating LLMs into an application (prompt engineering, tool use, structured output)
- Needs MLOps infrastructure (experiment tracking, model registry, A/B testing)
- Uses phrases like "build an AI agent", "deploy a model", "RAG pipeline", "LLM integration"
- Requires responsible AI evaluation (bias detection, hallucination mitigation, safety testing)

Do not activate for: data analytics/BI (use `superclaude-data`) or ETL pipelines without ML (use `superclaude-ml-ops`).

## Agents in This Wave

| Agent | Role | Focus |
|-------|------|-------|
| `ai-ml-engineer` | Lead | Model training, inference optimization, MLOps, responsible AI practices |
| `ai-agent-orchestrator` | Specialist | Multi-agent design, RAG architecture, tool orchestration, agent safety |

Wave strategy: enterprise | Synthesis: consensus | Model: Opus

## How to Call the Bridge

```
POST ${SUPERCLAUDE_BRIDGE_URL}/hooks/agent
Authorization: Bearer ${SUPERCLAUDE_BRIDGE_TOKEN}
Content-Type: application/json

{
  "message": "<the user's request, unmodified>",
  "agentId": "ai",
  "model": "opus",
  "thinking": "high",
  "deliver": true
}
```

## Output Structure

```
# AI Engineering Report

## ML Architecture — ai-ml-engineer
### Model Selection & Training Strategy
### Inference Optimization
### MLOps Pipeline Design
### Evaluation Framework

## Agent & Integration Design — ai-agent-orchestrator
### System Architecture
### Safety Guardrails
### Tool Orchestration Pattern

## Recommended Next Steps
1. [Immediate actions]
2. [Evaluation benchmarks to run]
```

## Examples

**Example 1 — RAG pipeline design:**

**User:** Build a RAG system for our internal documentation (50K pages, technical content).

**Response:** `ai-ml-engineer` designs the embedding pipeline — chunk strategy (512 tokens with 50-token overlap), embedding model selection (text-embedding-3-small for cost, ada-002 for quality), and vector store setup (Pinecone or pgvector). `ai-agent-orchestrator` designs the retrieval agent with hybrid search (semantic + BM25), re-ranking, and citation verification.

**Example 2 — Multi-agent system:**

**User:** Design a customer support system with multiple AI agents handling different ticket types.

**Response:** `ai-agent-orchestrator` designs a router agent with intent classification, specialist agents (billing, technical, returns), escalation paths, and safety guardrails. `ai-ml-engineer` recommends fine-tuned classification models for routing and sets up evaluation pipelines to track resolution rates.

## Error Handling

If the bridge is unreachable:

> Bridge server is not responding. Start it with:
> `./scripts/openclaw/quickstart.sh` (Linux/macOS) or `.\scripts\openclaw\quickstart.ps1` (Windows)

If one specialist fails, findings from the other are presented with a note about the incomplete analysis.
