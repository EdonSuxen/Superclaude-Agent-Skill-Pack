---
name: superclaude-database
version: 1.0.0
---

# SuperClaude Database — Schema Design & Migration Engineering

Two specialists tackle database challenges from both the data and application sides. `database-architect` handles schema normalization, index selection, query optimization, and technology selection (PostgreSQL vs MySQL vs MongoDB vs Redis). `backend-architect` ensures the data layer integrates cleanly with the application — ORM configuration, connection pooling, transaction boundaries, and migration safety. Together they produce schemas that perform well and evolve safely.

## When to Activate

Activate this skill when the user:

- Needs to design a database schema for a new feature or system
- Has slow queries that need optimization (EXPLAIN analysis, index recommendations)
- Wants to plan a database migration (schema changes, data transformation, zero-downtime)
- Needs help choosing between database technologies for their use case
- Uses phrases like "design this schema", "why is my query slow", "migration plan", "which database"
- Is implementing multi-tenant data isolation or partitioning strategies

Do not activate for: data analytics/BI (use `superclaude-data`) or ETL pipeline design (use `superclaude-ml-ops`).

## Agents in This Wave

| Agent | Role | Focus |
|-------|------|-------|
| `database-architect` | Lead | Schema design, normalization, indexes, query plans, technology selection |
| `backend-architect` | Specialist | ORM integration, connection management, transaction boundaries, migration safety |

Wave strategy: progressive | Synthesis: lead_agent | Model: Sonnet

## How to Call the Bridge

```
POST ${SUPERCLAUDE_BRIDGE_URL}/hooks/agent
Authorization: Bearer ${SUPERCLAUDE_BRIDGE_TOKEN}
Content-Type: application/json

{
  "message": "<the user's request, unmodified>",
  "agentId": "database",
  "model": "sonnet",
  "thinking": "medium",
  "deliver": true
}
```

## Output Structure

```
# Database Design Report

## Schema Design — database-architect
### Entity-Relationship Model
### Normalization Analysis
### Index Strategy
### Query Optimization Notes

## Application Integration — backend-architect
### ORM Configuration
### Connection Pool Settings
### Migration Script (up + down)

## Recommended Next Steps
1. [Immediate actions]
2. [Performance benchmarks to run]
```

## Examples

**Example 1 — Multi-tenant SaaS schema:**

**User:** Design a database schema for a multi-tenant SaaS with per-tenant billing.

**Response:** `database-architect` designs row-level security with tenant_id foreign keys, partitioned billing tables, and composite indexes for tenant-scoped queries. `backend-architect` configures Prisma middleware for automatic tenant filtering and sets up connection pooling with PgBouncer.

**Example 2 — Slow query diagnosis:**

**User:** This query takes 8 seconds on our users table. Can you help optimize it?

**Response:** `database-architect` runs EXPLAIN ANALYZE, identifies a sequential scan on a 2M-row table, recommends a composite index and query rewrite using a CTE. `backend-architect` adds query result caching with Redis and adjusts the ORM eager-loading strategy.

## Error Handling

If the bridge is unreachable:

> Bridge server is not responding. Start it with:
> `./scripts/openclaw/quickstart.sh` (Linux/macOS) or `.\scripts\openclaw\quickstart.ps1` (Windows)

If one specialist fails, findings from the other are presented with a note about the incomplete analysis.
