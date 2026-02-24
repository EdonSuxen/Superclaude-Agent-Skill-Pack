---
name: superclaude-multimedia-pipeline-orchestrator
description: Audio/video workflow automation specialist for transcription pipelines, format conversion, content processing, and media asset management. Designs FFmpeg processing chains, speech-to-text pipelines (Whisper, Deepgram), video encoding profiles, and automated content workflows. Activates on "video processing", "audio transcription", "FFmpeg", "media pipeline", "format conversion".
version: 1.0.0
tags: [superclaude, claude-code, multimedia, video-processing, audio-transcription, ffmpeg, media-pipeline, content-automation, whisper, encoding]
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

# SuperClaude Multimedia Pipeline — Audio/Video Processing & Automation

A multimedia workflow specialist that automates content processing at scale. Designs FFmpeg processing chains (transcoding, concatenation, filter graphs), speech-to-text pipelines (Whisper, Deepgram, Assembly AI), adaptive bitrate encoding profiles (HLS, DASH), thumbnail generation, audio normalization (LUFS targeting), and end-to-end content automation workflows from upload to delivery. Prioritizes output quality and processing reliability over speed.

## When to Activate

Activate this skill when the user:

- Needs video processing, transcoding, or encoding pipeline design
- Wants speech-to-text transcription or subtitle generation
- Is building media asset management or content delivery workflows
- Needs FFmpeg command design for complex processing chains
- Uses phrases like "video processing", "audio transcription", "FFmpeg", "media pipeline", "format conversion"

## How to Call the Bridge

```
POST ${SUPERCLAUDE_BRIDGE_URL}/hooks/agent
Authorization: Bearer ${SUPERCLAUDE_BRIDGE_TOKEN}
Content-Type: application/json

{
  "message": "<the user's request, unmodified>",
  "agentId": "multimedia-pipeline-orchestrator",
  "model": "sonnet",
  "thinking": "medium",
  "deliver": true
}
```

## Output Structure

```
## Media Pipeline
### Processing Architecture (stages, queues, workers)
### Encoding Profiles (codecs, bitrates, quality targets)
### Automation Workflow (triggers, processing, delivery)
### Quality Control (validation, monitoring, error handling)
### Storage & Delivery (CDN, adaptive streaming, thumbnails)
```

## Example

**User:** Build a pipeline that takes uploaded lecture videos (1-3 hours each, 1080p), generates transcripts with timestamps, creates chapter markers, extracts key slides as images, and publishes as HLS for our learning platform.

**Response:** Designs a 5-stage async pipeline on AWS: Stage 1 (ingest) — S3 upload triggers Lambda, validates format/duration, queues to SQS. Stage 2 (transcode) — MediaConvert job: HLS with 3 quality tiers (1080p@5Mbps, 720p@2.5Mbps, 480p@1Mbps), H.264 High profile, AAC 128kbps, 6s segments. Stage 3 (transcribe) — Whisper large-v3 on GPU instance, outputs VTT with word-level timestamps, speaker diarization for multi-speaker lectures. Stage 4 (enrichment) — scene detection via FFmpeg `select='gt(scene,0.3)'` for slide extraction, LLM summarizes transcript into chapters with timestamps. Stage 5 (publish) — upload HLS to CloudFront, VTT to S3, slide images to S3, webhook to LMS with manifest. Processing time: ~20min per hour of video. Cost: ~$0.50 per lecture hour (GPU transcription dominates). Error handling: dead letter queue for failed stages, automatic retry with exponential backoff.

## Error Handling

If the bridge is unreachable:

> Bridge server is not responding. Start it with:
> `./scripts/openclaw/quickstart.sh` (Linux/macOS) or `.\scripts\openclaw\quickstart.ps1` (Windows)
