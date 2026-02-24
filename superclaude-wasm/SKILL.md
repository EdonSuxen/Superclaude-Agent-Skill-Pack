---
name: superclaude-wasm
description: WebAssembly development using two specialists — webassembly-specialist (WASM/WASI compilation, browser integration, edge deployment, cross-platform portability) and rust-systems-engineer (Rust-to-WASM toolchain, wasm-bindgen, memory management, performance optimization). Returns WASM modules with binding code and deployment strategies. Activates on "compile to WASM", "WebAssembly module", "WASI runtime", "Rust to browser".
version: 1.0.0
tags: [superclaude, claude-code, webassembly, wasi, cross-platform, rust, wasm-bindgen, browser-performance, edge-computing, wasm-compilation]
category: developer-tools
metadata:
  openclaw:
    emoji: "🌐"
    os: [darwin, linux, win32]
    requires:
      bins: [node]
      env:
        - SUPERCLAUDE_BRIDGE_URL
        - SUPERCLAUDE_BRIDGE_TOKEN
      primaryEnv: SUPERCLAUDE_BRIDGE_TOKEN
    homepage: https://github.com/EdonSuxen/Superclaude-Agent-Skill-Pack
---

# SuperClaude WASM — WebAssembly & Cross-Platform Compilation

Two specialists bridge the gap between high-performance native code and portable execution. `webassembly-specialist` handles WASM/WASI compilation targets, browser integration (JS interop, Web Workers), edge deployment (Cloudflare Workers, Fastly Compute), and cross-platform portability strategies. `rust-systems-engineer` optimizes the Rust-to-WASM toolchain — wasm-bindgen configuration, memory management without allocator overhead, wasm-opt passes, and zero-copy data transfer between host and WASM module.

## When to Activate

Activate this skill when the user:

- Needs to compile Rust, C, or C++ code to WebAssembly
- Wants to run compute-heavy logic in the browser (image processing, crypto, codecs)
- Is deploying WASM modules to edge runtimes (Cloudflare Workers, Fastly, Deno Deploy)
- Needs to optimize WASM module size or execution performance
- Uses phrases like "compile to WASM", "WebAssembly module", "WASI", "Rust to browser", "wasm-pack"
- Is evaluating WASM vs JavaScript for specific workloads

Do not activate for: pure Rust systems programming (use `superclaude-systems-programming`) or embedded/firmware development (use `superclaude-iot`).

## Agents in This Wave

| Agent | Role | Focus |
|-------|------|-------|
| `webassembly-specialist` | Lead | WASM/WASI compilation, browser interop, edge deployment, portability |
| `rust-systems-engineer` | Specialist | Rust toolchain, wasm-bindgen, memory management, wasm-opt |

Wave strategy: progressive | Synthesis: lead_agent | Model: Sonnet

## How to Call the Bridge

```
POST ${SUPERCLAUDE_BRIDGE_URL}/hooks/agent
Authorization: Bearer ${SUPERCLAUDE_BRIDGE_TOKEN}
Content-Type: application/json

{
  "message": "<the user's request, unmodified>",
  "agentId": "wasm",
  "model": "sonnet",
  "thinking": "medium",
  "deliver": true
}
```

## Output Structure

```
# WebAssembly Report

## WASM Architecture — webassembly-specialist
### Compilation Target (browser, WASI, edge)
### Host Integration (JS bindings, memory model)
### Deployment Strategy
### Module Size Analysis

## Rust Optimization — rust-systems-engineer
### Toolchain Configuration (wasm-pack, wasm-opt)
### Memory Management (allocator, data transfer)
### Performance Profile (benchmarks vs JS baseline)

## Recommended Next Steps
1. [Build and test commands]
2. [Optimization passes to run]
```

## Examples

**Example 1 — Image processing in the browser:**

**User:** I want to add real-time image filters to our web app. JavaScript is too slow for 4K images.

**Response:** `webassembly-specialist` designs a WASM module architecture: Rust image processing compiled via wasm-pack, loaded as a Web Worker to avoid blocking the main thread, with SharedArrayBuffer for zero-copy image data transfer. `rust-systems-engineer` implements the filter pipeline using SIMD intrinsics (wasm32 SIMD), configures wasm-opt for size (115KB final module), and benchmarks showing 8x speedup over pure JS Canvas API.

**Example 2 — Edge function with WASI:**

**User:** We need to run our Rust validation logic on Cloudflare Workers instead of our API server.

**Response:** `webassembly-specialist` designs the WASI-compatible module with Cloudflare's component model, handles request/response binding via wasi-http, and sets up the wrangler configuration. `rust-systems-engineer` refactors the validation library to be no_std compatible, eliminates filesystem dependencies, and optimizes the module to 180KB (under Cloudflare's 1MB limit). Cold start benchmarks show 2ms vs 150ms for the equivalent Node.js Worker.

## Error Handling

If the bridge is unreachable:

> Bridge server is not responding. Start it with:
> `./scripts/openclaw/quickstart.sh` (Linux/macOS) or `.\scripts\openclaw\quickstart.ps1` (Windows)

If one specialist fails, findings from the other are presented with a note about the incomplete analysis.
