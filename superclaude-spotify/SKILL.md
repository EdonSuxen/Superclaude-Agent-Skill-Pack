---
name: superclaude-spotify
description: Spotify music intelligence using two specialists — multimedia-pipeline-orchestrator (audio feature analysis, playlist structure, track characteristics, BPM/key detection) and data-analyst-expert (listening trends, genre distribution, mood patterns, recommendation algorithms). Analyzes playlists, discovers patterns, and provides data-driven music recommendations. Activates on "analyze my playlist", "recommend music", "listening trends", "genre breakdown".
version: 1.0.0
tags: [superclaude, claude-code, spotify, music-intelligence, playlist-analysis, audio-features, genre-analysis, recommendations, listening-trends]
category: media
metadata:
  openclaw:
    emoji: "🎵"
    os: [darwin, linux, win32]
    requires:
      bins: [node]
      env:
        - SUPERCLAUDE_BRIDGE_URL
        - SUPERCLAUDE_BRIDGE_TOKEN
      primaryEnv: SUPERCLAUDE_BRIDGE_TOKEN
    homepage: https://github.com/EdonSuxen/Superclaude-Agent-Skill-Pack
---

# SuperClaude Spotify — Music Intelligence & Analysis

Two specialists turn listening data into insights. `multimedia-pipeline-orchestrator` handles audio analysis — extracting track characteristics (BPM, key, energy, danceability), playlist structure analysis, transition quality between tracks, and audio feature clustering. `data-analyst-expert` handles pattern discovery — genre distribution analysis, listening trend visualization, mood arc mapping, and data-driven recommendations based on audio feature similarity.

## When to Activate

Activate this skill when the user:

- Wants to analyze a playlist's genre mix, mood, or audio characteristics
- Needs music recommendations based on listening patterns or preferences
- Is building a playlist and wants optimization advice (flow, transitions, energy arc)
- Wants to understand their listening trends over time
- Uses phrases like "analyze my playlist", "recommend music like", "genre breakdown", "listening trends"
- References Spotify track, album, or playlist URLs

Do not activate for: audio/video processing pipelines without Spotify context (use the multimedia-pipeline-orchestrator agent directly).

## Agents in This Wave

| Agent | Role | Focus |
|-------|------|-------|
| `multimedia-pipeline-orchestrator` | Lead | Audio features, playlist structure, track characteristics, transitions |
| `data-analyst-expert` | Specialist | Genre distribution, listening trends, mood patterns, recommendations |

Wave strategy: adaptive | Synthesis: consensus | Model: Sonnet

## How to Call the Bridge

```
POST ${SUPERCLAUDE_BRIDGE_URL}/hooks/agent
Authorization: Bearer ${SUPERCLAUDE_BRIDGE_TOKEN}
Content-Type: application/json

{
  "message": "<the user's Spotify-related request, unmodified>",
  "agentId": "spotify",
  "model": "sonnet",
  "thinking": "medium",
  "deliver": true
}
```

## Output Structure

```
# Spotify Analysis Report

## Audio Analysis — multimedia-pipeline-orchestrator
### Track Characteristics (BPM, key, energy, valence)
### Playlist Structure (transitions, flow quality)
### Audio Feature Clusters

## Listening Insights — data-analyst-expert
### Genre Distribution
### Mood Arc Analysis
### Trend Patterns
### Recommendations

## Recommended Next Steps
1. [Playlist optimization suggestions]
2. [Discovery recommendations]
```

## Examples

**Example 1 — Playlist deep dive:**

**User:** Analyze my "Focus & Flow" playlist and tell me why some tracks break my concentration.

**Response:** `multimedia-pipeline-orchestrator` profiles all tracks: average BPM 112, energy 0.4-0.6, but 4 tracks spike to energy >0.8 with sudden key changes — these are the concentration breakers. `data-analyst-expert` identifies the playlist is 70% ambient electronica, 20% lo-fi hip hop, and 10% high-energy pop that disrupts the mood arc. Recommends replacing the 4 outliers with tracks matching the dominant audio profile.

**Example 2 — Discovery recommendations:**

**User:** I've been listening to a lot of jazz fusion and progressive rock lately. Find me something new in that space.

**Response:** `data-analyst-expert` identifies the audio signature: complex time signatures, high instrumentalness (>0.8), moderate energy with dynamic range. Clusters listening into 3 sub-genres: jazz-rock fusion (Snarky Puppy, Hiromi), math rock (Polyphia, Chon), and progressive metal (Animals as Leaders). `multimedia-pipeline-orchestrator` recommends 15 tracks across the 3 clusters, ordered by audio feature similarity to the user's most-played tracks.

## Error Handling

If the bridge is unreachable:

> Bridge server is not responding. Start it with:
> `./scripts/openclaw/quickstart.sh` (Linux/macOS) or `.\scripts\openclaw\quickstart.ps1` (Windows)

If Spotify credentials are not configured:

> Spotify API access requires SPOTIFY_CLIENT_ID and SPOTIFY_CLIENT_SECRET. Register an application at https://developer.spotify.com/dashboard and set the credentials in the bridge environment.

If one specialist fails, findings from the other are presented with a note about the incomplete analysis.
