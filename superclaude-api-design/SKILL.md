---
name: superclaude-api-design
description: Contract-first API design and implementation using two specialists — api-architect (OpenAPI specs, REST/GraphQL/gRPC patterns, versioning strategy, rate limiting) and backend-architect (service implementation, middleware, authentication, error handling). Returns OpenAPI specs, endpoint contracts, and implementation scaffolding. Activates on "design an API", "REST vs GraphQL", "API versioning", "OpenAPI spec".
version: 1.0.0
tags: [superclaude, claude-code, api-design, rest, graphql, grpc, openapi, swagger, api-gateway, versioning]
category: developer-tools
metadata:
  openclaw:
    emoji: "🔗"
    os: [darwin, linux, win32]
    requires:
      bins: [node]
      env:
        - SUPERCLAUDE_BRIDGE_URL
        - SUPERCLAUDE_BRIDGE_TOKEN
      primaryEnv: SUPERCLAUDE_BRIDGE_TOKEN
    homepage: https://github.com/EdonSuxen/Superclaude-Agent-Skill-Pack
---

# SuperClaude API Design — Contract-First Engineering

Two specialists ensure APIs are well-designed before a single line of implementation is written. `api-architect` handles the contract layer — OpenAPI 3.1 specifications, REST resource modeling, GraphQL schema design, gRPC proto definitions, versioning strategy, and rate limiting policies. `backend-architect` takes those contracts and produces clean implementations — route handlers, middleware chains, authentication flows, error response patterns, and pagination. Together they produce APIs that are consistent, documented, and developer-friendly.

## When to Activate

Activate this skill when the user:

- Needs to design a new API (REST, GraphQL, or gRPC)
- Wants an OpenAPI/Swagger specification for existing or planned endpoints
- Is choosing between API paradigms (REST vs GraphQL vs gRPC)
- Needs API versioning, rate limiting, or gateway configuration
- Uses phrases like "design an API", "REST vs GraphQL", "API versioning", "OpenAPI spec"
- Is building a public API that needs developer documentation

Do not activate for: backend service architecture without API focus (use `superclaude-backend-architect`) or database layer (use `superclaude-database`).

## Agents in This Wave

| Agent | Role | Focus |
|-------|------|-------|
| `api-architect` | Lead | OpenAPI specs, resource modeling, versioning, rate limiting, DX |
| `backend-architect` | Specialist | Route implementation, middleware, auth, error handling, pagination |

Wave strategy: progressive | Synthesis: lead_agent | Model: Sonnet

## How to Call the Bridge

```
POST ${SUPERCLAUDE_BRIDGE_URL}/hooks/agent
Authorization: Bearer ${SUPERCLAUDE_BRIDGE_TOKEN}
Content-Type: application/json

{
  "message": "<the user's request, unmodified>",
  "agentId": "api-design",
  "model": "sonnet",
  "thinking": "medium",
  "deliver": true
}
```

## Output Structure

```
# API Design Report

## API Contract — api-architect
### Resource Model
### Endpoint Specifications (OpenAPI)
### Versioning Strategy
### Rate Limiting Policy

## Implementation Plan — backend-architect
### Route Structure
### Middleware Chain
### Authentication Flow
### Error Response Schema

## Recommended Next Steps
1. [Immediate actions]
2. [Client SDK generation]
```

## Examples

**Example 1 — E-commerce API:**

**User:** Design a REST API for our e-commerce platform — products, orders, and payments.

**Response:** `api-architect` produces an OpenAPI 3.1 spec with resource hierarchy (/products, /orders, /payments), HATEOAS links, cursor pagination, and idempotency keys for payment endpoints. `backend-architect` scaffolds Express routes with Zod validation, JWT middleware, and standardized error responses.

**Example 2 — GraphQL migration:**

**User:** We want to migrate from REST to GraphQL. How should we approach this?

**Response:** `api-architect` designs a strangler fig pattern — GraphQL gateway in front of existing REST services, with schema stitching for gradual migration. `backend-architect` implements the Apollo Server setup with DataLoader for N+1 prevention and persisted queries for production safety.

## Error Handling

If the bridge is unreachable:

> Bridge server is not responding. Start it with:
> `./scripts/openclaw/quickstart.sh` (Linux/macOS) or `.\scripts\openclaw\quickstart.ps1` (Windows)

If one specialist fails, findings from the other are presented with a note about the incomplete analysis.
