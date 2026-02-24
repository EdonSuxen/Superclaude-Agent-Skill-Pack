---
name: superclaude-self-improving
version: 1.0.0
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

**Setup** — add to `.claude/settings.json`:

```json
{
  "hooks": {
    "PostToolUse": [
      {
        "matcher": "Bash",
        "hooks": [
          {
            "type": "command",
            "command": "bash .claude/hooks/on-error.sh"
          }
        ]
      }
    ],
    "UserPromptSubmit": [
      {
        "hooks": [
          {
            "type": "command",
            "command": "bash .claude/hooks/on-correction.sh \"$PROMPT\""
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
| Tool failure (exit code != 0) | PostToolUse hook | `.learnings/ERRORS.md` |
| User correction phrase | UserPromptSubmit hook | `.learnings/LEARNINGS.md` |
| Recurring pattern (3+ times) | Session review | `.learnings/PATTERNS.md` → `CLAUDE.md` |

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

## Learning Log Format

Each entry follows this structure:

```markdown
## [SEVERITY] Summary — YYYY-MM-DD HH:MM

**Area**: `[file-path or domain]`
**Trigger**: error | correction | discovery | capability-gap
**Priority**: critical | high | medium | low

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

Learnings that appear **3 or more times** across different sessions or tasks are promoted:

1. **Pattern identified** — semantic similarity > 0.7 with 3+ existing entries
2. **Promotion candidate** — entry moved to `.learnings/PATTERNS.md` with merged context
3. **Project memory** — pattern appended to `CLAUDE.md` under a `## Learned Patterns` section
4. **Source entries** — marked `Promoted: true` with link to pattern

## Output Structure

### Local Mode (Hook Output)
```
[LOGGED] Tool failure captured → .learnings/ERRORS.md
  Summary: npm install failed — missing peer dependency react@^18
  Area: package.json
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
- ⚠️ Scope creep detected: last 3 sessions expanded beyond initial task
- ⚠️ Approach monotony: same debugging strategy used 5x without improvement

## Promotion Candidates
1. "Always run `npm ls` before `npm install` in monorepos" → promote to CLAUDE.md
2. "Vitest mocks require `vi.resetAllMocks()` in afterEach" → promote to CLAUDE.md

## TBKCC Dimensions
- Truth: 0.82 (evidence-based corrections logged)
- Beauty: 0.75 (code elegance improvements tracked)
- Knowledge: 0.88 (5 new patterns this session)
- Creation: 0.71 (3 novel approaches discovered)
- Curiosity: 0.79 (2 exploration suggestions generated)
```

## Examples

**Example 1 — Automatic error capture (local hooks):**

A bash command fails during `npm install`. The PostToolUse hook fires, detects exit code 1, extracts the error message, and appends a structured entry to `.learnings/ERRORS.md` with the command, error output, and timestamp. No manual action needed.

**Example 2 — User correction capture:**

**User:** Actually, that's wrong — we use pnpm here, not npm.

The UserPromptSubmit hook detects "Actually, that's wrong" as a correction marker. It logs to `.learnings/LEARNINGS.md`: the user's correction, the context (Claude suggested npm), and the resolution (use pnpm). On the 3rd occurrence of "use pnpm not npm", it promotes to CLAUDE.md.

**Example 3 — Deep analysis via bridge:**

**User:** Analyze my learnings from this week. What patterns am I repeating?

The bridge runs the self-improvement-enhanced engine. It finds 12 entries in `.learnings/`, clusters them into 3 semantic groups, identifies 2 patterns above the promotion threshold, flags 1 anti-pattern (repeated same debugging approach), and generates a report with specific CLAUDE.md additions.

## Hook Scripts

### `.claude/hooks/on-error.sh`

```bash
#!/bin/bash
# PostToolUse hook — captures tool failures
# Reads: $TOOL_NAME, $EXIT_CODE, $TOOL_OUTPUT (from stdin)

EXIT_CODE="${TOOL_EXIT_CODE:-0}"
[ "$EXIT_CODE" -eq 0 ] && exit 0

LEARNINGS_DIR=".learnings"
mkdir -p "$LEARNINGS_DIR"

TIMESTAMP=$(date '+%Y-%m-%d %H:%M')
TOOL="${TOOL_NAME:-unknown}"
OUTPUT=$(cat /dev/stdin 2>/dev/null | head -50)

cat >> "$LEARNINGS_DIR/ERRORS.md" << EOF

## [ERROR] ${TOOL} failed (exit ${EXIT_CODE}) — ${TIMESTAMP}

**Area**: \`${PWD}\`
**Trigger**: error
**Priority**: medium

### What Happened
Tool \`${TOOL}\` exited with code ${EXIT_CODE}.

### Context
\`\`\`
${OUTPUT}
\`\`\`

### Resolution
[Pending — to be filled when resolved]

### Metadata
- **Promoted**: false
---
EOF

echo "[LOGGED] Tool failure → .learnings/ERRORS.md"
```

### `.claude/hooks/on-correction.sh`

```bash
#!/bin/bash
# UserPromptSubmit hook — captures user corrections

PROMPT="$1"

# Correction markers (case-insensitive)
if echo "$PROMPT" | grep -iqE "(actually|no,? that'?s wrong|I meant|not what I asked|that'?s incorrect|you'?re wrong|wrong approach|don'?t do that)"; then
  LEARNINGS_DIR=".learnings"
  mkdir -p "$LEARNINGS_DIR"

  TIMESTAMP=$(date '+%Y-%m-%d %H:%M')

  cat >> "$LEARNINGS_DIR/LEARNINGS.md" << EOF

## [CORRECTION] User correction — ${TIMESTAMP}

**Area**: \`${PWD}\`
**Trigger**: correction
**Priority**: high

### What Happened
User corrected Claude's approach or output.

### Context
User said: "${PROMPT}"

### Resolution
[Apply user's correction and update approach]

### Metadata
- **Promoted**: false
---
EOF

  echo "[LOGGED] User correction → .learnings/LEARNINGS.md"
fi
```

## Directory Structure

After setup, your project will have:

```
.learnings/
  ERRORS.md        # Tool failures, exceptions, crashes
  LEARNINGS.md     # User corrections, knowledge gaps, discoveries
  PATTERNS.md      # Promoted recurring patterns (auto-generated)
.claude/
  hooks/
    on-error.sh    # PostToolUse hook script
    on-correction.sh  # UserPromptSubmit hook script
```

## Error Handling

If the bridge is unreachable (bridge mode only):

> Bridge server is not responding. Local hooks are still active — errors and corrections continue to be captured in `.learnings/`. For deep analysis, start the bridge with:
> `./scripts/openclaw/quickstart.sh` (Linux/macOS) or `.\scripts\openclaw\quickstart.ps1` (Windows)

Local hooks have no external dependencies and never fail silently.
