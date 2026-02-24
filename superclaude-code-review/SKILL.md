---
name: superclaude-code-review
description: Multi-agent code review using three SuperClaude specialists in parallel — refactorer (code quality and maintainability), QA engineer (test coverage and correctness), and security analyst (vulnerabilities and compliance). Returns a structured report with findings ranked by severity.
version: 1.0.0
tags: [superclaude, claude-code, code-review, quality, security-scan, refactoring, solid-principles, test-coverage, vulnerability-detection]
category: developer-tools
metadata:
  openclaw:
    emoji: "🔍"
    os: [darwin, linux, win32]
    requires:
      bins: [node]
      env:
        - SUPERCLAUDE_BRIDGE_URL
        - SUPERCLAUDE_BRIDGE_TOKEN
      primaryEnv: SUPERCLAUDE_BRIDGE_TOKEN
    homepage: https://github.com/EdonSuxen/Superclaude-Agent-Skill-Pack
---

# SuperClaude Code Review — Three-Specialist Wave

This skill triggers a coordinated three-agent wave: `refactorer`, `qa`, and `security`. Each specialist reviews the submitted code independently, then the bridge merges their findings. The result is a comprehensive review covering code quality, test strategy, and security in one pass.

## When to Activate

Activate this skill when the user:

- Pastes code directly into the conversation
- Mentions reviewing, checking, or auditing code
- Asks about code quality, test coverage, or security of a function, file, or module
- Uses phrases like "look at this code", "can you review this", "is this secure", "does this need tests"
- Shares a file path and asks for a review

## Extracting Code from the Message

Before calling the bridge, identify the code to review:

1. If the message contains a fenced code block (` ``` `), extract everything inside it.
2. If the message references a file path (e.g., `src/auth/middleware.ts`), include the path in the message so the agents can locate and read the file.
3. If neither is present but the user clearly intends a review, pass their message as-is and let the agents ask clarifying questions.

Do not truncate or modify the code. Pass the full content to the bridge.

## How to Call the Bridge

```
POST ${SUPERCLAUDE_BRIDGE_URL}/hooks/agent
Authorization: Bearer ${SUPERCLAUDE_BRIDGE_TOKEN}
Content-Type: application/json

{
  "message": "Please review the following code:\n\n<extracted code or file reference>\n\nContext from user: <any additional context the user provided>",
  "agentId": "code-review",
  "model": "opus",
  "thinking": "high",
  "deliver": false
}
```

The `agentId` value `"code-review"` maps to a pre-configured three-agent wave on the bridge. Do not change it.

## Handling the Response

The bridge returns results from up to three specialists. Parse `results` and present each finding set under its own section heading derived from the `persona` field:

```
## Code Quality — refactorer
[findings]

## Test Strategy — qa
[findings]

## Security Analysis — security
[findings]
```

If `results` contains a `combined` field that is already merged, use it directly but still apply the section structure above by scanning for each persona's name in the combined text.

## Formatting the Report

Structure the output as a reviewers' report:

```
# Code Review Report

## Critical Issues
- [List any findings rated critical or high-severity across all three specialists]

## Code Quality (refactorer)
### What Works Well
- ...
### Suggested Improvements
- ...

## Test Coverage (qa)
### Coverage Gaps
- ...
### Recommended Tests
- ...

## Security (security)
### Vulnerabilities Found
- ...
### Compliance Notes
- ...

## Summary
One paragraph summarising the overall health of the code and the single most important action to take.
```

Always show critical issues first, regardless of which specialist found them. If no critical issues exist, state that explicitly in the Critical Issues section.

## Error Handling

If the bridge is unreachable:

> Bridge server is not responding. Start it with:
> `./scripts/openclaw/quickstart.sh` (Linux/macOS) or `.\scripts\openclaw\quickstart.ps1` (Windows)

If one specialist fails, present findings from the others and note which specialist was unavailable. Never silently drop a specialist's section.

If the user provides no code and no file path, respond:

> Please share the code you would like reviewed — paste it directly or provide a file path.

## Example Conversations

**Example 1 — Inline code:**

**User:** Can you review this? I'm not sure if it's safe.

```javascript
app.get('/user/:id', (req, res) => {
  const query = `SELECT * FROM users WHERE id = ${req.params.id}`;
  db.query(query, (err, rows) => res.json(rows));
});
```

**Skill action:** Extracts the code block, constructs the bridge message with `agentId: "code-review"`, presents structured report.

**Example 2 — File reference:**

**User:** Review `src/services/payment-processor.ts` before I merge this PR.

**Skill action:** Passes the file path in the bridge message. Agents read the file from the repository and return findings.

**Example 3 — Vague request:**

**User:** Can you check my auth code?

**Skill action:** Passes the message as-is with `agentId: "code-review"`. Agents will request the code if needed.
