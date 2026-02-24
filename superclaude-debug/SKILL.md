---
name: superclaude-debug
description: Root cause analysis and debugging using two SuperClaude specialists — analyzer (systematic evidence-based root cause investigation) and testing-strategist (reproduction test design and regression prevention). Returns a diagnosis with a targeted fix and test plan.
version: 1.0.0
tags: [superclaude, claude-code, debugging, root-cause, repair-loop, troubleshooting, stack-trace, error-analysis, test-reproduction]
category: developer-tools
metadata:
  openclaw:
    emoji: "🐛"
    os: [darwin, linux, win32]
    requires:
      bins: [node]
      env:
        - SUPERCLAUDE_BRIDGE_URL
        - SUPERCLAUDE_BRIDGE_TOKEN
      primaryEnv: SUPERCLAUDE_BRIDGE_TOKEN
    homepage: https://github.com/EdonSuxen/Superclaude-Agent-Skill-Pack
---

# SuperClaude Debug — Analyzer and Testing-Strategist Wave

This skill coordinates two SuperClaude specialists: `analyzer` (root cause investigation using systematic evidence-based reasoning — never assumes, always traces) and `testing-strategist` (designs reproduction tests and regression test plans to prevent the bug from returning). Together they diagnose and contain the problem.

## When to Activate

Activate this skill when the user:

- Reports a bug, error, or unexpected behaviour
- Pastes a stack trace, error message, or exception output
- Describes something that "used to work" but no longer does
- Asks "why is this failing", "what's wrong with", or "help me debug"
- Mentions a test that is failing unexpectedly
- Sees incorrect output from code they believe is correct
- Encounters runtime crashes, type errors, import failures, or assertion errors

## Extracting Debug Context

Before calling the bridge, gather all available evidence from the user's message. Construct a structured message that includes every piece of information present:

```
Bug report:

Error / Exception:
<paste the full error message or stack trace here>

Code involved (if provided):
<paste relevant code>

Environment:
<language/runtime version, OS, framework, relevant config — if mentioned>

Steps to reproduce (if described):
<numbered steps>

Expected behaviour:
<what the user expected>

Actual behaviour:
<what actually happened>

Additional context:
<anything else the user mentioned>
```

Only include sections for which the user provided information. If the user provided a bare stack trace with no other context, that is sufficient — pass it in the "Error / Exception" section and leave others blank.

Do not paraphrase or interpret the error before sending. Pass raw error text verbatim to preserve exact line numbers and message strings that the analyzer relies on.

## How to Call the Bridge

```
POST ${SUPERCLAUDE_BRIDGE_URL}/hooks/agent
Authorization: Bearer ${SUPERCLAUDE_BRIDGE_TOKEN}
Content-Type: application/json

{
  "message": "<structured bug report constructed above>",
  "agentId": "debug",
  "model": "opus",
  "thinking": "high",
  "deliver": false
}
```

The `agentId` value `"debug"` maps to the analyzer + testing-strategist wave. Do not substitute a different agent ID.

## Handling the Response

Parse `results`. Map personas to labels:

| persona | Label |
|---|---|
| analyzer | Root Cause Analysis |
| testing-strategist | Test Strategy and Regression Prevention |

## Formatting the Output

```
# Debug Report

## Root Cause (analyzer)

### Diagnosis
[One or two sentences stating the root cause clearly.]

### Evidence Trail
- [Evidence point 1 — what it indicates]
- [Evidence point 2 — what it indicates]
- [...]

### Contributing Factors
- [Secondary cause or condition that made the bug possible]

### Recommended Fix
[Specific, targeted description of the fix. Include code if the analyzer provided it.]

## Test Strategy (testing-strategist)

### Reproduction Test
[A minimal test case that demonstrates the bug. Include code.]

### Fix Verification Test
[A test that will pass once the fix is applied.]

### Regression Tests
- [Test scenario 1 — what it guards against]
- [Test scenario 2 — what it guards against]

## Action Checklist
- [ ] Apply fix: [one-line description]
- [ ] Run reproduction test (should now pass)
- [ ] Add regression tests to test suite
- [ ] [Any additional step recommended by the agents]
```

Always show the Root Cause section before the Test Strategy section. If the analyzer cannot identify the root cause with the provided information, it will say so — present that honestly and include the list of additional information it needs.

## Error Handling

If the bridge is unreachable:

> Bridge server is not responding. Start it with:
> `./scripts/openclaw/quickstart.sh` (Linux/macOS) or `.\scripts\openclaw\quickstart.ps1` (Windows)

If one specialist fails, present findings from the other and note the incomplete analysis. Do not guess at a root cause yourself.

If the user provides no error message and no code, respond:

> To diagnose the issue, please share at least one of: the full error message or stack trace, the code that is failing, or a description of what you expected versus what happened.

Do not call the bridge until at least one piece of diagnostic evidence is available.

## Example Conversations

**Example 1 — Stack trace:**

**User:** Getting this error in production:

```
TypeError: Cannot read properties of undefined (reading 'userId')
    at validateSession (auth/middleware.ts:34:22)
    at Layer.handle [as handle_request] (express/lib/router/layer.js:95:5)
```

**Skill action:** Extracts the stack trace into the "Error / Exception" section. Constructs the structured message. POSTs to bridge with `agentId: "debug"`. Presents diagnosis (undefined session object at middleware entry point) and a test that mocks an unauthenticated request to reproduce the null path.

**Example 2 — Failing test:**

**User:** This test was passing yesterday and now it fails with `AssertionError: expected 3 to equal 4`. The function counts unique users. Nothing changed in the function itself.

**Skill action:** Includes the assertion error, the function description, and the "nothing changed" context. The analyzer investigates data or fixture drift; testing-strategist recommends pinning test data to avoid order-dependent counts.

**Example 3 — Vague report:**

**User:** My API endpoint returns 500 sometimes but not always. It's random.

**Skill action:** Passes the description. The analyzer identifies likely non-deterministic causes (race conditions, missing error handling on async paths, connection pool exhaustion). The testing-strategist designs a load or concurrency test to reproduce the intermittent failure consistently.
