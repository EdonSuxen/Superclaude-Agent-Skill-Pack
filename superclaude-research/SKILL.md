---
name: superclaude-research
description: Deep research and evidence synthesis using two specialists — research-analyst (market research, literature reviews, fact-checking, competitive analysis, source evaluation) and scribe (structured documentation, clear writing, audience-aware formatting). Returns comprehensive research reports with cited sources and actionable recommendations. Activates on "research this topic", "competitive analysis", "literature review", "fact-check this claim".
version: 1.0.0
tags: [superclaude, claude-code, research, analysis, literature-review, fact-checking, competitive-analysis, evidence-synthesis, market-research]
category: research
metadata:
  openclaw:
    emoji: "📚"
    os: [darwin, linux, win32]
    requires:
      bins: [node]
      env:
        - SUPERCLAUDE_BRIDGE_URL
        - SUPERCLAUDE_BRIDGE_TOKEN
      primaryEnv: SUPERCLAUDE_BRIDGE_TOKEN
    homepage: https://github.com/EdonSuxen/Superclaude-Agent-Skill-Pack
---

# SuperClaude Research — Evidence Synthesis & Documentation

Two specialists turn questions into structured knowledge. `research-analyst` handles the investigation — systematic literature reviews, market research, competitive analysis, fact-checking with source credibility scoring, and information synthesis across multiple domains. `scribe` transforms raw findings into polished, audience-appropriate documentation with clear structure, proper citations, and progressive disclosure.

## When to Activate

Activate this skill when the user:

- Needs a comprehensive literature review or technology survey
- Wants competitive analysis with feature comparisons and market positioning
- Requires fact-checking with source evaluation and confidence levels
- Is exploring a new domain and needs structured knowledge gathering
- Uses phrases like "research this", "competitive analysis", "what's the state of the art", "fact-check"
- Needs findings presented as a formal report or executive summary

Do not activate for: code analysis (use `superclaude-analyze`) or architectural decisions (use `superclaude-architecture`).

## Agents in This Wave

| Agent | Role | Focus |
|-------|------|-------|
| `research-analyst` | Lead | Literature review, market research, fact-checking, source credibility, synthesis |
| `scribe` | Specialist | Report structure, audience adaptation, citations, progressive disclosure |

Wave strategy: progressive | Synthesis: lead_agent | Model: Sonnet

## How to Call the Bridge

```
POST ${SUPERCLAUDE_BRIDGE_URL}/hooks/agent
Authorization: Bearer ${SUPERCLAUDE_BRIDGE_TOKEN}
Content-Type: application/json

{
  "message": "<the user's request, unmodified>",
  "agentId": "research",
  "model": "sonnet",
  "thinking": "medium",
  "deliver": true
}
```

## Output Structure

```
# Research Report

## Executive Summary
[Key findings in 3-5 bullet points]

## Investigation — research-analyst
### Methodology
### Key Findings (with confidence levels)
### Source Analysis
### Competitive Landscape (if applicable)

## Documentation — scribe
### Structured Report
### Recommendations
### Further Reading

## Recommended Next Steps
1. [Immediate actions based on findings]
2. [Areas requiring deeper investigation]
```

## Examples

**Example 1 — Technology evaluation:**

**User:** We're choosing between Kafka, RabbitMQ, and Pulsar for our event bus. Research the tradeoffs.

**Response:** `research-analyst` evaluates all three across 8 dimensions (throughput, latency, ordering, exactly-once, ecosystem, operations complexity, cost, community). Sources include official benchmarks, production case studies, and recent conference talks. `scribe` produces a comparison matrix, decision framework, and executive summary tailored to the team's scale.

**Example 2 — Market research:**

**User:** What's the current state of AI code assistants? Who are the key players?

**Response:** `research-analyst` maps 12 products across capability tiers, pricing models, and benchmark performance (SWE-bench, HumanEval). Identifies 3 emerging trends and 2 market gaps. `scribe` formats as an industry landscape report with competitive positioning chart and investment thesis summary.

## Error Handling

If the bridge is unreachable:

> Bridge server is not responding. Start it with:
> `./scripts/openclaw/quickstart.sh` (Linux/macOS) or `.\scripts\openclaw\quickstart.ps1` (Windows)

If one specialist fails, findings from the other are presented with a note about the incomplete analysis.
