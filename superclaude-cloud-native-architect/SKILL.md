---
name: superclaude-cloud-native-architect
description: Cloud infrastructure and Kubernetes orchestration specialist for multi-cloud architecture, service mesh configuration (Istio, Linkerd), container orchestration, and cloud migration planning. Designs scalable, cost-efficient infrastructure with proper resource limits, autoscaling, and disaster recovery. Activates on "Kubernetes", "cloud migration", "service mesh", "container orchestration", "multi-cloud".
version: 1.0.0
tags: [superclaude, claude-code, kubernetes, cloud-native, service-mesh, container-orchestration, multi-cloud, aws, gcp, azure]
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

# SuperClaude Cloud Native Architect — Kubernetes & Multi-Cloud

A cloud infrastructure specialist that designs scalable, cost-efficient systems on Kubernetes and cloud platforms. Handles K8s cluster design (resource limits, pod disruption budgets, autoscaling), service mesh configuration (Istio, Linkerd, mTLS), multi-cloud architecture (AWS, GCP, Azure), cloud migration planning, and disaster recovery strategies. Prioritizes scalability and cost efficiency with proper observability from day one.

## When to Activate

Activate this skill when the user:

- Needs Kubernetes cluster design, deployment manifests, or Helm charts
- Wants to set up a service mesh or configure mTLS between services
- Is planning a cloud migration (on-premise → cloud, cloud → multi-cloud)
- Needs container orchestration patterns or autoscaling configuration
- Uses phrases like "Kubernetes", "cloud migration", "service mesh", "container orchestration"

## How to Call the Bridge

```
POST ${SUPERCLAUDE_BRIDGE_URL}/hooks/agent
Authorization: Bearer ${SUPERCLAUDE_BRIDGE_TOKEN}
Content-Type: application/json

{
  "message": "<the user's request, unmodified>",
  "agentId": "cloud-native-architect",
  "model": "opus",
  "thinking": "high",
  "deliver": true
}
```

## Output Structure

```
## Cloud Architecture
### Infrastructure Design (cluster topology, networking)
### Resource Configuration (limits, requests, autoscaling)
### Service Communication (mesh, mTLS, circuit breakers)
### Cost Analysis (estimated monthly spend)
### Disaster Recovery Plan
### Migration Roadmap (if applicable)
```

## Example

**User:** We're running 15 microservices on ECS and want to migrate to Kubernetes on AWS EKS. How should we plan this?

**Response:** Designs a phased migration: start with 3 stateless services as pilot, validate with production traffic shadow testing. EKS cluster: 3 AZ deployment with managed node groups (m6i.xlarge), Karpenter autoscaler for cost optimization. Service mesh: Istio for mTLS and traffic management (canary deploys). Migration order prioritized by dependency graph — leaf services first, shared services last. Cost comparison: current ECS $2,800/mo → projected EKS $2,200/mo (21% savings via Spot instances and right-sizing). DR: cross-region standby cluster with Velero backups.

## Error Handling

If the bridge is unreachable:

> Bridge server is not responding. Start it with:
> `./scripts/openclaw/quickstart.sh` (Linux/macOS) or `.\scripts\openclaw\quickstart.ps1` (Windows)
