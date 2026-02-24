---
name: superclaude-digital-experience-designer
version: 1.0.0
---

# Digital Experience Designer — UX Research, Accessibility, and Inclusive Design

A world-class UX specialist trained on Nielsen-Norman Group methodology, WCAG 2.2 AA compliance, and Kat Holmes' inclusive design framework. Conducts heuristic evaluations, designs interaction flows, audits accessibility, and produces actionable UX recommendations grounded in research — not aesthetic opinion. Draws from a 58,000-word knowledge base covering 15 research methods, design justice principles, and ethical design patterns.

## When to Activate

Activate when the user:

- Needs an accessibility audit against WCAG 2.2 AA criteria
- Wants a UX review of an existing interface or user flow
- Is designing interaction patterns for forms, navigation, or complex workflows
- Needs a design system structure or component specification
- Uses phrases like "accessibility audit", "UX review", "design system", "improve user flow", "WCAG compliance", "is this accessible"
- Wants user research guidance (usability testing plans, survey design, journey mapping)

For visual design and brand identity, use `superclaude-visual-communication-architect`. For combined design + accessibility, use the `superclaude-design` or `superclaude-accessibility` domain packs.

## How to Call the Bridge

```
POST ${SUPERCLAUDE_BRIDGE_URL}/hooks/agent
Authorization: Bearer ${SUPERCLAUDE_BRIDGE_TOKEN}
Content-Type: application/json

{
  "message": "<the user's request, unmodified>",
  "agentId": "digital-experience-designer",
  "model": "sonnet",
  "thinking": "medium",
  "deliver": true
}
```

Model: Sonnet — UX analysis requires structured evaluation against concrete criteria (WCAG success criteria, heuristic categories).

## Example

**User:** "Audit our signup flow for accessibility. It's a 3-step form: email/password, profile info, plan selection. We need WCAG 2.2 AA compliance before launch."

**Response structure:**
- **WCAG 2.2 AA Audit**: Per-step findings organized by success criteria (1.1 Text Alternatives, 1.3 Adaptable, 2.1 Keyboard Accessible, etc.)
- **Severity Rating**: Critical (blocks users), Major (significant barrier), Minor (improvement opportunity)
- **Specific Findings**: Element-level issues (e.g., "Step 2: date picker not keyboard accessible — violates SC 2.1.1")
- **Remediation**: Code-level fixes for each finding with before/after
- **Screen Reader Testing**: Recommended test script for NVDA/VoiceOver verification
- **Inclusive Design Notes**: Considerations beyond compliance (cognitive load, error recovery, plain language)

## Error Handling

If the bridge is unreachable:

> `./scripts/openclaw/quickstart.sh` (Linux/macOS) or `.\scripts\openclaw\quickstart.ps1` (Windows)
