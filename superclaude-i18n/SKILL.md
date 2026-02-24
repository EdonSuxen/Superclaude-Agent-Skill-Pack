---
name: superclaude-i18n
description: Internationalization and localization using the localization-internationalization-expert — i18n/l10n architecture, ICU MessageFormat, CLDR data, RTL layout support, pluralization rules, date/number formatting, and cultural adaptation. Returns i18n implementation plans with locale-specific configurations. Activates on "internationalize this app", "add RTL support", "translation workflow", "locale formatting".
version: 1.0.0
tags: [superclaude, claude-code, internationalization, localization, i18n, l10n, rtl, translation, icu, cldr]
category: developer-tools
metadata:
  openclaw:
    emoji: "🌍"
    os: [darwin, linux, win32]
    requires:
      bins: [node]
      env:
        - SUPERCLAUDE_BRIDGE_URL
        - SUPERCLAUDE_BRIDGE_TOKEN
      primaryEnv: SUPERCLAUDE_BRIDGE_TOKEN
    homepage: https://github.com/EdonSuxen/Superclaude-Agent-Skill-Pack
---

# SuperClaude i18n — Internationalization & Cultural Adaptation

The `localization-internationalization-expert` handles all aspects of making software work globally. This includes i18n architecture (ICU MessageFormat, CLDR locale data, react-intl/next-intl setup), RTL layout support (Arabic, Hebrew, Farsi), pluralization rules across languages, date/time/number/currency formatting, translation workflow design (TMS integration, context for translators), and cultural adaptation (content that respects local norms). The agent produces implementation plans that get i18n right from the start — avoiding costly retrofits.

## When to Activate

Activate this skill when the user:

- Needs to internationalize an existing application
- Is building a new app that must support multiple languages from day one
- Has RTL layout issues or needs bidirectional text support
- Needs a translation workflow (extraction, TMS integration, review process)
- Uses phrases like "internationalize this app", "add RTL support", "translation workflow", "locale formatting"
- Has locale-specific bugs (dates, numbers, plurals rendering incorrectly)

Do not activate for: content writing in specific languages (use `superclaude-scribe`) or general frontend architecture (use `superclaude-frontend-architecture-specialist`).

## How to Call the Bridge

```
POST ${SUPERCLAUDE_BRIDGE_URL}/hooks/agent
Authorization: Bearer ${SUPERCLAUDE_BRIDGE_TOKEN}
Content-Type: application/json

{
  "message": "<the user's request, unmodified>",
  "agentId": "i18n",
  "model": "sonnet",
  "thinking": "medium",
  "deliver": true
}
```

## Output Structure

```
# i18n Implementation Report

## Architecture
### Library Selection & Configuration
### Message Extraction Setup
### Locale Data Strategy

## Implementation
### String Externalization Plan
### RTL Layout Changes (if applicable)
### Date/Number/Currency Formatting
### Pluralization Rules

## Translation Workflow
### TMS Integration
### Context for Translators
### QA Process

## Recommended Next Steps
1. [Priority languages and effort estimate]
2. [Automated i18n linting setup]
```

## Examples

**Example 1 — React app internationalization:**

**User:** Internationalize our React app — we need to support English, Japanese, and Arabic.

**Response:** Recommends react-intl with ICU MessageFormat, designs the message extraction pipeline (FormatJS CLI → JSON catalogs), implements RTL support for Arabic using CSS logical properties and `dir="rtl"`, and configures CLDR-based date/number formatting per locale. Includes pluralization examples for Japanese (no plural forms) vs Arabic (6 plural forms).

**Example 2 — RTL layout debugging:**

**User:** Our Arabic users see overlapping text and mirrored icons. Fix the RTL issues.

**Response:** Identifies 4 categories of RTL bugs: CSS using `left/right` instead of `start/end`, non-mirrored directional icons, `text-align: left` hardcoding, and missing `dir` attribute propagation. Provides a systematic fix plan with CSS logical properties migration and icon audit.

## Error Handling

If the bridge is unreachable:

> Bridge server is not responding. Start it with:
> `./scripts/openclaw/quickstart.sh` (Linux/macOS) or `.\scripts\openclaw\quickstart.ps1` (Windows)
