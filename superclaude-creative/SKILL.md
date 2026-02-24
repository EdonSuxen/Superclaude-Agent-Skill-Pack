---
name: superclaude-creative
description: Creative design using three specialists — visual-communication-architect (brand identity, typography, data visualization, Vignelli methodology), motion-media-specialist (animation, motion graphics, Disney principles, sound design), and digital-experience-designer (UX patterns, interaction design, inclusive design). Returns comprehensive creative direction with visual, motion, and experience layers. Activates on "brand identity", "design system", "animation", "creative direction".
version: 1.0.0
tags: [superclaude, claude-code, creative-design, brand-identity, motion-graphics, ux-design, typography, animation, design-system, visual-design]
category: design
metadata:
  openclaw:
    emoji: "✨"
    os: [darwin, linux, win32]
    requires:
      bins: [node]
      env:
        - SUPERCLAUDE_BRIDGE_URL
        - SUPERCLAUDE_BRIDGE_TOKEN
      primaryEnv: SUPERCLAUDE_BRIDGE_TOKEN
    homepage: https://github.com/EdonSuxen/Superclaude-Agent-Skill-Pack
---

# SuperClaude Creative — Multi-Discipline Design Direction

Three world-class design specialists collaborate on creative projects. `visual-communication-architect` brings Vignelli's systematic approach to brand identity, typography systems, data visualization, and visual hierarchy. `motion-media-specialist` applies Disney's 12 principles of animation to motion design, micro-interactions, sound design, and video direction. `digital-experience-designer` ensures every visual decision serves the user — interaction patterns, cognitive load optimization, and WCAG accessibility compliance. Together they produce creative direction that is visually stunning, emotionally engaging, and functionally excellent.

## When to Activate

Activate this skill when the user:

- Needs comprehensive creative direction spanning visual, motion, and UX
- Is building a brand identity system (logo, typography, color, guidelines)
- Wants motion design for UI animations, loading states, or transitions
- Needs a design system that covers visual language, interaction patterns, and motion
- Uses phrases like "brand identity", "design system", "creative direction", "animation design"
- Is launching a product and needs cohesive visual+motion+UX strategy

Do not activate for: code-level frontend architecture (use `superclaude-frontend-architecture-specialist`) or pure UX research without visual design (use `superclaude-design`).

## Agents in This Wave

| Agent | Role | Focus |
|-------|------|-------|
| `visual-communication-architect` | Lead | Brand identity, typography, color theory, data visualization |
| `motion-media-specialist` | Specialist | Animation, motion graphics, micro-interactions, sound design |
| `digital-experience-designer` | Specialist | UX patterns, interaction design, accessibility, cognitive load |

Wave strategy: adaptive | Synthesis: consensus | Model: Opus

## How to Call the Bridge

```
POST ${SUPERCLAUDE_BRIDGE_URL}/hooks/agent
Authorization: Bearer ${SUPERCLAUDE_BRIDGE_TOKEN}
Content-Type: application/json

{
  "message": "<the user's request, unmodified>",
  "agentId": "creative",
  "model": "opus",
  "thinking": "high",
  "deliver": true
}
```

## Output Structure

```
# Creative Design Report

## Visual Identity — visual-communication-architect
### Brand Language
### Typography System
### Color Palette & Usage

## Motion & Animation — motion-media-specialist
### Motion Principles
### Interaction Animations
### Timing & Easing Guidelines

## User Experience — digital-experience-designer
### Interaction Patterns
### Accessibility Considerations
### Information Architecture

## Unified Creative Direction
Key themes, implementation priorities, and design token specifications.
```

## Examples

**Example 1 — Product launch brand identity:**

**User:** Create a brand identity for our developer tools startup.

**Response:** `visual-communication-architect` designs the visual system — geometric logo mark, Inter/JetBrains Mono type pairing, developer-friendly dark palette with high-contrast accents. `motion-media-specialist` creates logo animation (anticipation → reveal → settle), loading states, and transition curves. `digital-experience-designer` validates the system against WCAG AA and designs the onboarding interaction flow.

**Example 2 — Design system creation:**

**User:** Build a design system for our SaaS dashboard.

**Response:** All three specialists contribute: visual tokens (spacing scale, color semantic mapping, typography hierarchy), motion tokens (duration scale, easing library, state transitions), and UX patterns (data table interactions, form validation states, notification system). Output includes Figma-ready specifications.

## Error Handling

If the bridge is unreachable:

> Bridge server is not responding. Start it with:
> `./scripts/openclaw/quickstart.sh` (Linux/macOS) or `.\scripts\openclaw\quickstart.ps1` (Windows)

If one specialist fails, findings from the others are presented with a note about the incomplete analysis.
