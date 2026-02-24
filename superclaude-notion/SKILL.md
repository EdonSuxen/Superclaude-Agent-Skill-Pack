---
name: superclaude-notion
version: 1.0.0
---

# SuperClaude Notion — Workspace Intelligence

Two specialists turn Notion workspaces into actionable insights. `document-intelligence-expert` handles content extraction — parsing page hierarchies, block structures, inline databases, and nested content into clean summaries with preserved relationships. `data-analyst-expert` handles the numbers — querying Notion databases for KPI tracking, sprint velocity, trend analysis, and custom reports with visualization recommendations.

## When to Activate

Activate this skill when the user:

- Wants to summarize or analyze Notion pages, databases, or workspaces
- Needs to extract action items, decisions, or key findings from Notion content
- Requests KPI dashboards or trend analysis from Notion databases
- Is migrating content from Notion or integrating it with other tools
- Uses phrases like "summarize my Notion", "analyze this database", "extract action items"
- References Notion URLs, page titles, or workspace names

Do not activate for: general document processing without Notion context (use `superclaude-document`) or standalone data analysis (use `superclaude-data`).

## Agents in This Wave

| Agent | Role | Focus |
|-------|------|-------|
| `document-intelligence-expert` | Lead | Page extraction, block parsing, content summarization, relationship mapping |
| `data-analyst-expert` | Specialist | Database queries, KPI tracking, trend analysis, sprint velocity |

Wave strategy: adaptive | Synthesis: consensus | Model: Opus

## How to Call the Bridge

```
POST ${SUPERCLAUDE_BRIDGE_URL}/hooks/agent
Authorization: Bearer ${SUPERCLAUDE_BRIDGE_TOKEN}
Content-Type: application/json

{
  "message": "<the user's Notion-related request, unmodified>",
  "agentId": "notion",
  "model": "opus",
  "thinking": "high",
  "deliver": true
}
```

## Output Structure

```
# Notion Workspace Report

## Content Analysis — document-intelligence-expert
### Page Summary
### Key Findings
### Action Items Extracted
### Content Structure Map

## Data Insights — data-analyst-expert
### KPI Dashboard
### Trend Analysis
### Velocity Metrics (if sprint data)

## Recommended Next Steps
1. [Immediate actions from findings]
2. [Workspace organization improvements]
```

## Examples

**Example 1 — Sprint database analysis:**

**User:** Analyze our sprint tracking database in Notion and show me velocity trends for the last 6 sprints.

**Response:** `data-analyst-expert` queries the sprint database: average velocity trending up from 21 to 34 story points, 2 sprints had scope creep (>15% increase mid-sprint), completion rate stabilized at 85%. `document-intelligence-expert` cross-references sprint retro pages, identifying that velocity improvements correlate with the introduction of story point estimation workshops in Sprint 4.

**Example 2 — Meeting notes extraction:**

**User:** Summarize all meeting notes from this month in Notion and extract the decisions made.

**Response:** `document-intelligence-expert` parses 12 meeting note pages, extracts 23 decisions (8 action items assigned, 5 blocked on external dependencies), and produces a decision log with owners and deadlines. `data-analyst-expert` identifies that 60% of decisions relate to the Q2 product roadmap, and 3 decisions contradict earlier ones — flags for review.

## Error Handling

If the bridge is unreachable:

> Bridge server is not responding. Start it with:
> `./scripts/openclaw/quickstart.sh` (Linux/macOS) or `.\scripts\openclaw\quickstart.ps1` (Windows)

If Notion API access is not configured:

> Notion API access requires a NOTION_API_TOKEN. Create an integration at https://www.notion.so/my-integrations and set the token in the bridge environment.

If one specialist fails, findings from the other are presented with a note about the incomplete analysis.
