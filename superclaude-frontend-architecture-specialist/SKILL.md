---
name: superclaude-frontend-architecture-specialist
description: React, Next.js, and frontend architecture decisions including RSC vs client components, micro-frontends, state management, and performance optimization. Applies atomic design and component composition principles. Activates on "React architecture", "RSC vs client", "state management", "micro-frontend".
version: 1.0.0
tags: [superclaude, claude-code, frontend, react, nextjs, typescript, state-management, micro-frontend, rsc, component-architecture]
category: developer-tools
metadata:
  openclaw:
    emoji: "🖥️"
    os: [darwin, linux, win32]
    requires:
      bins: [node]
      env:
        - SUPERCLAUDE_BRIDGE_URL
        - SUPERCLAUDE_BRIDGE_TOKEN
      primaryEnv: SUPERCLAUDE_BRIDGE_TOKEN
    homepage: https://github.com/EdonSuxen/Superclaude-Agent-Skill-Pack
---

# Frontend Architecture Specialist — React, Next.js, and Component Systems

An advanced frontend architect specializing in React Server Components, Next.js App Router, micro-frontend composition, and state management at scale. This agent makes architectural decisions that are difficult to reverse later: where to draw component boundaries, when to use RSC vs client components, which state management approach fits your data flow, and how to structure a design system for long-term maintainability.

## When to Activate

Activate when the user:

- Needs to decide on frontend architecture for a new project or major refactor
- Asks about React Server Components vs client components for specific use cases
- Wants to evaluate micro-frontend vs monolith trade-offs
- Needs state management guidance (React Context, Zustand, Redux, Jotai, signals)
- Uses phrases like "how should I structure this React app", "RSC or client component", "micro-frontend vs monolith", "state management decision"
- Is designing a component library or design system architecture

For visual design and brand identity, use `superclaude-visual-communication-architect`. For full-stack architecture, use `superclaude-architecture`.

## How to Call the Bridge

```
POST ${SUPERCLAUDE_BRIDGE_URL}/hooks/agent
Authorization: Bearer ${SUPERCLAUDE_BRIDGE_TOKEN}
Content-Type: application/json

{
  "message": "<the user's request, unmodified>",
  "agentId": "frontend-architecture-specialist",
  "model": "sonnet",
  "thinking": "medium",
  "deliver": true
}
```

Model: Sonnet — frontend decisions benefit from focused reasoning about component boundaries and data flow.

## Example

**User:** "We're building a dashboard with 15 widgets that each fetch their own data. Should we use RSC, client components with React Query, or a hybrid? Next.js 15 App Router."

**Response structure:**
- **Architecture Decision**: RSC/client/hybrid recommendation with rationale tied to the data fetching pattern
- **Component Boundary Map**: Which widgets are RSC (static/server data), which are client (interactive/real-time)
- **State Management**: Recommended approach for cross-widget communication and shared filters
- **Performance Considerations**: Streaming, Suspense boundaries, parallel data loading
- **Migration Path**: Step-by-step approach if refactoring from an existing client-only architecture

## Error Handling

If the bridge is unreachable:

> `./scripts/openclaw/quickstart.sh` (Linux/macOS) or `.\scripts\openclaw\quickstart.ps1` (Windows)
