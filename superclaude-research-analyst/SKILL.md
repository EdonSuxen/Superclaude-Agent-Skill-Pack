---
name: superclaude-research-analyst
description: Information synthesis specialist for market research, literature reviews, fact-checking, competitive analysis, and comprehensive information gathering. Designs research methodologies, evaluates source credibility, synthesizes findings across multiple sources, and produces evidence-based reports with confidence levels. Activates on "research this", "competitive analysis", "literature review", "fact check", "market research".
version: 1.0.0
tags: [superclaude, claude-code, research, analysis, competitive-analysis, literature-review, fact-checking, market-research, evidence-synthesis, source-evaluation]
category: research
metadata:
  openclaw:
    emoji: "🔎"
    os: [darwin, linux, win32]
    requires:
      bins: [node]
      env:
        - SUPERCLAUDE_BRIDGE_URL
        - SUPERCLAUDE_BRIDGE_TOKEN
      primaryEnv: SUPERCLAUDE_BRIDGE_TOKEN
    homepage: https://github.com/EdonSuxen/Superclaude-Agent-Skill-Pack
---

# SuperClaude Research Analyst — Evidence-Based Information Synthesis

An information synthesis specialist that turns scattered data into actionable intelligence. Designs research methodologies, evaluates source credibility (primary vs secondary, recency, authority), synthesizes findings across multiple sources with conflict resolution, produces evidence-based reports with explicit confidence levels, and identifies knowledge gaps requiring further investigation. Prioritizes accuracy and source credibility over comprehensiveness.

## When to Activate

Activate this skill when the user:

- Needs market research or competitive landscape analysis
- Wants a literature review or technology evaluation
- Needs fact-checking or claim verification with sources
- Is comparing options and needs an objective analysis framework
- Uses phrases like "research this", "competitive analysis", "literature review", "fact check", "market research"

## How to Call the Bridge

```
POST ${SUPERCLAUDE_BRIDGE_URL}/hooks/agent
Authorization: Bearer ${SUPERCLAUDE_BRIDGE_TOKEN}
Content-Type: application/json

{
  "message": "<the user's request, unmodified>",
  "agentId": "research-analyst",
  "model": "sonnet",
  "thinking": "medium",
  "deliver": true
}
```

## Output Structure

```
## Research Report
### Methodology (approach, sources, scope)
### Key Findings (with confidence levels and citations)
### Comparative Analysis (frameworks, matrices, trade-offs)
### Knowledge Gaps (what we don't know, further research needed)
### Recommendations (evidence-based, prioritized)
```

## Example

**User:** Compare Supabase, Firebase, and PlanetScale for a B2B SaaS with 10K users, complex queries, and strict data privacy requirements (GDPR, data residency in EU).

**Response:** Evaluates across 6 dimensions with confidence ratings: Data model — PlanetScale (relational, complex joins native) > Supabase (PostgreSQL, full SQL) > Firebase (NoSQL, denormalized, complex queries difficult) [HIGH confidence]. GDPR compliance — Supabase (EU hosting available, row-level security, self-host option) > PlanetScale (SOC 2, GDPR DPA available, limited EU regions) > Firebase (Google Cloud EU regions, but data processing in US possible) [MEDIUM confidence — verify Firebase DPA terms]. Pricing at 10K users — Firebase ($25-50/mo), Supabase ($25-75/mo), PlanetScale ($39-99/mo) [HIGH confidence]. Recommendation: Supabase for this use case — PostgreSQL handles complex B2B queries, EU self-hosting solves data residency, row-level security maps well to B2B multi-tenancy. Risk: Supabase is younger (evaluate vendor lock-in with self-host escape hatch).

## Error Handling

If the bridge is unreachable:

> Bridge server is not responding. Start it with:
> `./scripts/openclaw/quickstart.sh` (Linux/macOS) or `.\scripts\openclaw\quickstart.ps1` (Windows)
