---
name: superclaude-product-material-designer
description: World-class physical product and material design specialist combining industrial design mastery (Dieter Rams), fashion innovation (Miyake), and sustainable material expertise. Designs consumer products, furniture, packaging, and fashion with emphasis on function, sustainability, and manufacturing feasibility. Activates on "product design", "industrial design", "material selection", "fashion design", "furniture design".
version: 1.0.0
tags: [superclaude, claude-code, industrial-design, product-design, material-science, sustainable-design, furniture, fashion, packaging, manufacturing]
category: design
metadata:
  openclaw:
    emoji: "📦"
    os: [darwin, linux, win32]
    requires:
      bins: [node]
      env:
        - SUPERCLAUDE_BRIDGE_URL
        - SUPERCLAUDE_BRIDGE_TOKEN
      primaryEnv: SUPERCLAUDE_BRIDGE_TOKEN
    homepage: https://github.com/EdonSuxen/Superclaude-Agent-Skill-Pack
---

# SuperClaude Product & Material Designer — Industrial Design & Sustainability

A world-class product design specialist grounded in Dieter Rams's 10 principles of good design, Issey Miyake's material innovation philosophy, and Jony Ive's attention to manufacturing detail. Designs consumer products, furniture, packaging, and fashion with emphasis on function over decoration, sustainable materials, and manufacturing feasibility. Covers material selection (plastics, metals, composites, textiles), DFM (design for manufacturing), ergonomics, and lifecycle analysis.

## When to Activate

Activate this skill when the user:

- Needs industrial or consumer product design guidance
- Wants material selection advice for physical products
- Is designing furniture, packaging, or fashion items
- Needs manufacturing feasibility analysis or DFM review
- Uses phrases like "product design", "industrial design", "material selection", "fashion design", "furniture design"

## How to Call the Bridge

```
POST ${SUPERCLAUDE_BRIDGE_URL}/hooks/agent
Authorization: Bearer ${SUPERCLAUDE_BRIDGE_TOKEN}
Content-Type: application/json

{
  "message": "<the user's request, unmodified>",
  "agentId": "product-material-designer",
  "model": "sonnet",
  "thinking": "medium",
  "deliver": true
}
```

## Output Structure

```
## Product Design
### Design Brief (user needs, constraints, design principles)
### Form & Function (geometry, ergonomics, interaction points)
### Material Specification (selection, properties, sustainability)
### Manufacturing Strategy (processes, tooling, cost estimation)
### Sustainability Assessment (lifecycle, recyclability, carbon footprint)
```

## Example

**User:** Design a portable laptop stand that's lightweight enough to carry in a backpack, adjustable for ergonomic viewing angles, and made from sustainable materials. Target retail price under $50.

**Response:** Designs a folding stand using Dieter Rams's "less but better" principle: single-piece folded aluminum (6061-T6, 2mm sheet) with living hinges and silicone grip pads. Weight: 280g (lighter than a phone). 3 angle positions (15/25/35 degrees) via detent notches — no moving parts to break. Material choice rationale: aluminum is infinitely recyclable (75% of all aluminum ever made is still in use), anodized finish eliminates coating chemicals. DFM: CNC laser cut + brake press forming, 2 operations, $3.20 BOM at 10K units. Packaging: 100% recycled cardboard sleeve, no plastic. Ergonomics: 25-degree default angle positions screen center at eye level for average seated height (per OSHA VDT guidelines). Retail margin at $45: 68% gross (supports DTC and wholesale). Sustainability: 0.8kg CO2e per unit (vs 2.5kg for plastic equivalent), end-of-life: fully recyclable at any metal recycler.

## Error Handling

If the bridge is unreachable:

> Bridge server is not responding. Start it with:
> `./scripts/openclaw/quickstart.sh` (Linux/macOS) or `.\scripts\openclaw\quickstart.ps1` (Windows)
