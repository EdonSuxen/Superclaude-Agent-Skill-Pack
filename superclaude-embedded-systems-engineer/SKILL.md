---
name: superclaude-embedded-systems-engineer
version: 1.0.0
---

# SuperClaude Embedded Systems — Firmware & Hardware Integration

An embedded systems specialist that writes reliable firmware for resource-constrained environments. Handles RTOS task design (FreeRTOS, Zephyr, ThreadX), bare-metal programming, peripheral driver development (SPI, I2C, UART, CAN bus), interrupt service routine optimization, memory-constrained architecture (static allocation, memory pools), and power management strategies. Writes firmware in C, C++, and Rust with a focus on deterministic real-time behavior and minimal memory footprint.

## When to Activate

Activate this skill when the user:

- Needs firmware development for microcontrollers (STM32, ESP32, nRF, PIC)
- Wants RTOS task architecture or bare-metal system design
- Is interfacing with hardware peripherals (sensors, actuators, communication buses)
- Needs memory optimization, power management, or interrupt handling
- Uses phrases like "embedded firmware", "RTOS", "bare-metal", "hardware interface", "microcontroller"

## How to Call the Bridge

```
POST ${SUPERCLAUDE_BRIDGE_URL}/hooks/agent
Authorization: Bearer ${SUPERCLAUDE_BRIDGE_TOKEN}
Content-Type: application/json

{
  "message": "<the user's request, unmodified>",
  "agentId": "embedded-systems-engineer",
  "model": "opus",
  "thinking": "high",
  "deliver": true
}
```

## Output Structure

```
## Embedded System Design
### Architecture (task model, memory map, peripheral allocation)
### Firmware Implementation (drivers, ISRs, state machines)
### Resource Budget (RAM, flash, CPU cycles, power)
### Testing Strategy (HIL, unit tests, fault injection)
### Safety Considerations (watchdog, brownout detection, failsafe)
```

## Example

**User:** Design a battery-powered environmental sensor node using an STM32L4 that reads temperature, humidity, and air quality every 30 seconds and transmits via LoRa. Target battery life is 2 years on 2xAA batteries.

**Response:** Designs a low-power architecture: STM32L4 in STOP2 mode (1.1uA) with RTC wakeup every 30s, sensor readings via I2C (BME280 + SGP40) with 50ms active window, LoRa transmission via SX1276 SPI (SF7, 14dBm, ~80ms airtime). Power budget: 3200mAh capacity, average draw 12uA including transmission → 30.4 months (exceeds 2-year target). FreeRTOS with 3 tasks: sensor_read (highest priority), lora_transmit (medium), sleep_manager (idle). Memory: 8KB RAM usage (4KB stack, 2KB buffers, 2KB state), 64KB flash. Failsafe: hardware watchdog (4s timeout), brownout detection triggers graceful shutdown writing last reading to flash. OTA updates via LoRa Class C window during nightly maintenance.

## Error Handling

If the bridge is unreachable:

> Bridge server is not responding. Start it with:
> `./scripts/openclaw/quickstart.sh` (Linux/macOS) or `.\scripts\openclaw\quickstart.ps1` (Windows)
