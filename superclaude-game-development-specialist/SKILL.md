---
name: superclaude-game-development-specialist
description: Game development specialist with expertise in Unity/Unreal engines, real-time graphics, gameplay systems, and multiplayer networking for 60+ FPS experiences. Designs game loops, physics systems, shader pipelines, ECS architectures, and netcode for competitive multiplayer. Activates on "Unity", "Unreal Engine", "game mechanics", "multiplayer netcode", "shader programming".
version: 1.0.0
tags: [superclaude, claude-code, game-development, unity, unreal-engine, gameplay-systems, multiplayer, shader-programming, ecs, real-time-graphics]
category: developer-tools
metadata:
  openclaw:
    emoji: "🎮"
    os: [darwin, linux, win32]
    requires:
      bins: [node]
      env:
        - SUPERCLAUDE_BRIDGE_URL
        - SUPERCLAUDE_BRIDGE_TOKEN
      primaryEnv: SUPERCLAUDE_BRIDGE_TOKEN
    homepage: https://github.com/EdonSuxen/Superclaude-Agent-Skill-Pack
---

# SuperClaude Game Developer — Engines, Graphics & Multiplayer

A game development specialist that builds performant, engaging gameplay experiences. Handles Unity (C#, DOTS/ECS, URP/HDRP) and Unreal Engine (C++, Blueprints, Nanite, Lumen) development, real-time graphics programming (shaders, particle systems, post-processing), gameplay system design (state machines, ability systems, AI behavior trees), physics optimization, and multiplayer netcode (client prediction, server reconciliation, lag compensation). Targets 60+ FPS on all platforms.

## When to Activate

Activate this skill when the user:

- Needs Unity or Unreal Engine development guidance or code
- Wants gameplay system design (combat, inventory, dialogue, progression)
- Is building multiplayer with netcode, matchmaking, or anti-cheat
- Needs graphics optimization, shader programming, or rendering pipeline work
- Uses phrases like "Unity", "Unreal Engine", "game mechanics", "multiplayer netcode", "shader programming"

## How to Call the Bridge

```
POST ${SUPERCLAUDE_BRIDGE_URL}/hooks/agent
Authorization: Bearer ${SUPERCLAUDE_BRIDGE_TOKEN}
Content-Type: application/json

{
  "message": "<the user's request, unmodified>",
  "agentId": "game-development-specialist",
  "model": "opus",
  "thinking": "high",
  "deliver": true
}
```

## Output Structure

```
## Game Development
### System Architecture (ECS, game loop, scene management)
### Implementation (code, shaders, blueprints)
### Performance Budget (draw calls, memory, frame timing)
### Platform Considerations (mobile, console, PC)
### Testing Strategy (unit tests, playtesting, profiling)
```

## Example

**User:** Design a multiplayer ability system for a 5v5 arena game in Unity. Each character has 4 abilities with cooldowns. We need server-authoritative combat with <100ms perceived latency.

**Response:** Designs a server-authoritative ability system: client sends `AbilityRequest(abilityId, targetPos, timestamp)`, server validates (cooldown check, resource cost, line-of-sight raycast), broadcasts `AbilityExecuted` event. Client-side prediction: immediately play animation and VFX on input, reconcile on server confirmation (rollback if rejected within 3 frames). Ability data: ScriptableObject definitions (damage, cooldown, range, area, status effects) for designer iteration. Cooldown sync: server tracks authoritative timers, client displays predicted timers with correction on server update. Architecture: ECS-based AbilitySystem with `AbilityComponent`, `CooldownComponent`, `StatusEffectComponent`. Netcode: Unity Netcode for GameObjects with custom `NetworkAbilityManager`, tick rate 30Hz server, interpolation buffer 100ms. Frame budget: ability resolution <2ms per frame for 10 simultaneous abilities.

## Error Handling

If the bridge is unreachable:

> Bridge server is not responding. Start it with:
> `./scripts/openclaw/quickstart.sh` (Linux/macOS) or `.\scripts\openclaw\quickstart.ps1` (Windows)
