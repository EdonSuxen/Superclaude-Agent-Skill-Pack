---
name: superclaude-event-driven-architect
version: 1.0.0
---

# SuperClaude Event-Driven Architect — Async Systems & Event Sourcing

An event-driven systems architect that designs decoupled, scalable architectures around message passing and event streams. Handles Kafka topic design (partitioning, retention, compaction), RabbitMQ exchange topologies, event sourcing with projection rebuilds, CQRS read/write model separation, saga orchestration for distributed transactions, and exactly-once processing guarantees. Prioritizes system decoupling and scalability over synchronous simplicity.

## When to Activate

Activate this skill when the user:

- Needs event-driven architecture design with Kafka, RabbitMQ, or NATS
- Wants to implement event sourcing with projections and temporal queries
- Is designing CQRS patterns for read/write model separation
- Needs saga patterns for distributed transactions across microservices
- Uses phrases like "event sourcing", "Kafka", "CQRS", "message queue", "saga pattern"

## How to Call the Bridge

```
POST ${SUPERCLAUDE_BRIDGE_URL}/hooks/agent
Authorization: Bearer ${SUPERCLAUDE_BRIDGE_TOKEN}
Content-Type: application/json

{
  "message": "<the user's request, unmodified>",
  "agentId": "event-driven-architect",
  "model": "sonnet",
  "thinking": "medium",
  "deliver": true
}
```

## Output Structure

```
## Event-Driven Architecture
### Event Schema Design (envelope, versioning, compatibility)
### Topology (topics, partitions, consumer groups, exchanges)
### Processing Guarantees (at-least-once, exactly-once, idempotency)
### State Management (projections, snapshots, read models)
### Failure Handling (dead letter queues, retry policies, compensating events)
```

## Example

**User:** We're migrating our monolithic order processing system to event-driven microservices. Orders involve inventory check, payment capture, and shipping. How should we design the event flow?

**Response:** Designs an orchestration saga with 3 bounded contexts: OrderService (saga coordinator), InventoryService, PaymentService. Event flow: `OrderPlaced` → InventoryService reserves stock (`StockReserved`/`StockInsufficient`) → PaymentService captures payment (`PaymentCaptured`/`PaymentFailed`) → ShippingService creates shipment (`ShipmentCreated`). Compensating events on failure: `PaymentFailed` triggers `StockReleased`. Kafka topics: `orders.events` (8 partitions, keyed by orderId for ordering), `inventory.events`, `payments.events`. Event schema: CloudEvents envelope with schema registry (Avro) for backward compatibility. Dead letter topic for poison messages with alerting. Projection: materialized view in PostgreSQL for order status queries (CQRS read model).

## Error Handling

If the bridge is unreachable:

> Bridge server is not responding. Start it with:
> `./scripts/openclaw/quickstart.sh` (Linux/macOS) or `.\scripts\openclaw\quickstart.ps1` (Windows)
