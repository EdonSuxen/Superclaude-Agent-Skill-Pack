---
name: superclaude-iot
description: IoT and embedded systems using two specialists — edge-computing-specialist (edge architectures, MQTT/CoAP protocols, real-time processing, offline-first patterns, 5G MEC) and embedded-systems-engineer (RTOS, bare-metal C/C++/Rust, hardware interfacing, power optimization). Returns system architectures, firmware designs, and communication protocols. Activates on "IoT architecture", "embedded firmware", "edge processing", "sensor network".
version: 1.0.0
tags: [superclaude, claude-code, iot, edge-computing, embedded, mqtt, rtos, firmware, sensor, real-time]
category: developer-tools
metadata:
  openclaw:
    emoji: "📡"
    os: [darwin, linux, win32]
    requires:
      bins: [node]
      env:
        - SUPERCLAUDE_BRIDGE_URL
        - SUPERCLAUDE_BRIDGE_TOKEN
      primaryEnv: SUPERCLAUDE_BRIDGE_TOKEN
    homepage: https://github.com/EdonSuxen/Superclaude-Agent-Skill-Pack
---

# SuperClaude IoT — Edge Computing & Embedded Engineering

Two specialists cover the full IoT stack from silicon to cloud. `edge-computing-specialist` designs the distributed architecture — MQTT/CoAP message brokers, edge inference for low-latency decisions, offline-first data synchronization, 5G MEC integration, and fleet management. `embedded-systems-engineer` handles the device side — RTOS selection (FreeRTOS, Zephyr), bare-metal firmware in C/C++/Rust, hardware interfacing (SPI, I2C, UART), power budget optimization, and OTA update mechanisms. Together they produce IoT systems that are reliable in the field and scalable in the cloud.

## When to Activate

Activate this skill when the user:

- Is designing an IoT system (sensor networks, industrial IoT, consumer devices)
- Needs embedded firmware development or RTOS configuration
- Wants edge computing architecture for real-time processing
- Needs IoT communication protocol selection (MQTT, CoAP, BLE, LoRaWAN)
- Uses phrases like "IoT architecture", "embedded firmware", "edge processing", "sensor network"
- Has power consumption, connectivity, or OTA update challenges

Do not activate for: cloud infrastructure without IoT context (use `superclaude-cloud-infra`) or general systems programming (use `superclaude-systems-programming`).

## Agents in This Wave

| Agent | Role | Focus |
|-------|------|-------|
| `edge-computing-specialist` | Lead | Edge architecture, protocols, real-time processing, fleet management |
| `embedded-systems-engineer` | Specialist | RTOS, firmware, hardware interfacing, power optimization, OTA |

Wave strategy: progressive | Synthesis: consensus | Model: Sonnet

## How to Call the Bridge

```
POST ${SUPERCLAUDE_BRIDGE_URL}/hooks/agent
Authorization: Bearer ${SUPERCLAUDE_BRIDGE_TOKEN}
Content-Type: application/json

{
  "message": "<the user's request, unmodified>",
  "agentId": "iot",
  "model": "sonnet",
  "thinking": "medium",
  "deliver": true
}
```

## Output Structure

```
# IoT Architecture Report

## Edge Architecture — edge-computing-specialist
### System Topology
### Communication Protocol Selection
### Data Flow & Processing Pipeline
### Fleet Management Strategy

## Device Engineering — embedded-systems-engineer
### Hardware Selection
### Firmware Architecture
### Power Budget Analysis
### OTA Update Mechanism

## Recommended Next Steps
1. [Prototype hardware and connectivity]
2. [Edge pipeline benchmarks]
```

## Examples

**Example 1 — Industrial sensor network:**

**User:** Design an IoT system for monitoring 200 temperature/humidity sensors in a warehouse.

**Response:** `edge-computing-specialist` designs a hub-spoke topology with MQTT over WiFi, local edge gateway for anomaly detection (no cloud roundtrip for alerts), and time-series database (InfluxDB) for historical data. `embedded-systems-engineer` selects ESP32-S3 with deep sleep for 2-year battery life, designs the sensor reading firmware with FreeRTOS tasks, and implements OTA updates via MQTT.

**Example 2 — Edge AI inference:**

**User:** We need to run object detection on cameras at retail locations with <100ms latency.

**Response:** `edge-computing-specialist` designs edge inference with NVIDIA Jetson at each location, model optimization (TensorRT, INT8 quantization), and results streaming to cloud via gRPC. `embedded-systems-engineer` handles the camera interface firmware, hardware synchronization, and watchdog timer for reliability.

## Error Handling

If the bridge is unreachable:

> Bridge server is not responding. Start it with:
> `./scripts/openclaw/quickstart.sh` (Linux/macOS) or `.\scripts\openclaw\quickstart.ps1` (Windows)

If one specialist fails, findings from the other are presented with a note about the incomplete analysis.
