---
name: superclaude-self-improving
version: 1.1.0
---

# SuperClaude Self-Improving Agent — Continuous Learning & Pattern Evolution

A hybrid self-improvement system that captures errors, corrections, and knowledge gaps in real-time, then evolves your project's intelligence over time. Operates in two modes: **local hooks** for zero-cost real-time capture, and **bridge analysis** for deep pattern detection using TF-IDF semantic retrieval and contextual bandits.

Unlike basic learning loggers, this skill performs **semantic similarity matching** to find related learnings across sessions, **decay-weighted memory** so stale patterns fade naturally, and **automatic promotion** of recurring patterns into your project memory.

## When to Activate

Activate this skill when:

- A command or tool execution fails unexpectedly
- The user corrects Claude ("actually...", "no, that's wrong", "I meant...")
- A better approach is discovered for a recurring task
- An external API or dependency fails
- Claude's knowledge is outdated or incorrect for the current codebase
- The user asks to "review learnings", "what patterns am I repeating?", or "analyze my mistakes"
- A session ends and accumulated learnings need promotion

Do not activate for: general code review (use `superclaude-code-review`), debugging specific bugs (use `superclaude-debug`), or test failures (use `superclaude-testing`).

## Two Operating Modes

### Mode 1: Local Hooks (Zero Cost, Real-Time)

Hooks run automatically inside Claude Code — no bridge server needed. They detect errors and corrections as they happen and log structured entries to `.learnings/`.

**Prerequisites**: `jq` must be installed (`brew install jq` / `apt install jq` / `choco install jq`).

**Setup** — add to `.claude/settings.json`:

```json
{
  "hooks": {
    "PostToolUseFailure": [
      {
        "matcher": "Bash",
        "hooks": [
          {
            "type": "command",
            "command": "bash \"$CLAUDE_PROJECT_DIR\"/.claude/hooks/on-error.sh",
            "timeout": 10,
            "statusMessage": "Logging error..."
          }
        ]
      }
    ],
    "UserPromptSubmit": [
      {
        "hooks": [
          {
            "type": "command",
            "command": "bash \"$CLAUDE_PROJECT_DIR\"/.claude/hooks/on-correction.sh",
            "timeout": 10,
            "statusMessage": "Checking for corrections..."
          }
        ]
      }
    ]
  }
}
```

**What gets captured:**

| Trigger | Detection | Logged To |
|---------|-----------|-----------|
| Tool failure (Bash exit != 0) | PostToolUseFailure hook | `.learnings/ERRORS.md` |
| User correction phrase | UserPromptSubmit hook | `.learnings/LEARNINGS.md` |
| Feature request phrase | UserPromptSubmit hook | `.learnings/FEATURE_REQUESTS.md` |
| Recurring pattern (3+ times) | Bridge analysis | `.learnings/PATTERNS.md` → `CLAUDE.md` |

### Mode 2: Bridge Analysis (Deep Intelligence)

For deep analysis — pattern detection across sessions, semantic similarity matching, anti-pattern warnings — invoke the bridge:

```
POST ${SUPERCLAUDE_BRIDGE_URL}/hooks/agent
Authorization: Bearer ${SUPERCLAUDE_BRIDGE_TOKEN}
Content-Type: application/json

{
  "message": "<the user's request, unmodified>",
  "agentId": "self-improving",
  "model": "sonnet",
  "thinking": "medium",
  "deliver": true
}
```

Bridge mode activates the full self-improvement engine: TF-IDF semantic retrieval finds related learnings across your history, contextual bandits identify which approaches work best for which task types, and the anti-pattern detector flags analysis paralysis, scope creep, and hallucinated success.

**Promotion is a bridge-only operation.** When the bridge identifies learnings that recur 3+ times with semantic similarity > 0.7, it generates concrete additions for `CLAUDE.md`. Local hooks only capture — they never write to `CLAUDE.md` directly.

## Learning Log Format

Each entry follows this structure:

```markdown
## [SEVERITY] Summary — YYYY-MM-DD HH:MM  (ID: entry-XXXXXXXX)

**Area**: `[file-path or domain]`
**Trigger**: error | correction | discovery | feature-request
**Priority**: critical | high | medium | low
**Status**: new | investigating | resolved | promoted

### What Happened
[Concise description of the error, correction, or discovery]

### Context
[Reproduction steps, stack trace, or conversation excerpt]

### Resolution
[What fixed it, or suggested fix if unresolved]

### Metadata
- **Session**: [session-id]
- **Related**: [links to related learnings]
- **Promoted**: false
```

## Promotion Rules

Learnings that appear **3 or more times** across different sessions or tasks are promoted (bridge mode only):

1. **Pattern identified** — semantic similarity > 0.7 with 3+ existing entries
2. **Promotion candidate** — entry moved to `.learnings/PATTERNS.md` with merged context
3. **Project memory** — pattern appended to `CLAUDE.md` under a `## Learned Patterns` section
4. **Source entries** — marked `Status: promoted` with link to pattern

Promotion thresholds are configurable via bridge request parameters:
- `promotionThreshold`: minimum occurrences (default: 3)
- `similarityThreshold`: minimum semantic similarity (default: 0.7)

## Output Structure

### Local Mode (Hook Output)
```
[LOGGED] Tool failure captured → .learnings/ERRORS.md
  ID: entry-1740422400-12345
  Summary: Bash failed — Command exited with non-zero status code 1
  Priority: medium
```

### Bridge Mode (Deep Analysis)
```
# Self-Improvement Analysis Report

## Pattern Detection
### Recurring Patterns (3+ occurrences)
1. [HIGH] TypeScript strict mode errors after dependency updates (5 occurrences)
   → Suggested: Add pre-install type check to CI pipeline

### Semantic Clusters
- Cluster A: "dependency resolution" (7 related entries, similarity 0.82)
- Cluster B: "test mock configuration" (4 related entries, similarity 0.76)

## Anti-Pattern Warnings
- Scope creep detected: last 3 sessions expanded beyond initial task
- Approach monotony: same debugging strategy used 5x without improvement

## Promotion Candidates
1. "Always run `npm ls` before `npm install` in monorepos" → promote to CLAUDE.md
2. "Vitest mocks require `vi.resetAllMocks()` in afterEach" → promote to CLAUDE.md

## Quality Dimensions
Scores track five dimensions of project health over time:
- Truth: 0.82 — evidence-based corrections, verified claims
- Beauty: 0.75 — code elegance, structural improvements
- Knowledge: 0.88 — accumulated patterns, domain understanding
- Creation: 0.71 — novel approaches, innovative solutions
- Curiosity: 0.79 — exploration breadth, hypothesis testing
```

## Examples

**Example 1 — Automatic error capture (local hooks):**

A bash command fails during `npm install`. The `PostToolUseFailure` hook fires, receives JSON on stdin with `{ tool_name: "Bash", error: "Command exited with non-zero status code 1", tool_input: { command: "npm install" } }`. The hook extracts fields via `jq` and appends a structured entry to `.learnings/ERRORS.md` with a unique ID, timestamp, and error context. No manual action needed.

**Example 2 — User correction capture:**

**User:** Actually, that's wrong — we use pnpm here, not npm.

The `UserPromptSubmit` hook receives `{ prompt: "Actually, that's wrong — we use pnpm here, not npm." }` on stdin. It extracts the prompt via `jq`, detects "Actually, that's wrong" as a correction marker, and logs to `.learnings/LEARNINGS.md`. When the bridge later identifies 3+ similar corrections about "use pnpm not npm", it promotes the pattern to `CLAUDE.md`.

**Example 3 — Deep analysis via bridge:**

**User:** Analyze my learnings from this week. What patterns am I repeating?

The bridge runs the self-improvement engine with TF-IDF semantic retrieval. It finds 12 entries in `.learnings/`, clusters them into 3 semantic groups, identifies 2 patterns above the promotion threshold, flags 1 anti-pattern (repeated same debugging approach), and generates a report with specific `CLAUDE.md` additions.

## Hook Scripts

Both scripts receive JSON on stdin from Claude Code and require `jq` for parsing.

### `.claude/hooks/on-error.sh`

```bash
#!/bin/bash
set -euo pipefail
# PostToolUseFailure hook — captures tool failures
# Receives JSON on stdin: { tool_name, tool_input, error, is_interrupt, cwd, session_id }
# Requires: jq

INPUT=$(cat)

# Guard: reject empty or malformed JSON
if [ -z "$INPUT" ] || ! echo "$INPUT" | jq -e . > /dev/null 2>&1; then
  exit 0
fi

# Skip if user interrupted (not a real error)
IS_INTERRUPT=$(echo "$INPUT" | jq -r '.is_interrupt // false')
[ "$IS_INTERRUPT" = "true" ] && exit 0

TOOL_NAME=$(echo "$INPUT" | jq -r '.tool_name // "unknown"')
ERROR_MSG=$(echo "$INPUT" | jq -r '.error // "unknown error"' | head -c 500)
COMMAND=$(echo "$INPUT" | jq -r '.tool_input.command // ""' | head -c 500)
SESSION_ID=$(echo "$INPUT" | jq -r '.session_id // "unknown"' | cut -c1-8)

# Use $CLAUDE_PROJECT_DIR (set by Claude Code) — never trust cwd from stdin
CWD="${CLAUDE_PROJECT_DIR:-.}"
LEARNINGS_DIR="$CWD/.learnings"
mkdir -p "$LEARNINGS_DIR"

TIMESTAMP=$(date '+%Y-%m-%d %H:%M')
ENTRY_ID="entry-$(date '+%s')-$$"

{
  printf '\n## [ERROR] %s failed — %s  (ID: %s)\n\n' "$TOOL_NAME" "$TIMESTAMP" "$ENTRY_ID"
  printf '**Area**: `%s`\n' "$CWD"
  printf '**Trigger**: error\n'
  printf '**Priority**: medium\n'
  printf '**Status**: new\n\n'
  printf '### What Happened\n'
  printf 'Tool `%s` failed.\n\n' "$TOOL_NAME"
  printf '### Context\n```\n'
  printf '%s\n' "$ERROR_MSG"
  [ -n "$COMMAND" ] && printf 'Command: %s\n' "$COMMAND"
  printf '```\n\n'
  printf '### Resolution\n[Pending — to be filled when resolved]\n\n'
  printf '### Metadata\n- **Session**: %s\n- **Promoted**: false\n---\n' "$SESSION_ID"
} >> "$LEARNINGS_DIR/ERRORS.md"

echo "[LOGGED] Tool failure → .learnings/ERRORS.md (ID: $ENTRY_ID)"
```

### `.claude/hooks/on-correction.sh`

```bash
#!/bin/bash
set -euo pipefail
# UserPromptSubmit hook — captures user corrections and feature requests
# Receives JSON on stdin: { prompt, session_id, cwd }
# Requires: jq

INPUT=$(cat)

# Guard: reject empty or malformed JSON
if [ -z "$INPUT" ] || ! echo "$INPUT" | jq -e . > /dev/null 2>&1; then
  exit 0
fi

PROMPT=$(echo "$INPUT" | jq -r '.prompt // ""')
[ -z "$PROMPT" ] && exit 0

# Truncate prompt to prevent PII leakage (300 chars captures the signal)
PROMPT_SAFE="${PROMPT:0:300}"
SESSION_ID=$(echo "$INPUT" | jq -r '.session_id // "unknown"' | cut -c1-8)

# Use $CLAUDE_PROJECT_DIR (set by Claude Code) — never trust cwd from stdin
CWD="${CLAUDE_PROJECT_DIR:-.}"
LEARNINGS_DIR="$CWD/.learnings"
mkdir -p "$LEARNINGS_DIR"

TIMESTAMP=$(date '+%Y-%m-%d %H:%M')
ENTRY_ID="entry-$(date '+%s')-$$"

# Feature request detection
if echo "$PROMPT" | grep -iqE "(can you add|feature request|would be nice if|I wish|it would help if|please add|we need a)"; then
  {
    printf '\n## [FEATURE] User request — %s  (ID: %s)\n\n' "$TIMESTAMP" "$ENTRY_ID"
    printf '**Area**: `%s`\n' "$CWD"
    printf '**Trigger**: feature-request\n'
    printf '**Priority**: medium\n'
    printf '**Status**: new\n\n'
    printf '### What Was Requested\n'
    printf '%s\n\n' "$PROMPT_SAFE"
    printf '### Metadata\n- **Session**: %s\n- **Promoted**: false\n---\n' "$SESSION_ID"
  } >> "$LEARNINGS_DIR/FEATURE_REQUESTS.md"
  echo "[LOGGED] Feature request → .learnings/FEATURE_REQUESTS.md (ID: $ENTRY_ID)"
  exit 0
fi

# Correction detection (case-insensitive)
if echo "$PROMPT" | grep -iqE "(actually,? (that|no|it|you)|no,? that'?s wrong|I meant|not what I asked|that'?s incorrect|you'?re wrong|wrong approach|don'?t do that)"; then
  {
    printf '\n## [CORRECTION] User correction — %s  (ID: %s)\n\n' "$TIMESTAMP" "$ENTRY_ID"
    printf '**Area**: `%s`\n' "$CWD"
    printf '**Trigger**: correction\n'
    printf '**Priority**: high\n'
    printf '**Status**: new\n\n'
    printf '### What Happened\n'
    printf 'User corrected Claude'\''s approach or output.\n\n'
    printf '### Context\n'
    printf '%s\n\n' "$PROMPT_SAFE"
    printf '### Resolution\n[Apply user'\''s correction and update approach]\n\n'
    printf '### Metadata\n- **Session**: %s\n- **Promoted**: false\n---\n' "$SESSION_ID"
  } >> "$LEARNINGS_DIR/LEARNINGS.md"
  echo "[LOGGED] User correction → .learnings/LEARNINGS.md (ID: $ENTRY_ID)"
fi
```

## Directory Structure

After setup, your project will have:

```
.learnings/
  ERRORS.md           # Tool failures, exceptions, crashes
  LEARNINGS.md        # User corrections, knowledge gaps, discoveries
  FEATURE_REQUESTS.md # User-requested features and enhancements
  PATTERNS.md         # Promoted recurring patterns (bridge-generated)
.claude/
  hooks/
    on-error.sh       # PostToolUseFailure hook script
    on-correction.sh  # UserPromptSubmit hook script
```

## Error Handling

If `jq` is not installed, the hooks will fail silently (due to `set -euo pipefail`). Install it first:

```bash
# macOS
brew install jq

# Ubuntu/Debian
sudo apt install jq

# Windows (via Chocolatey)
choco install jq
```

If the bridge is unreachable (bridge mode only):

> Bridge server is not responding. Local hooks are still active — errors and corrections continue to be captured in `.learnings/`. For deep analysis, start the bridge with:
> `./scripts/openclaw/quickstart.sh` (Linux/macOS) or `.\scripts\openclaw\quickstart.ps1` (Windows)

Local hooks have no external dependencies beyond `jq` and never fail silently.
