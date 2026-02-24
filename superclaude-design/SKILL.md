---
name: superclaude-design
description: UX and visual design using two specialists — digital-experience-designer (UX research, usability testing, interaction design, WCAG 2.2 accessibility) and visual-communication-architect (brand identity, typography, data visualization, Vignelli methodology). Returns UX audits, wireframes, and visual specifications. Activates on "UX review", "redesign this page", "improve user flow", "design critique".
version: 1.0.0
tags: [superclaude, claude-code, ux-design, visual-design, brand-identity, typography, data-visualization, wcag, interaction-design, wireframes]
category: design
metadata:
  openclaw:
    emoji: "🎨"
    os: [darwin, linux, win32]
    requires:
      bins: [node]
      env:
        - SUPERCLAUDE_BRIDGE_URL
        - SUPERCLAUDE_BRIDGE_TOKEN
      primaryEnv: SUPERCLAUDE_BRIDGE_TOKEN
    homepage: https://github.com/EdonSuxen/Superclaude-Agent-Skill-Pack
---

# SuperClaude Design — UX Research & Visual Communication

Two design specialists approach every project from both the user experience and visual communication angles. `digital-experience-designer` applies Nielsen-Norman methodology — usability heuristic evaluation, journey mapping, interaction design, cognitive load analysis, and WCAG 2.2 accessibility compliance. `visual-communication-architect` brings Vignelli's systematic design approach — typography systems, color theory, data visualization principles (Tufte), information hierarchy, and brand consistency. Together they produce designs that are both usable and beautiful.

## When to Activate

Activate this skill when the user:

- Needs a UX review or usability assessment of existing interfaces
- Wants to improve user flows, reduce friction, or increase conversion
- Is designing a new interface and needs both UX and visual guidance
- Needs data visualization design or information architecture
- Uses phrases like "UX review", "redesign this page", "improve user flow", "design critique"
- Wants a design system that covers both interaction patterns and visual language

Do not activate for: motion/animation design (use `superclaude-creative`) or frontend code architecture (use `superclaude-frontend-architecture-specialist`).

## Agents in This Wave

| Agent | Role | Focus |
|-------|------|-------|
| `digital-experience-designer` | Lead | UX research, usability testing, interaction design, WCAG compliance |
| `visual-communication-architect` | Specialist | Brand identity, typography, data visualization, visual hierarchy |

Wave strategy: adaptive | Synthesis: consensus | Model: Sonnet

## How to Call the Bridge

```
POST ${SUPERCLAUDE_BRIDGE_URL}/hooks/agent
Authorization: Bearer ${SUPERCLAUDE_BRIDGE_TOKEN}
Content-Type: application/json

{
  "message": "<the user's request, unmodified>",
  "agentId": "design",
  "model": "sonnet",
  "thinking": "medium",
  "deliver": true
}
```

## Output Structure

```
# Design Report

## User Experience — digital-experience-designer
### Heuristic Evaluation
### User Flow Analysis
### Interaction Recommendations
### Accessibility Notes

## Visual Design — visual-communication-architect
### Visual Hierarchy Assessment
### Typography & Color Recommendations
### Information Design
### Brand Consistency

## Unified Recommendations
Prioritized design improvements with implementation guidance.
```

## Examples

**Example 1 — SaaS dashboard redesign:**

**User:** Review the UX of our analytics dashboard — users complain it's confusing.

**Response:** `digital-experience-designer` identifies 6 usability issues: cognitive overload from 12 visible metrics, no progressive disclosure, inconsistent filter patterns, and missing empty states. `visual-communication-architect` redesigns the information hierarchy — primary KPIs elevated, sparkline charts replacing data tables, consistent Tufte-inspired data-ink ratio.

**Example 2 — Landing page design:**

**User:** Design a landing page for our API product targeting developers.

**Response:** `digital-experience-designer` maps the developer journey: hero with instant value prop, interactive code example, pricing comparison, and social proof placement. `visual-communication-architect` designs the visual system: monospace code typography, terminal-inspired dark sections, and developer-friendly iconography.

## Error Handling

If the bridge is unreachable:

> Bridge server is not responding. Start it with:
> `./scripts/openclaw/quickstart.sh` (Linux/macOS) or `.\scripts\openclaw\quickstart.ps1` (Windows)

If one specialist fails, findings from the other are presented with a note about the incomplete analysis.
