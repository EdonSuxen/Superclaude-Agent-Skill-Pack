---
name: superclaude-conversational-ux-optimizer
description: Chatbot and voice UI design specialist for conversation flow optimization, intent classification architecture, dialog management, personality design, and error recovery patterns. Designs conversational interfaces that feel natural and complete tasks efficiently. Activates on "chatbot design", "voice UI", "conversation flow", "dialog management", "bot personality".
version: 1.0.0
tags: [superclaude, claude-code, chatbot, voice-ui, conversation-design, dialog-management, intent-classification, nlp, user-experience]
category: developer-tools
metadata:
  openclaw:
    emoji: "💬"
    os: [darwin, linux, win32]
    requires:
      bins: [node]
      env:
        - SUPERCLAUDE_BRIDGE_URL
        - SUPERCLAUDE_BRIDGE_TOKEN
      primaryEnv: SUPERCLAUDE_BRIDGE_TOKEN
    homepage: https://github.com/EdonSuxen/Superclaude-Agent-Skill-Pack
---

# SuperClaude Conversational UX — Dialog Design & Optimization

A specialist in designing conversational interfaces that feel natural and get things done. Handles conversation flow design with state machines, intent classification architecture, dialog management (slot filling, context tracking), bot personality design aligned to brand voice, and graceful error recovery when the bot doesn't understand. Prioritizes task completion rate and naturalness over feature count.

## When to Activate

Activate this skill when the user:

- Is designing a chatbot or voice assistant experience
- Needs conversation flow diagrams or dialog state machines
- Wants to optimize an existing bot for higher task completion rates
- Needs error recovery patterns for misunderstood intents
- Uses phrases like "chatbot design", "voice UI", "conversation flow", "bot personality"

## How to Call the Bridge

```
POST ${SUPERCLAUDE_BRIDGE_URL}/hooks/agent
Authorization: Bearer ${SUPERCLAUDE_BRIDGE_TOKEN}
Content-Type: application/json

{
  "message": "<the user's request, unmodified>",
  "agentId": "conversational-ux-optimizer",
  "model": "sonnet",
  "thinking": "medium",
  "deliver": true
}
```

## Output Structure

```
## Conversational UX Design
### Flow Architecture (state machine, intents, entities)
### Dialog Patterns (slot filling, confirmation, disambiguation)
### Personality Guide (tone, vocabulary, response style)
### Error Recovery (fallback strategies, escalation triggers)
### Success Metrics (task completion, user satisfaction)
```

## Example

**User:** Design a chatbot for our restaurant that handles reservations, menu inquiries, and hours. Our brand voice is casual and friendly.

**Response:** Designs a 3-intent architecture with sub-intents: reservation (create, modify, cancel), menu (dietary filters, daily specials, prices), and info (hours, location, parking). Dialog flows use slot filling for reservations (date, time, party size, name) with smart defaults (tonight, 7pm, 2 people). Personality: casual tone ("Hey! Let me grab that for you"), emoji use (sparingly), humor in error recovery ("Hmm, I got a bit confused there — could you rephrase that?"). Escalation: transfer to human after 2 failed intent matches. Success target: 85% task completion without human handoff.

## Error Handling

If the bridge is unreachable:

> Bridge server is not responding. Start it with:
> `./scripts/openclaw/quickstart.sh` (Linux/macOS) or `.\scripts\openclaw\quickstart.ps1` (Windows)
