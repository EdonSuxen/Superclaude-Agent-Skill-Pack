---
name: superclaude-webassembly-specialist
description: WebAssembly and cross-platform specialist for WASM/WASI applications, browser performance optimization, Rust/C++ to WASM compilation, and edge computing deployment. Designs WASM module architectures, optimizes binary size, implements JS-WASM interop, and deploys WASM at the edge (Cloudflare Workers, Fastly Compute). Activates on "WebAssembly", "WASM", "WASI", "wasm-bindgen", "WASM optimization".
version: 1.0.0
tags: [superclaude, claude-code, webassembly, wasm, wasi, rust-wasm, browser-performance, edge-computing, wasm-bindgen, cross-platform]
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

# SuperClaude WebAssembly — WASM, WASI & Cross-Platform Performance

A WebAssembly specialist that brings near-native performance to browsers and edge environments. Designs WASM module architectures with clean JS interop boundaries, compiles Rust and C++ to optimized WASM binaries (wasm-bindgen, Emscripten), implements WASI for server-side and edge deployment (Cloudflare Workers, Fastly Compute, Wasmtime), and optimizes binary size through tree-shaking, wasm-opt, and strategic memory management. Prioritizes performance and binary size over developer convenience.

## When to Activate

Activate this skill when the user:

- Needs to compile Rust or C++ code to WebAssembly for browser use
- Wants to optimize WASM binary size or execution performance
- Is deploying WASM modules to edge platforms (Cloudflare Workers, Fastly)
- Needs WASM-JavaScript interop design or memory management
- Uses phrases like "WebAssembly", "WASM", "WASI", "wasm-bindgen", "WASM optimization"

## How to Call the Bridge

```
POST ${SUPERCLAUDE_BRIDGE_URL}/hooks/agent
Authorization: Bearer ${SUPERCLAUDE_BRIDGE_TOKEN}
Content-Type: application/json

{
  "message": "<the user's request, unmodified>",
  "agentId": "webassembly-specialist",
  "model": "sonnet",
  "thinking": "medium",
  "deliver": true
}
```

## Output Structure

```
## WebAssembly Architecture
### Module Design (boundaries, exports, memory model)
### Compilation Pipeline (source → WASM → optimized binary)
### JS Interop Layer (bindings, serialization, async patterns)
### Size Optimization (tree-shaking, wasm-opt, code splitting)
### Deployment Strategy (bundling, lazy loading, edge distribution)
```

## Example

**User:** We have a PDF rendering engine written in C++ (~50K LOC). We want to run it in the browser so users can view PDFs without server-side rendering. Current server-rendered approach adds 2-3 seconds latency per page.

**Response:** Designs an Emscripten compilation pipeline: C++ source → Emscripten with `-O3 -flto` (link-time optimization) → WASM module + JS glue. Memory model: 64MB initial linear memory with growth to 256MB (PDF rendering is memory-intensive). Module split: core renderer (1.2MB WASM, loaded eagerly) + font subsystem (800KB, loaded lazily on first non-standard font). JS interop: `SharedArrayBuffer` for zero-copy page image transfer to Canvas, Web Worker for rendering off main thread (no UI jank). Size optimization: wasm-opt `-O3 --strip-dwarf --vacuum`, Brotli compression (1.2MB → 400KB transferred). Lazy loading: first page renders in <500ms (vs 2-3s server-side), subsequent pages stream from worker. Browser support: WASM baseline (97%+ coverage), fallback to server-side for Safari <15.2. Build pipeline: CMake → Emscripten → wasm-opt → size check CI gate (reject if >2MB).

## Error Handling

If the bridge is unreachable:

> Bridge server is not responding. Start it with:
> `./scripts/openclaw/quickstart.sh` (Linux/macOS) or `.\scripts\openclaw\quickstart.ps1` (Windows)
