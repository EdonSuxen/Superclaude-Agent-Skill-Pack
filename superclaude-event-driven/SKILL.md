---
name: superclaude-event-driven
version: 1.0.0
---

# SuperClaude Event-Driven — Messaging & Event Sourcing Architecture

Two specialists design reliable asynchronous systems. `event-driven-architect` handles the architectural patterns — event sourcing with append-only stores, CQRS read/write separation, saga orchestration for distributed transactions, message schema evolution (Avro/Protobuf), and topic topology design. `backend-architect` implements the consumer side — idempotent message handlers, dead letter queue strategies, exactly-once processing semantics, and transaction boundary management. Together they produce event-driven systems that are resilient, scalable, and debuggable.

## When to Activate

Activate this skill when the user:

- Wants to implement event sourcing or CQRS patterns
- Needs Kafka, RabbitMQ, or NATS architecture and setup
- Is designing distributed transactions with saga patterns
- Needs message schema design or schema evolution strategy
- Uses phrases like "event sourcing", "Kafka setup", "CQRS", "message queue", "saga pattern"
- Has reliability issues with async message processing (lost messages, duplicates)

Do not activate for: synchronous API design (use `superclaude-api-design`) or general backend architecture without messaging focus (use `superclaude-backend-architect`).

## Agents in This Wave

| Agent | Role | Focus |
|-------|------|-------|
| `event-driven-architect` | Lead | Event sourcing, CQRS, saga patterns, schema design, topology |
| `backend-architect` | Specialist | Consumer implementation, idempotency, DLQ, transaction boundaries |

Wave strategy: progressive | Synthesis: lead_agent | Model: Sonnet

## How to Call the Bridge

```
POST ${SUPERCLAUDE_BRIDGE_URL}/hooks/agent
Authorization: Bearer ${SUPERCLAUDE_BRIDGE_TOKEN}
Content-Type: application/json

{
  "message": "<the user's request, unmodified>",
  "agentId": "event-driven",
  "model": "sonnet",
  "thinking": "medium",
  "deliver": true
}
```

## Output Structure

```
# Event-Driven Architecture Report

## Architecture Design — event-driven-architect
### Event Schema Definitions
### Topic/Queue Topology
### Consistency Patterns (saga/CQRS)
### Schema Evolution Strategy

## Implementation — backend-architect
### Consumer Design (idempotency, ordering)
### Error Handling & DLQ Strategy
### Transaction Boundaries

## Recommended Next Steps
1. [Immediate implementation steps]
2. [Load testing for throughput validation]
```

## Examples

**Example 1 — Order processing with event sourcing:**

**User:** Design an event-sourced order processing system with Kafka.

**Response:** `event-driven-architect` designs the event store (OrderCreated, ItemAdded, PaymentProcessed, OrderShipped), Kafka topic partitioning by order_id, and a saga for the payment→inventory→shipping flow with compensation events. `backend-architect` implements idempotent consumers with deduplication table, exactly-once Kafka transactions, and a DLQ for poison messages.

**Example 2 — Migrating from sync to async:**

**User:** Our checkout calls 5 services synchronously and times out. Help us go async.

**Response:** `event-driven-architect` designs an event-driven checkout flow: emit CheckoutInitiated, have each service subscribe and emit completion events, with a saga coordinator tracking overall state. `backend-architect` implements the transition: dual-write period with outbox pattern, consumer group configuration, and graceful fallback to sync during migration.

## Error Handling

If the bridge is unreachable:

> Bridge server is not responding. Start it with:
> `./scripts/openclaw/quickstart.sh` (Linux/macOS) or `.\scripts\openclaw\quickstart.ps1` (Windows)

If one specialist fails, findings from the other are presented with a note about the incomplete analysis.
