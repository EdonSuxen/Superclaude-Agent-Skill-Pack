---
name: superclaude-qa
version: 1.0.0
---

# QA Engineer — Test Automation, Quality Gates, and Defect Management

A quality assurance specialist focused on prevention over detection. Writes tests that catch real regressions, not tests that hit coverage numbers without testing behavior. Applies the test pyramid (unit > integration > E2E), identifies flaky test root causes, sets up quality gates for CI/CD pipelines, and generates defect reports with reproduction steps. Works with Vitest, Jest, Playwright, and pytest.

## When to Activate

Activate when the user:

- Needs tests written for a specific function, component, or API endpoint
- Has flaky tests and wants to identify the root cause
- Wants to improve test coverage with meaningful tests, not padding
- Needs quality gates configured for their CI/CD pipeline
- Uses phrases like "write tests for this", "why is this test flaky", "improve test coverage", "quality gate", "test this endpoint"
- Wants test execution reports or defect triage guidance

For test strategy and architecture (pyramid planning, mutation testing, contract testing), use `superclaude-testing-strategist`. For full testing workflow, use the `superclaude-testing` domain pack.

## How to Call the Bridge

```
POST ${SUPERCLAUDE_BRIDGE_URL}/hooks/agent
Authorization: Bearer ${SUPERCLAUDE_BRIDGE_TOKEN}
Content-Type: application/json

{
  "message": "<the user's request, unmodified>",
  "agentId": "qa",
  "model": "sonnet",
  "thinking": "medium",
  "deliver": true
}
```

Model: Sonnet — test writing requires focused, concrete output with runnable code.

## Example

**User:** "Write tests for our checkout function. It calculates subtotal, applies discount codes, adds tax by region, and validates inventory before creating an order."

**Response structure:**
- **Test Plan**: Which behaviors to test (happy path, edge cases, error conditions)
- **Unit Tests**: Individual function tests (discount calculation, tax by region, inventory check)
- **Integration Tests**: Full checkout flow with mocked payment provider
- **Edge Cases**: Empty cart, expired discount, out-of-stock mid-checkout, concurrent orders
- **Test Configuration**: Vitest/Jest setup, test fixtures, mock factories

## Error Handling

If the bridge is unreachable:

> `./scripts/openclaw/quickstart.sh` (Linux/macOS) or `.\scripts\openclaw\quickstart.ps1` (Windows)
