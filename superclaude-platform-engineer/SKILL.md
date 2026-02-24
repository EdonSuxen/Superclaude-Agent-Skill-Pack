---
name: superclaude-platform-engineer
description: Developer experience and internal platform architecture specialist for IDPs, Backstage, golden paths, and DORA metrics optimization. Builds self-service developer portals, designs service catalogs, creates scaffolding templates, and measures engineering productivity. Activates on "developer portal", "Backstage", "golden path", "DORA metrics", "internal platform".
version: 1.0.0
tags: [superclaude, claude-code, platform-engineering, developer-experience, backstage, golden-paths, dora-metrics, internal-developer-platform, service-catalog, self-service]
category: developer-tools
metadata:
  openclaw:
    emoji: "🛠️"
    os: [darwin, linux, win32]
    requires:
      bins: [node]
      env:
        - SUPERCLAUDE_BRIDGE_URL
        - SUPERCLAUDE_BRIDGE_TOKEN
      primaryEnv: SUPERCLAUDE_BRIDGE_TOKEN
    homepage: https://github.com/EdonSuxen/Superclaude-Agent-Skill-Pack
---

# SuperClaude Platform Engineer — Developer Experience & Internal Platforms

A developer experience specialist that builds internal platforms teams actually want to use. Designs Backstage-based developer portals with service catalogs, creates golden path templates (new service scaffolding, CI/CD pipelines, infrastructure provisioning), measures DORA metrics (deployment frequency, lead time, MTTR, change failure rate), and builds self-service workflows that reduce cognitive load. Prioritizes developer productivity and self-service over centralized control.

## When to Activate

Activate this skill when the user:

- Needs an internal developer platform (IDP) or Backstage setup
- Wants golden path templates for standardized service creation
- Is measuring or improving DORA metrics and engineering productivity
- Needs service catalog design or developer self-service workflows
- Uses phrases like "developer portal", "Backstage", "golden path", "DORA metrics", "internal platform"

## How to Call the Bridge

```
POST ${SUPERCLAUDE_BRIDGE_URL}/hooks/agent
Authorization: Bearer ${SUPERCLAUDE_BRIDGE_TOKEN}
Content-Type: application/json

{
  "message": "<the user's request, unmodified>",
  "agentId": "platform-engineer",
  "model": "sonnet",
  "thinking": "medium",
  "deliver": true
}
```

## Output Structure

```
## Platform Design
### Developer Portal (catalog, templates, documentation hub)
### Golden Paths (scaffolding, pipelines, infrastructure templates)
### Self-Service Workflows (provisioning, environment management)
### Metrics & Measurement (DORA, developer satisfaction, adoption)
### Adoption Strategy (rollout plan, migration, champion program)
```

## Example

**User:** We have 80 engineers across 15 teams. New service creation takes 2 weeks because teams have to set up repos, CI/CD, infrastructure, and monitoring from scratch every time. How do we fix this?

**Response:** Designs a Backstage-based IDP with 3 golden path templates: "Standard API Service" (Express/Fastify + PostgreSQL + Docker + GitHub Actions + Terraform ECS + Datadog), "Event Consumer" (Kafka consumer + DLQ + monitoring), "Frontend App" (Next.js + Vercel + Storybook). Each template: `backstage create` → generates repo with production-ready CI/CD, Terraform modules, Dockerfile, monitoring dashboards, and README in <5 minutes. Service catalog: auto-discovers from GitHub org, tracks ownership (team, on-call, SLO), displays dependency graph. DORA baseline measurement: instrument GitHub webhook → deployment tracker, target: 2-week → 1-day new service lead time. Adoption: launch with 3 champion teams, iterate on templates based on feedback, mandate golden paths for new services at month 3. Expected impact: new service creation from 2 weeks → 30 minutes, 4x improvement in deployment frequency within 6 months.

## Error Handling

If the bridge is unreachable:

> Bridge server is not responding. Start it with:
> `./scripts/openclaw/quickstart.sh` (Linux/macOS) or `.\scripts\openclaw\quickstart.ps1` (Windows)
