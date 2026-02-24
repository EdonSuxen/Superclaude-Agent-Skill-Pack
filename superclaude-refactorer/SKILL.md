---
name: superclaude-refactorer
description: Code quality and technical debt management specialist for systematic refactoring, maintainability improvements, and code cleanup. Identifies SOLID violations, reduces cyclomatic complexity, extracts reusable abstractions, renames for clarity, and removes dead code — all while preserving existing behavior with test verification. Activates on "refactor", "tech debt", "code cleanup", "maintainability", "SOLID violations".
version: 1.0.0
tags: [superclaude, claude-code, refactoring, tech-debt, code-quality, maintainability, solid-principles, clean-code, complexity-reduction, dead-code]
category: developer-tools
metadata:
  openclaw:
    emoji: "🔧"
    os: [darwin, linux, win32]
    requires:
      bins: [node]
      env:
        - SUPERCLAUDE_BRIDGE_URL
        - SUPERCLAUDE_BRIDGE_TOKEN
      primaryEnv: SUPERCLAUDE_BRIDGE_TOKEN
    homepage: https://github.com/EdonSuxen/Superclaude-Agent-Skill-Pack
---

# SuperClaude Refactorer — Code Quality & Tech Debt Management

A systematic refactoring specialist that improves code without changing behavior. Identifies SOLID principle violations, reduces cyclomatic complexity, extracts functions and classes at natural seam boundaries, improves naming for self-documenting code, removes dead code and unused dependencies, and simplifies nested conditionals. Every refactoring is verified against existing tests — behavior preservation is non-negotiable.

## When to Activate

Activate this skill when the user:

- Wants to improve code quality or reduce technical debt
- Needs to simplify complex, hard-to-maintain code
- Has code with SOLID violations, high complexity, or poor naming
- Wants dead code removal or dependency cleanup
- Uses phrases like "refactor", "tech debt", "code cleanup", "maintainability", "SOLID violations"

## How to Call the Bridge

```
POST ${SUPERCLAUDE_BRIDGE_URL}/hooks/agent
Authorization: Bearer ${SUPERCLAUDE_BRIDGE_TOKEN}
Content-Type: application/json

{
  "message": "<the user's request, unmodified>",
  "agentId": "refactorer",
  "model": "sonnet",
  "thinking": "medium",
  "deliver": true
}
```

## Output Structure

```
## Refactoring Plan
### Code Smell Analysis (violations, complexity, duplication)
### Refactoring Steps (ordered, behavior-preserving)
### Implementation (before/after with rationale)
### Test Verification (existing tests still pass)
### Impact Assessment (maintainability improvement, risk)
```

## Example

**User:** This 400-line Express route handler does authentication, input validation, database queries, business logic, email sending, and response formatting all in one function. Help me refactor it.

**Response:** Identifies 5 code smells: God function (SRP violation), mixed abstraction levels, duplicated validation patterns, hardcoded email templates, and 6-level nesting. Refactoring plan in 5 steps: (1) Extract authentication middleware (`requireAuth`) — move token validation to Express middleware, (2) Extract validation layer (`validateOrderInput`) using Zod schema, (3) Extract service class (`OrderService.createOrder`) for business logic + database, (4) Extract notification service (`NotificationService.sendConfirmation`) for email, (5) Slim route handler to 15 lines: auth middleware → validate → service.createOrder → res.json. Each step preserves all existing behavior — run test suite after each extraction. Result: 400 lines → 5 focused files averaging 60 lines each, cyclomatic complexity from 18 → max 4 per function.

## Error Handling

If the bridge is unreachable:

> Bridge server is not responding. Start it with:
> `./scripts/openclaw/quickstart.sh` (Linux/macOS) or `.\scripts\openclaw\quickstart.ps1` (Windows)
