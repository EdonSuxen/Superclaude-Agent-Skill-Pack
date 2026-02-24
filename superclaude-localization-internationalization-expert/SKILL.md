---
name: superclaude-localization-internationalization-expert
description: Localization and internationalization expert specializing in i18n/l10n architecture, RTL support, cultural adaptation, and global software delivery using ICU/CLDR standards. Designs translation workflows, implements locale-aware formatting (dates, numbers, currencies), configures RTL layouts, and builds pluralization systems. Activates on "internationalization", "localization", "RTL support", "translation workflow", "i18n".
version: 1.0.0
tags: [superclaude, claude-code, internationalization, localization, i18n, l10n, rtl-support, icu-cldr, translation, cultural-adaptation]
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

# SuperClaude i18n Expert — Localization & Global Software

A localization specialist that makes software work naturally in every language and culture. Designs i18n architecture (message extraction, ICU MessageFormat, CLDR data integration), implements RTL layout support (CSS logical properties, bidirectional text), builds translation workflows (TMS integration, context annotations, translator-friendly keys), and handles locale-aware formatting for dates, numbers, currencies, and pluralization rules across 100+ locales.

## When to Activate

Activate this skill when the user:

- Needs i18n architecture for a new or existing application
- Wants to add RTL language support (Arabic, Hebrew, Persian)
- Is setting up translation workflows or TMS integration
- Needs locale-aware date, number, or currency formatting
- Uses phrases like "internationalization", "localization", "RTL support", "translation workflow", "i18n"

## How to Call the Bridge

```
POST ${SUPERCLAUDE_BRIDGE_URL}/hooks/agent
Authorization: Bearer ${SUPERCLAUDE_BRIDGE_TOKEN}
Content-Type: application/json

{
  "message": "<the user's request, unmodified>",
  "agentId": "localization-internationalization-expert",
  "model": "sonnet",
  "thinking": "medium",
  "deliver": true
}
```

## Output Structure

```
## Internationalization Design
### i18n Architecture (extraction, storage, runtime loading)
### Locale Handling (formatting, pluralization, collation)
### RTL Support (layout mirroring, bidirectional text)
### Translation Workflow (TMS, context, quality assurance)
### Testing Strategy (pseudo-localization, locale coverage)
```

## Example

**User:** We have a React app with hardcoded English strings everywhere. We need to support French, German, Japanese, and Arabic. What's the migration plan?

**Response:** Designs a 4-phase migration: Phase 1 (extraction) — use `react-intl` with `formatjs` CLI to extract 500+ strings into ICU MessageFormat JSON files, replace JSX text with `<FormattedMessage>` components, plurals use `{count, plural, one {# item} other {# items}}`. Phase 2 (infrastructure) — configure locale detection (Accept-Language → URL prefix → cookie fallback), lazy-load locale bundles (<20KB per locale), set up Crowdin TMS with GitHub sync. Phase 3 (RTL for Arabic) — switch to CSS logical properties (`margin-inline-start` not `margin-left`), add `dir="rtl"` on `<html>`, test with `[dir=rtl]` CSS selectors for mirrored layouts. Phase 4 (CJK for Japanese) — handle line-break rules (`word-break: keep-all`), date format (`YYYY年MM月DD日`), honorifics in user-facing strings. Testing: pseudo-localization pass (expand strings 30% to catch truncation), visual regression for RTL, automated locale screenshot comparison.

## Error Handling

If the bridge is unreachable:

> Bridge server is not responding. Start it with:
> `./scripts/openclaw/quickstart.sh` (Linux/macOS) or `.\scripts\openclaw\quickstart.ps1` (Windows)
