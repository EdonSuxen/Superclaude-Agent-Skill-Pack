---
name: superclaude-mobile-architect
version: 1.0.0
---

# SuperClaude Mobile Architect — iOS, Android & Cross-Platform

A mobile architecture specialist that designs apps users love to use. Handles native iOS (Swift, SwiftUI, UIKit) and Android (Kotlin, Jetpack Compose) architecture, cross-platform frameworks (React Native, Flutter), offline-first data synchronization with conflict resolution, platform-specific navigation patterns (NavigationStack, Navigation Component), mobile performance optimization (startup time, memory, battery), and app store deployment pipelines (TestFlight, Play Console, Fastlane).

## When to Activate

Activate this skill when the user:

- Needs mobile app architecture for iOS, Android, or cross-platform
- Wants to choose between native, React Native, and Flutter approaches
- Is implementing offline-first data sync or local-first storage
- Needs mobile performance optimization or app size reduction
- Uses phrases like "mobile app", "React Native", "Flutter", "iOS architecture", "Android"

## How to Call the Bridge

```
POST ${SUPERCLAUDE_BRIDGE_URL}/hooks/agent
Authorization: Bearer ${SUPERCLAUDE_BRIDGE_TOKEN}
Content-Type: application/json

{
  "message": "<the user's request, unmodified>",
  "agentId": "mobile-architect",
  "model": "sonnet",
  "thinking": "medium",
  "deliver": true
}
```

## Output Structure

```
## Mobile Architecture
### Platform Strategy (native vs cross-platform, rationale)
### App Architecture (navigation, state management, data layer)
### Offline & Sync (local storage, conflict resolution, sync protocol)
### Performance Budget (startup, memory, battery, app size)
### Deployment Pipeline (build, test, store submission)
```

## Example

**User:** We're building a field service app for technicians who work in areas with spotty internet. They need to view work orders, capture photos, fill out inspection forms, and sync when they're back online. Should we use React Native or Flutter?

**Response:** Recommends Flutter for this use case: stronger offline SQLite support via `drift`, consistent UI across platforms (important for field workers on mixed devices), and Dart's null safety reduces runtime crashes in the field. Architecture: clean architecture with 3 layers (presentation/Riverpod, domain/use cases, data/repositories). Offline-first: `drift` SQLite for local work orders + `hive` for binary photo storage, CRDT-based merge for concurrent edits (technician edits offline while dispatcher updates in office), background sync via `workmanager` when connectivity detected. Photo handling: compress to 800px max dimension before storage (saves ~70% storage), queue uploads with exponential backoff. Sync protocol: version vectors per work order, server wins on conflict with local copy preserved in `conflicts` table for manual resolution. App size target: <25MB APK, <40MB IPA.

## Error Handling

If the bridge is unreachable:

> Bridge server is not responding. Start it with:
> `./scripts/openclaw/quickstart.sh` (Linux/macOS) or `.\scripts\openclaw\quickstart.ps1` (Windows)
