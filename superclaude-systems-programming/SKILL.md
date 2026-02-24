---
name: superclaude-systems-programming
version: 1.0.0
---

# SuperClaude Systems Programming — Rust & Embedded Engineering

Two specialists handle the full spectrum of systems-level development. `rust-systems-engineer` covers memory-safe high-performance code — ownership patterns, async/await runtime design, unsafe Rust with safety invariants, FFI boundaries, and zero-cost abstractions. `embedded-systems-engineer` handles resource-constrained environments — RTOS selection and configuration, bare-metal development, hardware interfacing (SPI, I2C, UART), interrupt handling, and power optimization for battery-powered devices.

## When to Activate

Activate this skill when the user:

- Is writing or porting code to Rust and needs ownership/lifetime guidance
- Needs to develop firmware or embedded software for microcontrollers
- Wants to optimize systems code for performance or memory footprint
- Is designing FFI boundaries between Rust and C/C++
- Uses phrases like "write in Rust", "embedded firmware", "bare-metal", "memory-safe", "RTOS"
- Needs to evaluate Rust async runtimes (tokio, async-std) or no_std environments

Do not activate for: WebAssembly compilation (use `superclaude-wasm`) or general backend development (use `superclaude-api-design`).

## Agents in This Wave

| Agent | Role | Focus |
|-------|------|-------|
| `rust-systems-engineer` | Lead | Ownership, async, unsafe Rust, FFI, zero-cost abstractions |
| `embedded-systems-engineer` | Specialist | RTOS, bare-metal, hardware interfacing, power optimization |

Wave strategy: progressive | Synthesis: lead_agent | Model: Opus

## How to Call the Bridge

```
POST ${SUPERCLAUDE_BRIDGE_URL}/hooks/agent
Authorization: Bearer ${SUPERCLAUDE_BRIDGE_TOKEN}
Content-Type: application/json

{
  "message": "<the user's request, unmodified>",
  "agentId": "systems-programming",
  "model": "opus",
  "thinking": "high",
  "deliver": true
}
```

## Output Structure

```
# Systems Programming Report

## Rust Implementation — rust-systems-engineer
### Design (ownership model, trait boundaries)
### Safety Analysis (unsafe blocks, invariants)
### Performance Profile (benchmarks, allocations)

## Embedded Integration — embedded-systems-engineer
### Hardware Interface Design
### Resource Budget (RAM, flash, CPU cycles)
### RTOS Configuration (if applicable)

## Recommended Next Steps
1. [Implementation priorities]
2. [Testing and verification plan]
```

## Examples

**Example 1 — Rust async service:**

**User:** I need to build a high-throughput TCP server in Rust that handles 100K concurrent connections.

**Response:** `rust-systems-engineer` designs a tokio-based server with io_uring backend, connection pooling via tower, and zero-copy buffer management. Provides ownership model for shared state (Arc<RwLock> vs DashMap tradeoffs), benchmarks showing throughput at 100K connections, and unsafe blocks documented with safety invariants. `embedded-systems-engineer` advises on kernel tuning (SO_REUSEPORT, epoll edge-triggered) for bare-metal-like performance on Linux.

**Example 2 — Embedded sensor firmware:**

**User:** I need firmware for an STM32 that reads 4 I2C sensors and transmits over BLE every 100ms.

**Response:** `embedded-systems-engineer` designs the firmware architecture: Embassy async runtime on no_std, DMA-based I2C reads for all 4 sensors in parallel, BLE stack with SoftDevice. Power budget shows 18-month battery life at 100ms intervals. `rust-systems-engineer` reviews the unsafe HAL abstractions, ensures no undefined behavior in DMA buffer management, and provides a testing strategy using defmt + probe-rs.

## Error Handling

If the bridge is unreachable:

> Bridge server is not responding. Start it with:
> `./scripts/openclaw/quickstart.sh` (Linux/macOS) or `.\scripts\openclaw\quickstart.ps1` (Windows)

If one specialist fails, findings from the other are presented with a note about the incomplete analysis.
