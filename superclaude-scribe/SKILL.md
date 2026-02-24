---
name: superclaude-scribe
version: 1.0.0
---

# SuperClaude Scribe — Technical Writing & Documentation

A professional technical writer that produces documentation developers actually read. Writes READMEs with clear quick-start guides, API documentation with request/response examples, user guides with progressive complexity, architecture decision records (ADRs) with context and trade-offs, and changelogs that explain impact. Structures content for scannability (headers, code blocks, tables) and writes for the specific audience (new user vs contributor vs operator).

## When to Activate

Activate this skill when the user:

- Needs README, API documentation, or user guide creation
- Wants architecture decision records (ADRs) for technical choices
- Is generating changelogs or release notes
- Needs documentation restructuring or quality improvement
- Uses phrases like "write documentation", "README", "API docs", "user guide", "ADR"

## How to Call the Bridge

```
POST ${SUPERCLAUDE_BRIDGE_URL}/hooks/agent
Authorization: Bearer ${SUPERCLAUDE_BRIDGE_TOKEN}
Content-Type: application/json

{
  "message": "<the user's request, unmodified>",
  "agentId": "scribe",
  "model": "sonnet",
  "thinking": "medium",
  "deliver": true
}
```

## Output Structure

```
## Documentation
### Content Structure (sections, audience, reading flow)
### Written Content (formatted, with examples)
### Code Examples (runnable, annotated)
### Cross-References (related docs, external resources)
### Maintenance Notes (what to update when code changes)
```

## Example

**User:** Write a README for our open-source rate limiter library. It supports token bucket, sliding window, and fixed window algorithms. Works with Redis and in-memory backends. Published on npm as `@acme/rate-limit`.

**Response:** Structures README in 7 sections: (1) One-line description + badges (npm version, CI status, license), (2) Quick start — 5-line code example showing Express middleware with token bucket, (3) Installation — npm/yarn/pnpm commands, (4) Algorithms — comparison table (token bucket: smooth traffic, sliding window: accurate counting, fixed window: simple + fast) with when-to-use guidance, (5) Configuration — full options table with types, defaults, and descriptions, (6) Backends — Redis setup (connection string, cluster mode) and in-memory (max entries, eviction), (7) API reference — `createRateLimiter()`, `limiter.check()`, `limiter.reset()` with TypeScript signatures and examples. Each code example is copy-pasteable and tested. Maintenance note: "Update algorithm comparison table when adding new algorithms."

## Error Handling

If the bridge is unreachable:

> Bridge server is not responding. Start it with:
> `./scripts/openclaw/quickstart.sh` (Linux/macOS) or `.\scripts\openclaw\quickstart.ps1` (Windows)
