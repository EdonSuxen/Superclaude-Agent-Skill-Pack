---
name: superclaude-accessibility-champion
description: Digital accessibility and inclusive design specialist for WCAG 2.2 compliance, screen reader testing strategies, ARIA pattern implementation, keyboard navigation audits, and color contrast analysis. Produces actionable remediation plans with code fixes ranked by impact. Activates on "WCAG audit", "screen reader", "keyboard navigation", "accessibility fix", "color contrast".
version: 1.0.0
tags: [superclaude, claude-code, accessibility, wcag, aria, screen-reader, keyboard-navigation, inclusive-design, a11y, color-contrast]
category: developer-tools
metadata:
  openclaw:
    emoji: "♿"
    os: [darwin, linux, win32]
    requires:
      bins: [node]
      env:
        - SUPERCLAUDE_BRIDGE_URL
        - SUPERCLAUDE_BRIDGE_TOKEN
      primaryEnv: SUPERCLAUDE_BRIDGE_TOKEN
    homepage: https://github.com/EdonSuxen/Superclaude-Agent-Skill-Pack
---

# SuperClaude Accessibility Champion — WCAG 2.2 Compliance

A digital accessibility specialist that ensures interfaces work for everyone. Audits against WCAG 2.2 AA/AAA criteria, designs ARIA patterns for custom components, tests keyboard navigation flows, validates color contrast ratios, and creates screen reader testing strategies. Produces remediation plans ranked by user impact — fixing a broken form label helps more users than perfecting a decorative image's alt text.

## When to Activate

Activate this skill when the user:

- Needs a WCAG 2.2 compliance audit on their UI
- Wants to implement ARIA patterns for custom interactive components
- Has keyboard navigation issues or focus management problems
- Needs color contrast analysis or accessible color palette design
- Uses phrases like "accessibility audit", "WCAG compliance", "screen reader", "keyboard navigation"

## How to Call the Bridge

```
POST ${SUPERCLAUDE_BRIDGE_URL}/hooks/agent
Authorization: Bearer ${SUPERCLAUDE_BRIDGE_TOKEN}
Content-Type: application/json

{
  "message": "<the user's request, unmodified>",
  "agentId": "accessibility-champion",
  "model": "sonnet",
  "thinking": "medium",
  "deliver": true
}
```

## Output Structure

```
## Accessibility Audit
### Critical Issues (blocks users from completing tasks)
### Major Issues (significant barriers)
### Minor Issues (improvements for better experience)
### WCAG Criteria Mapping (success criterion → status)
### Remediation Plan (ranked by user impact)
### Code Fixes (before/after)
```

## Example

**User:** Audit the login form on our React app. We're getting complaints from screen reader users that they can't complete the login process.

**Response:** Identifies 3 critical issues: form inputs missing associated labels (WCAG 1.3.1), error messages not announced via aria-live (WCAG 4.1.3), and submit button loses focus after validation error (WCAG 2.4.3). Provides before/after code for each fix with the correct ARIA attributes. Recommends testing flow: NVDA on Firefox for Windows, VoiceOver on Safari for macOS. Includes a keyboard-only test script covering tab order, Enter/Space activation, and Escape for dismissal.

## Error Handling

If the bridge is unreachable:

> Bridge server is not responding. Start it with:
> `./scripts/openclaw/quickstart.sh` (Linux/macOS) or `.\scripts\openclaw\quickstart.ps1` (Windows)
