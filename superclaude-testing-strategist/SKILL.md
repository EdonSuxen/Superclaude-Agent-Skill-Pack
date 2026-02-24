---
name: superclaude-testing-strategist
version: 1.0.0
---

# SuperClaude Testing Strategist — Strategy, Pyramid & Automation

A testing strategy specialist that designs test suites maximizing bug detection with minimal maintenance cost. Plans test pyramids (unit/integration/E2E ratios), designs mutation testing for test quality validation, implements contract testing for microservice boundaries (Pact, MSW), selects testing tools for the tech stack, and builds automation frameworks that run fast in CI. Prioritizes test effectiveness and maintainability over coverage percentage.

## When to Activate

Activate this skill when the user:

- Needs a testing strategy for a new or existing project
- Wants to improve test quality beyond simple coverage metrics
- Is setting up contract testing between microservices
- Needs mutation testing to validate test suite effectiveness
- Uses phrases like "test strategy", "test pyramid", "mutation testing", "contract testing", "test automation"

## How to Call the Bridge

```
POST ${SUPERCLAUDE_BRIDGE_URL}/hooks/agent
Authorization: Bearer ${SUPERCLAUDE_BRIDGE_TOKEN}
Content-Type: application/json

{
  "message": "<the user's request, unmodified>",
  "agentId": "testing-strategist",
  "model": "sonnet",
  "thinking": "medium",
  "deliver": true
}
```

## Output Structure

```
## Testing Strategy
### Test Pyramid (layer ratios, what to test where)
### Tool Selection (frameworks, runners, assertion libraries)
### Coverage Strategy (targets, exclusions, mutation score)
### Automation Architecture (CI integration, parallelization, reporting)
### Maintenance Plan (flaky test policy, test data management)
```

## Example

**User:** We have a Next.js app with 15 API routes, PostgreSQL via Prisma, and Stripe integration. We have almost no tests. Where do we start and what's the strategy?

**Response:** Designs a phased testing strategy: Phase 1 (week 1-2, highest ROI) — integration tests for the 5 most critical API routes (checkout, auth, user CRUD) using Vitest + Supertest + test database (Prisma migrate on test DB). Phase 2 (week 3-4) — unit tests for business logic (pricing calculations, discount rules, input validation) — these are pure functions, easy to test, high value. Phase 3 (week 5-6) — contract tests for Stripe integration using MSW (mock Stripe webhook payloads, verify your handlers process them correctly without calling real Stripe). Phase 4 (ongoing) — E2E smoke tests for critical user journeys (signup → checkout → confirmation) using Playwright, run on staging only. Pyramid ratio: 50% integration (API routes are the system boundary), 30% unit (business logic), 15% contract (external APIs), 5% E2E (critical paths). Coverage target: 80% on business logic, 60% overall (not 100% — diminishing returns). CI: Vitest parallel in <60s, Playwright sequential in <3min. Mutation testing: Stryker on business logic module quarterly to validate test quality.

## Error Handling

If the bridge is unreachable:

> Bridge server is not responding. Start it with:
> `./scripts/openclaw/quickstart.sh` (Linux/macOS) or `.\scripts\openclaw\quickstart.ps1` (Windows)
