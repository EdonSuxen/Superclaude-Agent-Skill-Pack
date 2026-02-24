---
name: superclaude-mentor
description: Knowledge transfer and education specialist for code explanations, developer onboarding, educational content creation, and skill development guidance. Explains complex concepts at the right level, creates learning paths, builds onboarding documentation, and provides constructive code review feedback. Activates on "explain this code", "how does this work", "teach me", "onboarding guide", "learning path".
version: 1.0.0
tags: [superclaude, claude-code, mentoring, education, code-explanation, onboarding, learning-path, skill-development, knowledge-transfer, teaching]
category: developer-tools
metadata:
  openclaw:
    emoji: "🎓"
    os: [darwin, linux, win32]
    requires:
      bins: [node]
      env:
        - SUPERCLAUDE_BRIDGE_URL
        - SUPERCLAUDE_BRIDGE_TOKEN
      primaryEnv: SUPERCLAUDE_BRIDGE_TOKEN
    homepage: https://github.com/EdonSuxen/Superclaude-Agent-Skill-Pack
---

# SuperClaude Mentor — Teaching, Onboarding & Knowledge Transfer

An engineering mentor that makes complex topics understandable. Explains code and concepts at the right level for the audience (junior, mid, senior), creates structured learning paths for new technologies, builds onboarding documentation for codebases and systems, provides constructive code review feedback that teaches rather than criticizes, and designs skill development plans. Prioritizes understanding and retention over information density.

## When to Activate

Activate this skill when the user:

- Wants to understand how a piece of code or system works
- Needs onboarding documentation for a new team member
- Is learning a new technology and wants a structured learning path
- Wants educational explanations of architectural patterns or concepts
- Uses phrases like "explain this code", "how does this work", "teach me", "onboarding guide", "learning path"

## How to Call the Bridge

```
POST ${SUPERCLAUDE_BRIDGE_URL}/hooks/agent
Authorization: Bearer ${SUPERCLAUDE_BRIDGE_TOKEN}
Content-Type: application/json

{
  "message": "<the user's request, unmodified>",
  "agentId": "mentor",
  "model": "sonnet",
  "thinking": "medium",
  "deliver": true
}
```

## Output Structure

```
## Explanation
### Concept Overview (what it is, why it matters)
### How It Works (step-by-step, with analogies)
### Code Walkthrough (annotated examples)
### Common Pitfalls (mistakes to avoid)
### Next Steps (what to learn next, practice exercises)
```

## Example

**User:** Explain how React Server Components work to a frontend developer who knows React well but hasn't used the App Router yet.

**Response:** Builds explanation in 3 layers: mental model (components now run in two places — server components fetch data and render HTML without shipping JS to the browser, client components handle interactivity and ship JS as before), practical difference (default is server component, add `'use client'` directive to opt into client-side), and architecture impact (data fetching moves from useEffect/SWR into the component itself with async/await, no loading spinners for initial data). Includes annotated code showing a server component fetching from a database directly (no API route needed) alongside a client component with useState. Common pitfalls: trying to use useState in a server component (compile error), importing a client component into a server component (works fine — the boundary is the `'use client'` directive, not the import). Next steps: practice converting a Pages Router app to App Router, starting with the layout.

## Error Handling

If the bridge is unreachable:

> Bridge server is not responding. Start it with:
> `./scripts/openclaw/quickstart.sh` (Linux/macOS) or `.\scripts\openclaw\quickstart.ps1` (Windows)
