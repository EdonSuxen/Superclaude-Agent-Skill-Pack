---
name: superclaude-vercel
version: 1.0.0
---

# SuperClaude Vercel — Deployment Intelligence

Two specialists optimize the full Vercel deployment lifecycle. `devops-engineer` handles pipeline analysis — build configuration, environment variable management, deployment strategies (preview vs production), rollback procedures, and CI/CD integration with GitHub/GitLab. `performance-engineer` handles runtime optimization — build step profiling, bundle size analysis (tree-shaking, code splitting), edge function cold start reduction, and ISR/SSR performance tuning for Next.js applications.

## When to Activate

Activate this skill when the user:

- Has slow Vercel builds that need profiling and optimization
- Encounters deployment failures and needs build log analysis
- Wants to optimize edge function performance or reduce cold starts
- Needs Vercel configuration review (vercel.json, environment variables, headers)
- Uses phrases like "Vercel build slow", "deployment failed", "optimize edge functions"
- Is setting up CI/CD pipelines with Vercel for the first time

Do not activate for: general CI/CD without Vercel context (use `superclaude-devops`) or application performance without deployment focus (use `superclaude-performance`).

## Agents in This Wave

| Agent | Role | Focus |
|-------|------|-------|
| `devops-engineer` | Lead | Deployment pipelines, CI/CD, environment config, rollback strategies |
| `performance-engineer` | Specialist | Build profiling, bundle analysis, edge functions, cold starts |

Wave strategy: progressive | Synthesis: lead_agent | Model: Sonnet

## How to Call the Bridge

```
POST ${SUPERCLAUDE_BRIDGE_URL}/hooks/agent
Authorization: Bearer ${SUPERCLAUDE_BRIDGE_TOKEN}
Content-Type: application/json

{
  "message": "<the user's Vercel-related request, unmodified>",
  "agentId": "vercel",
  "model": "sonnet",
  "thinking": "medium",
  "deliver": true
}
```

## Output Structure

```
# Vercel Deployment Report

## Pipeline Analysis — devops-engineer
### Build Configuration Review
### Environment & Secrets Management
### Deployment Strategy Assessment
### CI/CD Integration

## Performance Profile — performance-engineer
### Build Step Profiling (time per step)
### Bundle Analysis (size, tree-shaking opportunities)
### Edge Function Metrics (cold start, execution time)
### Optimization Recommendations

## Recommended Next Steps
1. [Quick wins for build speed]
2. [Longer-term optimizations]
```

## Examples

**Example 1 — Build optimization:**

**User:** My Vercel build takes 4 minutes for a Next.js app. It used to be under 2 minutes.

**Response:** `performance-engineer` profiles build steps: TypeScript compilation (45s), Next.js bundling (90s), image optimization (60s), and identifies that the `@next/bundle-analyzer` shows 3 large dependencies pulled into the client bundle unnecessarily. `devops-engineer` recommends enabling Remote Caching with Turborepo, splitting the build into parallel steps, and pinning Node.js version to avoid re-installation.

**Example 2 — Deployment failure diagnosis:**

**User:** My latest Vercel deployment failed with "Error: Cannot find module 'sharp'". Here are the build logs.

**Response:** `devops-engineer` identifies the root cause: `sharp` requires native binaries that aren't available in Vercel's build environment (Linux x64), but the lockfile was generated on macOS (Darwin arm64). Recommends adding `sharp` to `optionalDependencies` and configuring `NEXT_SHARP_PATH` for Vercel's environment. `performance-engineer` additionally notes that image optimization can be offloaded to Vercel's built-in Image Optimization API, eliminating the `sharp` dependency entirely.

## Error Handling

If the bridge is unreachable:

> Bridge server is not responding. Start it with:
> `./scripts/openclaw/quickstart.sh` (Linux/macOS) or `.\scripts\openclaw\quickstart.ps1` (Windows)

If Vercel credentials are not configured:

> Vercel API access requires a VERCEL_TOKEN. Generate one at https://vercel.com/account/tokens and set it in the bridge environment.

If one specialist fails, findings from the other are presented with a note about the incomplete analysis.
