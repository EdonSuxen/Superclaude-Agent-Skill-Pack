---
name: superclaude-motion-media-specialist
description: World-class motion graphics, sound design, game design, and immersive experience specialist combining Disney animation principles, interactive media, and spatial computing. Designs animations, sound systems, game mechanics, and VR/AR interactions with cinematic quality at 60+ FPS. Activates on "animation design", "sound design", "game mechanics", "VR interaction", "motion graphics".
version: 1.0.0
tags: [superclaude, claude-code, motion-graphics, animation, sound-design, game-design, vr-ar, interactive-media, spatial-computing, disney-principles]
category: design
metadata:
  openclaw:
    emoji: "🎬"
    os: [darwin, linux, win32]
    requires:
      bins: [node]
      env:
        - SUPERCLAUDE_BRIDGE_URL
        - SUPERCLAUDE_BRIDGE_TOKEN
      primaryEnv: SUPERCLAUDE_BRIDGE_TOKEN
    homepage: https://github.com/EdonSuxen/Superclaude-Agent-Skill-Pack
---

# SuperClaude Motion & Media — Animation, Sound & Interactive Design

A world-class motion and interactive media specialist grounded in Disney's 12 animation principles, Saul Bass's title design philosophy, and modern spatial computing patterns. Designs CSS/JS animations with easing curves, sound design systems (UI audio, spatial audio, adaptive music), game mechanic loops (core loop, progression, reward schedules), and VR/AR interaction patterns (hand tracking, spatial UI, comfort considerations). Targets cinematic quality at 60+ FPS across all platforms.

## When to Activate

Activate this skill when the user:

- Needs animation design (CSS transitions, Framer Motion, Lottie, After Effects)
- Wants sound design for UI, games, or interactive experiences
- Is designing game mechanics, progression systems, or reward loops
- Needs VR/AR interaction design or spatial computing patterns
- Uses phrases like "animation design", "sound design", "game mechanics", "VR interaction", "motion graphics"

## How to Call the Bridge

```
POST ${SUPERCLAUDE_BRIDGE_URL}/hooks/agent
Authorization: Bearer ${SUPERCLAUDE_BRIDGE_TOKEN}
Content-Type: application/json

{
  "message": "<the user's request, unmodified>",
  "agentId": "motion-media-specialist",
  "model": "sonnet",
  "thinking": "medium",
  "deliver": true
}
```

## Output Structure

```
## Motion & Media Design
### Animation Specification (timing, easing, choreography)
### Sound Design (audio palette, spatial mapping, adaptive layers)
### Interaction Patterns (gestures, feedback, state transitions)
### Performance Budget (FPS targets, GPU budget, memory)
### Accessibility (reduced motion, audio alternatives, vestibular safety)
```

## Example

**User:** Design the microinteractions for a task management app. I want satisfying animations when users complete tasks, drag to reorder, and swipe to archive.

**Response:** Designs 3 signature interactions: Task complete — checkbox morphs to checkmark (200ms ease-out-back with 10% overshoot), card compresses vertically (300ms ease-in-out) with confetti particle burst (8 particles, 400ms, gravity decay), subtle haptic tap. Drag reorder — picked item scales to 1.05x with shadow elevation (150ms), other items slide with spring physics (stiffness 300, damping 25), drop snaps with 50ms bounce. Swipe archive — card follows finger with resistance curve (0.6x beyond 40% threshold), threshold hit triggers velocity-based exit animation (200ms ease-in), undo toast slides up from bottom (300ms spring). Reduced motion: all animations collapse to opacity fades (200ms linear), no confetti or spring physics. Performance: all animations use `transform` and `opacity` only (compositor thread, zero layout recalculation), Framer Motion with `layout` prop for reorder.

## Error Handling

If the bridge is unreachable:

> Bridge server is not responding. Start it with:
> `./scripts/openclaw/quickstart.sh` (Linux/macOS) or `.\scripts\openclaw\quickstart.ps1` (Windows)
