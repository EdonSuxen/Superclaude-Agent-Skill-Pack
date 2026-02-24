---
name: superclaude-accessibility
version: 1.0.0
---

# SuperClaude Accessibility — WCAG 2.2 Compliance & Inclusive Design

Two specialists provide comprehensive accessibility coverage. `digital-experience-designer` evaluates the user experience through an inclusive design lens — interaction patterns, cognitive load, navigation flow, and touch target sizing using Nielsen-Norman methodology. `accessibility-champion` runs technical WCAG 2.2 AA compliance checks — contrast ratios, ARIA attributes, keyboard navigation, screen reader compatibility, and automated Playwright audits. Together they catch both the UX issues humans notice and the technical violations automated tools detect.

## When to Activate

Activate this skill when the user:

- Needs a WCAG compliance audit for a website or application
- Wants to improve accessibility of existing components or pages
- Is preparing for accessibility certification or legal compliance
- Needs screen reader compatibility testing or ARIA attribute guidance
- Uses phrases like "accessibility audit", "WCAG compliance", "screen reader support", "make this accessible"
- Has received accessibility complaints or failed automated a11y checks

Do not activate for: general UX redesign without accessibility focus (use `superclaude-design`) or frontend architecture decisions (use `superclaude-frontend-architecture-specialist`).

## Agents in This Wave

| Agent | Role | Focus |
|-------|------|-------|
| `digital-experience-designer` | Lead | UX evaluation, inclusive design, interaction patterns, cognitive accessibility |
| `accessibility-champion` | Specialist | WCAG 2.2 AA technical compliance, ARIA, keyboard nav, Playwright automation |

Wave strategy: systematic | Synthesis: consensus | Model: Sonnet

## How to Call the Bridge

```
POST ${SUPERCLAUDE_BRIDGE_URL}/hooks/agent
Authorization: Bearer ${SUPERCLAUDE_BRIDGE_TOKEN}
Content-Type: application/json

{
  "message": "<the user's request, unmodified>",
  "agentId": "accessibility",
  "model": "sonnet",
  "thinking": "medium",
  "deliver": true
}
```

## Output Structure

```
# Accessibility Audit Report

## UX & Inclusive Design — digital-experience-designer
### Interaction Pattern Issues
### Cognitive Load Assessment
### Navigation Flow Analysis

## WCAG 2.2 Compliance — accessibility-champion
### Level A Violations (critical)
### Level AA Violations (required)
### Automated Test Results (Playwright/axe-core)

## Prioritized Remediation Plan
1. [Critical: keyboard trap in modal — fix with focus management]
2. [High: contrast ratio 3.2:1 on buttons — needs 4.5:1]
3. ...
```

## Examples

**Example 1 — Pre-launch accessibility audit:**

**User:** Audit our checkout flow for WCAG 2.2 AA compliance before launch.

**Response:** `digital-experience-designer` identifies cognitive overload in the 7-step checkout and recommends progressive disclosure. `accessibility-champion` finds 12 WCAG violations: 3 missing form labels, 4 insufficient contrast ratios, 2 keyboard traps, and 3 missing ARIA live regions for dynamic price updates.

**Example 2 — Component accessibility:**

**User:** Our dropdown menu doesn't work with screen readers. Help fix it.

**Response:** `accessibility-champion` identifies missing `role="listbox"`, absent `aria-expanded` state, and no keyboard arrow-key navigation. `digital-experience-designer` recommends a combobox pattern over custom dropdown for better assistive technology support.

## Error Handling

If the bridge is unreachable:

> Bridge server is not responding. Start it with:
> `./scripts/openclaw/quickstart.sh` (Linux/macOS) or `.\scripts\openclaw\quickstart.ps1` (Windows)

If one specialist fails, findings from the other are presented with a note about the incomplete analysis.
