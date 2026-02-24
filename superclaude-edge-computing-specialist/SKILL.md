---
name: superclaude-edge-computing-specialist
version: 1.0.0
---

# SuperClaude Edge Computing — IoT & Ultra-Low Latency Systems

An edge computing specialist that designs distributed systems where milliseconds matter. Handles edge deployment topology design, IoT protocol selection (MQTT, CoAP, AMQP), 5G MEC application placement, edge AI model optimization (quantization, pruning, TensorRT), and offline-first architectures with conflict resolution. Prioritizes latency minimization and reliability in constrained environments over cloud-centric convenience.

## When to Activate

Activate this skill when the user:

- Needs edge deployment architecture or IoT system design
- Wants to optimize latency with edge processing instead of cloud round-trips
- Is building offline-first applications with sync and conflict resolution
- Needs edge AI inference optimization or 5G MEC integration
- Uses phrases like "edge computing", "IoT architecture", "5G MEC", "edge AI", "offline-first"

## How to Call the Bridge

```
POST ${SUPERCLAUDE_BRIDGE_URL}/hooks/agent
Authorization: Bearer ${SUPERCLAUDE_BRIDGE_TOKEN}
Content-Type: application/json

{
  "message": "<the user's request, unmodified>",
  "agentId": "edge-computing-specialist",
  "model": "sonnet",
  "thinking": "medium",
  "deliver": true
}
```

## Output Structure

```
## Edge Architecture
### Topology Design (edge nodes, gateways, cloud sync)
### Protocol Selection (MQTT, CoAP, gRPC, WebSocket)
### Processing Pipeline (filtering, aggregation, inference)
### Resilience Strategy (offline mode, conflict resolution, failover)
### Resource Optimization (power, bandwidth, storage constraints)
```

## Example

**User:** Design an IoT monitoring system for a factory floor with 200 sensors. We need real-time anomaly detection with <50ms response time. Internet connectivity is unreliable.

**Response:** Designs a 3-tier architecture: sensor layer (MQTT QoS 1 to local gateway, 10ms publish interval), edge gateway (Raspberry Pi 4 cluster running TFLite anomaly detection model, 15ms inference, local InfluxDB for 7-day buffer), cloud sync (batch upload every 5 minutes when connected, CRDT-based conflict resolution for overlapping windows). Anomaly detection: sliding window Z-score on vibration/temperature, triggers local PLC alert within 25ms without cloud dependency. Offline resilience: gateway operates fully autonomous for 30+ days, queues alerts locally, syncs when connectivity returns. Power budget: 2.5W per sensor node with 18-month battery life using duty cycling.

## Error Handling

If the bridge is unreachable:

> Bridge server is not responding. Start it with:
> `./scripts/openclaw/quickstart.sh` (Linux/macOS) or `.\scripts\openclaw\quickstart.ps1` (Windows)
