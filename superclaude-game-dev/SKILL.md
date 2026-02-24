---
name: superclaude-game-dev
version: 1.0.0
---

# SuperClaude Game Dev — Engine Architecture & Animation Design

Two specialists collaborate on game development from both the systems and creative sides. `game-development-specialist` handles engine architecture — Unity/Unreal project structure, gameplay systems (ECS, state machines), physics simulation, multiplayer networking (client prediction, lag compensation), and 60+ FPS performance optimization. `motion-media-specialist` brings animation expertise — character animation using Disney's 12 principles, particle systems, procedural animation, sound design integration, and VFX pipelines. Together they produce games that play well and look great.

## When to Activate

Activate this skill when the user:

- Is building a game and needs architecture or system design guidance
- Wants to implement gameplay mechanics (inventory, combat, dialogue, AI)
- Needs multiplayer networking setup (authoritative server, client prediction)
- Has performance issues (frame drops, memory leaks, draw call batching)
- Uses phrases like "game mechanic", "Unity setup", "multiplayer networking", "game performance"
- Needs animation pipeline setup or character animation guidance

Do not activate for: non-game animation/motion design (use `superclaude-creative`) or VR/AR without game context (use `superclaude-motion-media-specialist`).

## Agents in This Wave

| Agent | Role | Focus |
|-------|------|-------|
| `game-development-specialist` | Lead | Engine architecture, gameplay systems, physics, multiplayer, performance |
| `motion-media-specialist` | Specialist | Character animation, particles, VFX, sound design, Disney principles |

Wave strategy: progressive | Synthesis: lead_agent | Model: Opus

## How to Call the Bridge

```
POST ${SUPERCLAUDE_BRIDGE_URL}/hooks/agent
Authorization: Bearer ${SUPERCLAUDE_BRIDGE_TOKEN}
Content-Type: application/json

{
  "message": "<the user's request, unmodified>",
  "agentId": "game-dev",
  "model": "opus",
  "thinking": "high",
  "deliver": true
}
```

## Output Structure

```
# Game Development Report

## Systems Architecture — game-development-specialist
### Project Structure
### Gameplay System Design
### Performance Budget
### Networking Architecture

## Animation & Visual — motion-media-specialist
### Animation State Machine
### Particle & VFX Design
### Sound Integration Plan

## Recommended Next Steps
1. [Prototype priority features]
2. [Performance benchmarks to hit]
```

## Examples

**Example 1 — Multiplayer roguelike:**

**User:** Design the architecture for a 4-player co-op roguelike with procedural dungeons.

**Response:** `game-development-specialist` designs the authoritative server with client-side prediction, procedural dungeon generator using BSP trees, and ECS-based combat system with deterministic physics. `motion-media-specialist` designs the animation state machine: 8-direction movement blend trees, attack anticipation/follow-through, and hit reaction procedural animation.

**Example 2 — Mobile game performance:**

**User:** Our mobile game drops to 20 FPS when there are 50+ enemies on screen.

**Response:** `game-development-specialist` profiles the bottleneck: 50 individual draw calls, unoptimized physics collision checks, and GC spikes from object instantiation. Recommends GPU instancing, spatial partitioning (quadtree), and object pooling. `motion-media-specialist` redesigns enemy animations with LOD — full skeletal at close range, sprite sheet at distance.

## Error Handling

If the bridge is unreachable:

> Bridge server is not responding. Start it with:
> `./scripts/openclaw/quickstart.sh` (Linux/macOS) or `.\scripts\openclaw\quickstart.ps1` (Windows)

If one specialist fails, findings from the other are presented with a note about the incomplete analysis.
