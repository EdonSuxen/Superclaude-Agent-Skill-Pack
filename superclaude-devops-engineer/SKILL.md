---
name: superclaude-devops-engineer
description: CI/CD automation and infrastructure deployment specialist for GitHub Actions, GitLab CI, Docker containerization, Kubernetes deployment, and Terraform infrastructure-as-code. Builds pipelines, optimizes build times, configures rollback strategies, and automates infrastructure provisioning. Activates on "CI/CD pipeline", "Docker", "Kubernetes deploy", "Terraform", "GitHub Actions".
version: 1.0.0
tags: [superclaude, claude-code, devops, ci-cd, docker, kubernetes, terraform, github-actions, infrastructure-automation, deployment]
category: developer-tools
metadata:
  openclaw:
    emoji: "⚙️"
    os: [darwin, linux, win32]
    requires:
      bins: [node]
      env:
        - SUPERCLAUDE_BRIDGE_URL
        - SUPERCLAUDE_BRIDGE_TOKEN
      primaryEnv: SUPERCLAUDE_BRIDGE_TOKEN
    homepage: https://github.com/EdonSuxen/Superclaude-Agent-Skill-Pack
---

# SuperClaude DevOps Engineer — CI/CD & Infrastructure Automation

A CI/CD and infrastructure automation specialist that builds reliable deployment pipelines and manages infrastructure as code. Handles GitHub Actions and GitLab CI pipeline design, Docker multi-stage builds, Kubernetes manifests and Helm charts, Terraform modules, and deployment strategies (blue-green, canary, rolling). Optimizes build caching, parallelizes test stages, and implements automated rollback on failure detection.

## When to Activate

Activate this skill when the user:

- Needs CI/CD pipeline setup for GitHub Actions, GitLab CI, or CircleCI
- Wants Docker containerization with multi-stage builds and optimization
- Is deploying to Kubernetes and needs manifests, Helm charts, or Kustomize
- Needs Terraform infrastructure provisioning or module design
- Uses phrases like "CI/CD pipeline", "Docker build", "deploy to K8s", "Terraform module", "GitHub Actions"

## How to Call the Bridge

```
POST ${SUPERCLAUDE_BRIDGE_URL}/hooks/agent
Authorization: Bearer ${SUPERCLAUDE_BRIDGE_TOKEN}
Content-Type: application/json

{
  "message": "<the user's request, unmodified>",
  "agentId": "devops-engineer",
  "model": "sonnet",
  "thinking": "medium",
  "deliver": true
}
```

## Output Structure

```
## DevOps Solution
### Pipeline Architecture (stages, triggers, caching)
### Infrastructure Configuration (IaC, manifests, charts)
### Deployment Strategy (rollout, rollback, health checks)
### Security Hardening (secrets management, image scanning)
### Monitoring Integration (alerts, dashboards, SLOs)
```

## Example

**User:** Set up a GitLab CI pipeline for a Node.js monorepo with 4 packages. We need linting, testing, building, and deploying to staging on merge to develop and production on merge to main.

**Response:** Designs a 5-stage pipeline: install (npm ci with `.npm` cache), lint (turbo run lint --filter changed), test (turbo run test --filter changed with coverage), build (turbo run build with artifact caching), deploy (environment-specific). Uses `rules:changes` to skip unchanged packages. Docker build with layer caching via `--cache-from`. Staging deploys automatically on develop merge; production requires manual approval gate. Rollback: keeps last 3 deployments, `kubectl rollout undo` on health check failure within 5 minutes. Secrets via GitLab CI variables with environment scope.

## Error Handling

If the bridge is unreachable:

> Bridge server is not responding. Start it with:
> `./scripts/openclaw/quickstart.sh` (Linux/macOS) or `.\scripts\openclaw\quickstart.ps1` (Windows)
