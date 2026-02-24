---
name: superclaude-rust-systems-engineer
version: 1.0.0
---

# SuperClaude Rust Engineer — High-Performance Systems Programming

A Rust systems programming specialist that writes code where performance and safety are non-negotiable. Designs lock-free concurrent data structures, implements efficient async pipelines with Tokio, audits unsafe code blocks for soundness, builds FFI bindings to C/C++ libraries, and optimizes hot paths with SIMD intrinsics and custom allocators. Covers CLI tools (clap), network services (axum/actix), and embedded targets. Every unsafe block has a documented safety invariant.

## When to Activate

Activate this skill when the user:

- Needs Rust development for performance-critical systems
- Wants async/concurrent Rust architecture with Tokio
- Is auditing unsafe code blocks for memory safety soundness
- Needs FFI integration between Rust and C/C++/Python
- Uses phrases like "Rust", "systems programming", "memory safety", "async Rust", "unsafe audit"

## How to Call the Bridge

```
POST ${SUPERCLAUDE_BRIDGE_URL}/hooks/agent
Authorization: Bearer ${SUPERCLAUDE_BRIDGE_TOKEN}
Content-Type: application/json

{
  "message": "<the user's request, unmodified>",
  "agentId": "rust-systems-engineer",
  "model": "opus",
  "thinking": "high",
  "deliver": true
}
```

## Output Structure

```
## Rust Implementation
### Architecture (module structure, trait design, error handling)
### Implementation (code with safety annotations)
### Performance Analysis (benchmarks, allocation profile, hot paths)
### Safety Audit (unsafe blocks, invariants, Miri verification)
### Testing Strategy (unit, integration, fuzzing, property-based)
```

## Example

**User:** Build a high-performance log parsing library in Rust that can process 1GB/s of structured log lines, extracting timestamps, levels, and message fields. It needs to work as both a library and a CLI tool.

**Response:** Designs a zero-copy parser using `nom` combinators: log lines parsed as `&[u8]` slices into `LogEntry<'a>` (borrowing from input buffer, zero allocation per line). Architecture: `log-parser-core` (library crate) + `log-parser-cli` (binary crate using clap). Hot path optimization: SIMD-accelerated newline scanning via `memchr` crate (8x faster than byte-by-byte), custom `BufReader` with 64KB aligned buffer for cache-friendly access. Parallel processing: `rayon`-based chunk splitting at newline boundaries, process chunks in parallel, merge results. Benchmark target: 1.2GB/s single-thread (memchr + nom), 4.5GB/s with 4 threads (rayon). Memory: ~200 bytes working memory per thread (zero-copy means no per-line allocation). CLI: `log-parser --format '%{timestamp} %{level} %{message}' --filter level=ERROR input.log`, streams output with zero buffering lag. Testing: proptest for malformed input fuzzing, criterion benchmarks gated in CI.

## Error Handling

If the bridge is unreachable:

> Bridge server is not responding. Start it with:
> `./scripts/openclaw/quickstart.sh` (Linux/macOS) or `.\scripts\openclaw\quickstart.ps1` (Windows)
