---
name: superclaude-cloud-infra
description: Cloud infrastructure and Kubernetes engineering using two specialists — cloud-native-architect (K8s cluster design, service mesh, multi-cloud strategy, container orchestration) and devops-engineer (Terraform/IaC, deployment automation, monitoring integration). Returns infrastructure designs, K8s manifests, and migration plans. Activates on "Kubernetes setup", "cloud architecture", "migrate to cloud", "service mesh".
version: 1.0.0
tags: [superclaude, claude-code, kubernetes, cloud-native, terraform, aws, gcp, azure, service-mesh, infrastructure-as-code]
category: cloud
metadata:
  openclaw:
    emoji: "☁️"
    os: [darwin, linux, win32]
    requires:
      bins: [node]
      env:
        - SUPERCLAUDE_BRIDGE_URL
        - SUPERCLAUDE_BRIDGE_TOKEN
      primaryEnv: SUPERCLAUDE_BRIDGE_TOKEN
    homepage: https://github.com/EdonSuxen/Superclaude-Agent-Skill-Pack
---

# SuperClaude Cloud Infrastructure — Kubernetes & Cloud-Native Architecture

Two specialists handle cloud infrastructure from design through deployment. `cloud-native-architect` designs Kubernetes clusters, service mesh topology, multi-cloud strategies, and container orchestration patterns — choosing between EKS/GKE/AKS, configuring Istio/Linkerd, and planning cloud migrations. `devops-engineer` implements the infrastructure — Terraform modules, Helm charts, CI/CD integration, and monitoring stack setup. Together they produce cloud infrastructure that scales reliably and costs predictably.

## When to Activate

Activate this skill when the user:

- Needs to design or set up a Kubernetes cluster (EKS, GKE, AKS, self-managed)
- Wants a cloud migration strategy (on-prem to cloud, cloud-to-cloud)
- Is implementing service mesh, ingress controllers, or network policies
- Needs Terraform/IaC modules for cloud resource provisioning
- Uses phrases like "Kubernetes setup", "cloud architecture", "migrate to cloud", "service mesh"
- Wants to optimize cloud costs or implement multi-cloud redundancy

Do not activate for: CI/CD pipeline setup without cloud focus (use `superclaude-devops`) or cost optimization only (use `superclaude-finops-specialist`).

## Agents in This Wave

| Agent | Role | Focus |
|-------|------|-------|
| `cloud-native-architect` | Lead | K8s cluster design, service mesh, multi-cloud, container patterns |
| `devops-engineer` | Specialist | Terraform/IaC, Helm charts, deployment automation, monitoring |

Wave strategy: enterprise | Synthesis: lead_agent | Model: Opus

## How to Call the Bridge

```
POST ${SUPERCLAUDE_BRIDGE_URL}/hooks/agent
Authorization: Bearer ${SUPERCLAUDE_BRIDGE_TOKEN}
Content-Type: application/json

{
  "message": "<the user's request, unmodified>",
  "agentId": "cloud-infra",
  "model": "opus",
  "thinking": "high",
  "deliver": true
}
```

## Output Structure

```
# Cloud Infrastructure Report

## Architecture Design — cloud-native-architect
### Cluster Topology
### Networking & Service Mesh
### Storage Strategy
### Cost Projection

## Implementation — devops-engineer
### Terraform Modules
### Helm Charts / K8s Manifests
### Monitoring & Alerting Setup

## Recommended Next Steps
1. [Immediate provisioning steps]
2. [Load testing before production]
```

## Examples

**Example 1 — Kubernetes cluster for microservices:**

**User:** Design a Kubernetes setup for our 12 microservices running on AWS.

**Response:** `cloud-native-architect` designs an EKS cluster with Karpenter for autoscaling, Istio service mesh for inter-service mTLS, and namespace isolation per team. `devops-engineer` creates Terraform modules for VPC/EKS provisioning, Helm charts for each service, and ArgoCD for GitOps deployment.

**Example 2 — Cloud migration:**

**User:** We need to move from a monolithic VM deployment to Kubernetes.

**Response:** `cloud-native-architect` plans a strangler fig migration — containerize services incrementally, run hybrid (VM + K8s) during transition, with service mesh routing traffic between old and new. `devops-engineer` creates the migration pipeline: Dockerfile per service, staging cluster, canary routing, and rollback automation.

## Error Handling

If the bridge is unreachable:

> Bridge server is not responding. Start it with:
> `./scripts/openclaw/quickstart.sh` (Linux/macOS) or `.\scripts\openclaw\quickstart.ps1` (Windows)

If one specialist fails, findings from the other are presented with a note about the incomplete analysis.
