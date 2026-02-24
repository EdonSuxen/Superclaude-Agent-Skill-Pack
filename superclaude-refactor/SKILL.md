---
name: superclaude-refactor
version: 1.0.0
---

# SuperClaude Refactor — Evidence-Based Code Quality

Two specialists work together to make code simpler without changing behavior. `refactorer` handles the craft — identifying SOLID violations, reducing cyclomatic complexity, extracting functions, improving naming, and removing dead code. `analyzer` provides the evidence base — mapping dependencies, tracing call chains, and quantifying complexity hotspots so refactoring effort targets the highest-impact areas first.

## When to Activate

Activate this skill when the user:

- Has accumulated tech debt and needs a prioritized reduction plan
- Wants to simplify a complex module or reduce cyclomatic complexity
- Needs to extract, inline, or restructure functions for better readability
- Is dealing with SOLID principle violations or tightly coupled code
- Uses phrases like "clean up this code", "reduce tech debt", "simplify", "refactor for maintainability"
- Wants before/after comparisons with risk assessment for each change

Do not activate for: performance optimization (use `superclaude-performance`) or full architectural redesign (use `superclaude-architecture`).

## Agents in This Wave

| Agent | Role | Focus |
|-------|------|-------|
| `refactorer` | Lead | SOLID analysis, complexity reduction, extract/inline patterns, naming, dead code |
| `analyzer` | Specialist | Dependency mapping, call chain tracing, complexity hotspot quantification |

Wave strategy: progressive | Synthesis: lead_agent | Model: Sonnet

## How to Call the Bridge

```
POST ${SUPERCLAUDE_BRIDGE_URL}/hooks/agent
Authorization: Bearer ${SUPERCLAUDE_BRIDGE_TOKEN}
Content-Type: application/json

{
  "message": "<the user's request, unmodified>",
  "agentId": "refactor",
  "model": "sonnet",
  "thinking": "medium",
  "deliver": true
}
```

## Output Structure

```
# Refactoring Report

## Complexity Analysis — analyzer
### Hotspot Map (top 5 by cyclomatic complexity)
### Dependency Graph (coupling metrics)
### Risk Assessment

## Refactoring Plan — refactorer
### Priority 1: High-Impact Changes
### Priority 2: Incremental Improvements
### Before/After Examples
### SOLID Violation Fixes

## Recommended Next Steps
1. [Safe first moves]
2. [Follow-up improvements]
```

## Examples

**Example 1 — Module simplification:**

**User:** This service file is 800 lines with 15 functions. Help me break it down.

**Response:** `analyzer` maps internal call chains and identifies 3 natural clusters (auth logic, validation, data transformation) with 4 unused helper functions. `refactorer` produces an extraction plan: 3 focused modules with clear interfaces, removes dead code, and provides before/after for the 5 most complex functions.

**Example 2 — Tech debt sprint:**

**User:** We have a sprint dedicated to tech debt. Where should we focus?

**Response:** `analyzer` scans the codebase for complexity hotspots — finds 12 files with cyclomatic complexity >15, 8 with >5 dependencies, and 3 god classes. `refactorer` prioritizes by impact: top 5 changes that reduce complexity by 40% with low regression risk, each with estimated effort and before/after examples.

## Error Handling

If the bridge is unreachable:

> Bridge server is not responding. Start it with:
> `./scripts/openclaw/quickstart.sh` (Linux/macOS) or `.\scripts\openclaw\quickstart.ps1` (Windows)

If one specialist fails, findings from the other are presented with a note about the incomplete analysis.
