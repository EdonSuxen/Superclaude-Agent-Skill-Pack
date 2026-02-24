---
name: superclaude-incident-commander
description: Production incident and crisis management specialist for outage response, severity classification, communication templates, postmortem facilitation, and runbook creation. Coordinates triage, identifies blast radius, drafts status page updates, and builds blameless postmortem documents. Activates on "production incident", "outage", "postmortem", "runbook", "incident response".
version: 1.0.0
tags: [superclaude, claude-code, incident-response, postmortem, runbook, outage-management, on-call, severity-classification, crisis-management, status-page]
category: developer-tools
metadata:
  openclaw:
    emoji: "🚨"
    os: [darwin, linux, win32]
    requires:
      bins: [node]
      env:
        - SUPERCLAUDE_BRIDGE_URL
        - SUPERCLAUDE_BRIDGE_TOKEN
      primaryEnv: SUPERCLAUDE_BRIDGE_TOKEN
    homepage: https://github.com/EdonSuxen/Superclaude-Agent-Skill-Pack
---

# SuperClaude Incident Commander — Outage Response & Postmortems

A production incident management specialist that restores service and prevents recurrence. Handles incident severity classification (SEV1-4), blast radius assessment, communication drafting (status page updates, stakeholder notifications), triage coordination, runbook creation for common failure modes, and blameless postmortem facilitation with action item tracking. Prioritizes service restoration speed over root cause completeness during active incidents.

## When to Activate

Activate this skill when the user:

- Is dealing with a production incident or outage and needs triage guidance
- Wants to write a postmortem document with timeline and action items
- Needs runbooks for common failure scenarios (database failover, deployment rollback)
- Is building incident response processes or on-call rotation design
- Uses phrases like "production incident", "outage", "postmortem", "runbook", "incident response"

## How to Call the Bridge

```
POST ${SUPERCLAUDE_BRIDGE_URL}/hooks/agent
Authorization: Bearer ${SUPERCLAUDE_BRIDGE_TOKEN}
Content-Type: application/json

{
  "message": "<the user's request, unmodified>",
  "agentId": "incident-commander",
  "model": "sonnet",
  "thinking": "medium",
  "deliver": true
}
```

## Output Structure

```
## Incident Management
### Severity & Impact (classification, blast radius, affected users)
### Response Playbook (immediate actions, escalation, communication)
### Timeline Reconstruction (events, decisions, resolution)
### Root Cause Analysis (contributing factors, 5 Whys)
### Action Items (prevention, detection, response improvements)
```

## Example

**User:** Our API started returning 500 errors 20 minutes ago. About 30% of requests are failing. We deployed a new version 2 hours ago. Write us an incident response plan and help draft the status page update.

**Response:** Classifies as SEV2 (partial service degradation, >10% error rate). Immediate actions: (1) check if rollback is safe — 2-hour deploy gap suggests yes, initiate `kubectl rollout undo` as parallel track while investigating, (2) check error logs for pattern — 500s starting 20min ago but deploy was 2h ago suggests delayed trigger (maybe traffic threshold, cron job, or cache expiry), (3) check dependent services (database connections, external APIs, Redis). Status page draft: "Investigating: Some API requests returning errors. Our team is actively investigating. No data loss. ETA for update: 30 minutes." Communication: notify engineering Slack, page on-call DBA if database-related. After resolution: schedule postmortem within 48h, template provided with timeline, 5 Whys, and action item categories (prevent/detect/respond).

## Error Handling

If the bridge is unreachable:

> Bridge server is not responding. Start it with:
> `./scripts/openclaw/quickstart.sh` (Linux/macOS) or `.\scripts\openclaw\quickstart.ps1` (Windows)
