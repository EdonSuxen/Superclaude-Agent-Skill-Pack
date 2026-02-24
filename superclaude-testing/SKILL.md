---
name: superclaude-testing
version: 1.0.0
---

# SuperClaude Testing — Strategy-First Quality Engineering

Two specialists collaborate to produce test architectures that catch real bugs, not just hit coverage numbers. `testing-strategist` designs the test pyramid — which tests to write, where mutation testing adds value, and how to structure contract tests between services. `qa` handles execution — writing the actual tests, setting up quality gates, and managing defect triage. Together they produce test plans that balance thoroughness with maintenance cost.

## When to Activate

Activate this skill when the user:

- Needs a test strategy for a new feature or existing codebase
- Wants to improve test coverage with meaningful tests (not just line hits)
- Has flaky tests that need diagnosis and stabilization
- Asks about test pyramid structure (unit vs integration vs E2E ratios)
- Uses phrases like "test strategy", "improve coverage", "what should I test", "flaky test"
- Needs quality gates for CI/CD pipelines

Do not activate for: individual test file writing (use `superclaude-qa` directly) or performance testing (use `superclaude-performance`).

## Agents in This Wave

| Agent | Role | Focus |
|-------|------|-------|
| `testing-strategist` | Lead | Test architecture, pyramid design, mutation testing strategy, contract test planning |
| `qa` | Specialist | Test implementation, quality gates, defect classification, automation setup |

Wave strategy: progressive | Synthesis: lead_agent | Model: Sonnet

## How to Call the Bridge

```
POST ${SUPERCLAUDE_BRIDGE_URL}/hooks/agent
Authorization: Bearer ${SUPERCLAUDE_BRIDGE_TOKEN}
Content-Type: application/json

{
  "message": "<the user's request, unmodified>",
  "agentId": "testing",
  "model": "sonnet",
  "thinking": "medium",
  "deliver": true
}
```

## Output Structure

```
# Test Strategy Report

## Test Pyramid Design — testing-strategist
### Unit Tests (recommended ratio and scope)
### Integration Tests (service boundaries)
### E2E Tests (critical user journeys)
### Mutation Testing Candidates

## Implementation Plan — qa
### Priority Test Cases (ranked by risk coverage)
### Quality Gate Configuration
### CI/CD Integration

## Recommended Next Steps
1. [Immediate actions]
2. [Follow-up improvements]
```

## Examples

**Example 1 — New feature test strategy:**

**User:** We're adding a payment processing module. What's the right test strategy?

**Response:** `testing-strategist` designs a pyramid: 60% unit (payment calculation, validation), 30% integration (Stripe API contract tests, database state), 10% E2E (checkout flow). `qa` writes the quality gate: all unit tests pass, integration coverage >80% on payment paths, E2E smoke on staging before deploy.

**Example 2 — Flaky test diagnosis:**

**User:** Our CI keeps failing randomly on 3 integration tests. Help fix the flakiness.

**Response:** `testing-strategist` identifies root causes — shared database state, race conditions in async assertions, time-dependent logic. `qa` implements fixes: test isolation with transactions, deterministic waits replacing timeouts, frozen clocks for time-sensitive tests.

## Error Handling

If the bridge is unreachable:

> Bridge server is not responding. Start it with:
> `./scripts/openclaw/quickstart.sh` (Linux/macOS) or `.\scripts\openclaw\quickstart.ps1` (Windows)

If one specialist fails, findings from the other are presented with a note about the incomplete analysis.
