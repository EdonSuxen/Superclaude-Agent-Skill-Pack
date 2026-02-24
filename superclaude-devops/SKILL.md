---
name: superclaude-devops
version: 1.0.0
---

# SuperClaude DevOps — Pipeline Automation & Platform Engineering

Two specialists cover the full DevOps lifecycle. `devops-engineer` builds and optimizes CI/CD pipelines — GitLab CI, GitHub Actions, Docker multi-stage builds, Kubernetes manifests, and GitOps workflows. `platform-engineer` focuses on the developer experience layer — internal developer portals, golden path templates, self-service infrastructure, and DORA metrics tracking. Together they produce pipelines that are fast, reliable, and pleasant to use.

## When to Activate

Activate this skill when the user:

- Needs to set up or optimize a CI/CD pipeline (GitLab CI, GitHub Actions, Jenkins)
- Wants to containerize an application (Dockerfile, docker-compose, multi-stage builds)
- Is planning a deployment strategy (blue-green, canary, rolling updates)
- Needs an internal developer platform or golden path templates
- Uses phrases like "set up CI/CD", "deployment pipeline", "Docker setup", "improve DX"
- Wants to implement GitOps or infrastructure-as-code workflows

Do not activate for: Kubernetes cluster architecture (use `superclaude-cloud-infra`) or security scanning in pipelines (use `superclaude-compliance`).

## Agents in This Wave

| Agent | Role | Focus |
|-------|------|-------|
| `devops-engineer` | Lead | Pipeline automation, Docker, K8s manifests, GitOps, deployment strategies |
| `platform-engineer` | Specialist | Developer portals, golden paths, self-service tooling, DORA metrics |

Wave strategy: progressive | Synthesis: lead_agent | Model: Opus

## How to Call the Bridge

```
POST ${SUPERCLAUDE_BRIDGE_URL}/hooks/agent
Authorization: Bearer ${SUPERCLAUDE_BRIDGE_TOKEN}
Content-Type: application/json

{
  "message": "<the user's request, unmodified>",
  "agentId": "devops",
  "model": "opus",
  "thinking": "high",
  "deliver": true
}
```

## Output Structure

```
# DevOps Report

## Pipeline Design — devops-engineer
### Pipeline Configuration
### Container Strategy
### Deployment Strategy
### Rollback Plan

## Developer Experience — platform-engineer
### Golden Path Template
### Self-Service Capabilities
### DORA Metrics Baseline

## Recommended Next Steps
1. [Immediate actions]
2. [Optimization opportunities]
```

## Examples

**Example 1 — CI/CD for a monorepo:**

**User:** Set up GitLab CI for our TypeScript monorepo with 4 packages.

**Response:** `devops-engineer` creates a `.gitlab-ci.yml` with Turbo-aware caching, per-package test stages, Docker build with layer caching, and deploy-on-tag strategy. `platform-engineer` adds a project template so new packages inherit the pipeline automatically.

**Example 2 — Deployment strategy:**

**User:** We need zero-downtime deployments for our Node.js API on Kubernetes.

**Response:** `devops-engineer` designs a rolling update strategy with readiness probes, pre-stop hooks for graceful shutdown, and HPA for load-based scaling. `platform-engineer` creates a deployment dashboard showing DORA metrics and rollback triggers.

## Error Handling

If the bridge is unreachable:

> Bridge server is not responding. Start it with:
> `./scripts/openclaw/quickstart.sh` (Linux/macOS) or `.\scripts\openclaw\quickstart.ps1` (Windows)

If one specialist fails, findings from the other are presented with a note about the incomplete analysis.
