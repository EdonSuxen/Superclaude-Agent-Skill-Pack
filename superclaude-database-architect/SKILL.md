---
name: superclaude-database-architect
version: 1.0.0
---

# Database Architect — Schema Design, Query Optimization, and Migration Planning

A database specialist that designs schemas for data integrity and query performance, not just correctness. Applies normalization principles where they serve performance, denormalizes strategically where they don't, and plans migrations that can be rolled back safely. Covers PostgreSQL, MySQL, MongoDB, Redis, and polyglot persistence strategies for systems that need multiple data stores.

## When to Activate

Activate when the user:

- Needs to design a database schema for a new feature or system
- Has slow queries and wants optimization guidance (EXPLAIN ANALYZE interpretation)
- Is planning a database migration and needs a safe rollback strategy
- Wants to choose between databases for a specific use case (SQL vs NoSQL vs time-series)
- Uses phrases like "design this schema", "why is my query slow", "help with migrations", "which database should I use"
- Needs index strategy, partitioning, or sharding guidance

For API layer that sits on top of the database, use `superclaude-backend-architect`. For full database + backend analysis, use the `superclaude-database` domain pack.

## How to Call the Bridge

```
POST ${SUPERCLAUDE_BRIDGE_URL}/hooks/agent
Authorization: Bearer ${SUPERCLAUDE_BRIDGE_TOKEN}
Content-Type: application/json

{
  "message": "<the user's request, unmodified>",
  "agentId": "database-architect",
  "model": "sonnet",
  "thinking": "medium",
  "deliver": true
}
```

Model: Sonnet — schema design and query optimization require precise, structured analysis.

## Example

**User:** "We have a multi-tenant SaaS app. Each tenant has ~50K rows in the orders table, growing 10% monthly. Queries filter by tenant_id + date range + status. Should we partition? Current P95 is 800ms, target is 100ms."

**Response structure:**
- **Current State Analysis**: Why P95 is 800ms (likely missing composite index or sequential scan)
- **Schema Recommendations**: Index strategy (composite index on tenant_id, created_at, status), partition-by-range on created_at if data exceeds 100M rows
- **Migration Plan**: Step-by-step with CREATE INDEX CONCURRENTLY, zero-downtime approach, rollback commands
- **Verification**: EXPLAIN ANALYZE queries to confirm improvement, pg_stat_user_indexes to verify index usage
- **Growth Projection**: When partitioning becomes necessary given 10% monthly growth

## Error Handling

If the bridge is unreachable:

> `./scripts/openclaw/quickstart.sh` (Linux/macOS) or `.\scripts\openclaw\quickstart.ps1` (Windows)
