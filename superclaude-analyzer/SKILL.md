---
name: superclaude-analyzer
version: 1.0.0
---

# SuperClaude Analyzer — Root Cause Investigation

An evidence-based investigation specialist that traces problems from symptoms to root causes using systematic reasoning. Never assumes — always builds evidence chains. Classifies failures (assertion vs import vs syntax vs runtime), identifies contributing factors, and maps the causal chain with confidence levels. Distinguishes correlation from causation and flags when insufficient evidence prevents a definitive diagnosis.

## When to Activate

Activate this skill when the user:

- Reports a bug and needs to understand why it's happening
- Has a system behaving unexpectedly and needs investigation
- Wants pattern recognition across multiple failure instances
- Needs systematic troubleshooting with evidence tracking
- Uses phrases like "why is this broken", "investigate", "find the root cause", "what changed"

## How to Call the Bridge

```
POST ${SUPERCLAUDE_BRIDGE_URL}/hooks/agent
Authorization: Bearer ${SUPERCLAUDE_BRIDGE_TOKEN}
Content-Type: application/json

{
  "message": "<the user's request, unmodified>",
  "agentId": "analyzer",
  "model": "sonnet",
  "thinking": "medium",
  "deliver": true
}
```

## Output Structure

```
## Investigation Report
### Diagnosis (root cause statement)
### Evidence Trail (observations → inferences)
### Contributing Factors
### Confidence Level (high/medium/low with reasoning)
### Recommended Fix
### Additional Information Needed (if diagnosis incomplete)
```

## Example

**User:** Our API returns 500 errors intermittently — about 5% of requests. It's been happening since Tuesday's deploy. The logs show "connection refused" from the database.

**Response:** Traces the evidence: 5% failure rate + connection refused + post-deploy timing suggests connection pool exhaustion rather than database outage. Checks: Tuesday's deploy likely changed concurrency or removed pool size configuration. Contributing factors: no connection timeout configured, no circuit breaker on DB calls. Recommends: check deploy diff for pool config changes, add connection pool monitoring, implement circuit breaker pattern. Confidence: high (evidence consistent with single cause).

## Error Handling

If the bridge is unreachable:

> Bridge server is not responding. Start it with:
> `./scripts/openclaw/quickstart.sh` (Linux/macOS) or `.\scripts\openclaw\quickstart.ps1` (Windows)
