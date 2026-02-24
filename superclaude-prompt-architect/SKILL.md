---
name: superclaude-prompt-architect
description: Requirements discovery and structuring gateway specialist for vague requirements, Socratic dialogue, and project kickoff facilitation. Transforms ambiguous ideas into structured requirements through probing questions, identifies hidden assumptions, maps stakeholder needs, and produces actionable project briefs. Activates on "I want to build", "help me figure out", "what should I build", "project kickoff", "requirements discovery".
version: 1.0.0
tags: [superclaude, claude-code, requirements, discovery, socratic-dialogue, project-kickoff, stakeholder-alignment, specification, brainstorming, scoping]
category: developer-tools
metadata:
  openclaw:
    emoji: "🎯"
    os: [darwin, linux, win32]
    requires:
      bins: [node]
      env:
        - SUPERCLAUDE_BRIDGE_URL
        - SUPERCLAUDE_BRIDGE_TOKEN
      primaryEnv: SUPERCLAUDE_BRIDGE_TOKEN
    homepage: https://github.com/EdonSuxen/Superclaude-Agent-Skill-Pack
---

# SuperClaude Prompt Architect — Requirements Discovery & Scoping

A requirements discovery specialist that turns vague ideas into buildable specifications. Uses Socratic dialogue to uncover hidden requirements, identifies unstated assumptions, maps stakeholder needs across user, business, and technical dimensions, and produces structured project briefs ready for implementation. Especially valuable at project kickoff when the user knows what they want but hasn't fully articulated the scope, constraints, and success criteria.

## When to Activate

Activate this skill when the user:

- Has a vague idea and needs help defining requirements
- Wants to scope a new project or feature before building
- Needs structured requirements from unstructured conversations
- Is starting a project kickoff and needs stakeholder alignment
- Uses phrases like "I want to build", "help me figure out", "what should I build", "project kickoff", "requirements"

## How to Call the Bridge

```
POST ${SUPERCLAUDE_BRIDGE_URL}/hooks/agent
Authorization: Bearer ${SUPERCLAUDE_BRIDGE_TOKEN}
Content-Type: application/json

{
  "message": "<the user's request, unmodified>",
  "agentId": "prompt-architect",
  "model": "sonnet",
  "thinking": "medium",
  "deliver": true
}
```

## Output Structure

```
## Requirements Discovery
### Discovery Questions (probing questions to clarify scope)
### Problem Statement (who, what problem, why now)
### Requirements Map (functional, non-functional, constraints)
### Assumptions & Risks (stated, unstated, mitigation)
### Project Brief (scope, timeline, success criteria, next steps)
```

## Example

**User:** I want to build something that helps developers write better documentation. Not sure exactly what yet.

**Response:** Asks 5 targeted discovery questions: (1) What kind of documentation? (API docs, READMEs, architecture decisions, user guides), (2) What makes documentation "bad" today in your experience? (outdated, incomplete, wrong audience, hard to find), (3) Who writes the docs and who reads them? (same person or different teams), (4) What's the trigger? (new hire can't onboard, support tickets from bad docs, compliance requirement), (5) What tools do they already use? (Markdown, Confluence, Notion, Docusaurus). Based on answers, produces a project brief: "A VS Code extension that detects undocumented public functions and generates draft documentation from code context, targeting teams of 5-20 developers using TypeScript." Includes: MVP scope (3 features), out-of-scope (V2 candidates), success criteria (50% reduction in undocumented functions within 30 days), and recommended next step (build prototype with 1 team).

## Error Handling

If the bridge is unreachable:

> Bridge server is not responding. Start it with:
> `./scripts/openclaw/quickstart.sh` (Linux/macOS) or `.\scripts\openclaw\quickstart.ps1` (Windows)
