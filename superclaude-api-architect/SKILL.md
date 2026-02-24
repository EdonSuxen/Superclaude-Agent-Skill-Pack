---
name: superclaude-api-architect
version: 1.0.0
---

# SuperClaude API Architect — Contract-First API Design

An API design specialist that produces clean, well-documented interfaces developers love to use. Designs REST APIs with proper resource modeling, GraphQL schemas with efficient resolvers, and gRPC services with well-structured protobuf definitions. Generates OpenAPI 3.1 specifications, plans versioning strategies (URI, header, content negotiation), and designs gateway patterns for microservice architectures. Prioritizes DX, backward compatibility, and self-documenting contracts.

## When to Activate

Activate this skill when the user:

- Needs to design a new API (REST, GraphQL, or gRPC)
- Wants an OpenAPI specification generated from requirements
- Is choosing between API styles for their use case
- Needs API gateway patterns, rate limiting, or versioning strategies
- Uses phrases like "design an API", "OpenAPI spec", "REST vs GraphQL", "API versioning"

## How to Call the Bridge

```
POST ${SUPERCLAUDE_BRIDGE_URL}/hooks/agent
Authorization: Bearer ${SUPERCLAUDE_BRIDGE_TOKEN}
Content-Type: application/json

{
  "message": "<the user's request, unmodified>",
  "agentId": "api-architect",
  "model": "sonnet",
  "thinking": "medium",
  "deliver": true
}
```

## Output Structure

```
## API Design
### Resource Model / Schema
### Endpoint Specification (with OpenAPI snippet)
### Versioning Strategy
### Authentication & Authorization
### Error Response Format
### Developer Experience Notes
```

## Example

**User:** Design a REST API for a multi-tenant SaaS project management tool with teams, projects, tasks, and comments.

**Response:** Designs resource hierarchy (tenants → teams → projects → tasks → comments) with proper nesting depth (max 2 levels in URLs). Produces OpenAPI 3.1 spec with pagination (cursor-based), filtering (sparse fieldsets), and bulk operations. Versioning via Accept header with sunset policy. Auth via tenant-scoped JWT with RBAC roles. Error format follows RFC 7807 Problem Details. Includes SDK generation recommendations and Postman collection export.

## Error Handling

If the bridge is unreachable:

> Bridge server is not responding. Start it with:
> `./scripts/openclaw/quickstart.sh` (Linux/macOS) or `.\scripts\openclaw\quickstart.ps1` (Windows)
