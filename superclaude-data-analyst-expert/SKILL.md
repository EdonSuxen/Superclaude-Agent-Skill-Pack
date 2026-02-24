---
name: superclaude-data-analyst-expert
version: 1.0.0
---

# SuperClaude Data Analyst — Insights & Visualization

An expert data analyst that turns raw data into decisions. Writes optimized SQL queries (CTEs, window functions, pivots), designs BI dashboards with clear KPI hierarchies, creates data visualization specifications (chart type selection, axis design, color encoding), performs statistical analysis (hypothesis testing, regression, cohort analysis), and identifies actionable trends in datasets.

## When to Activate

Activate this skill when the user:

- Needs SQL queries for analytics or reporting
- Wants to design a BI dashboard or KPI framework
- Has data that needs visualization recommendations
- Needs statistical analysis (A/B test results, cohort analysis, trend identification)
- Uses phrases like "SQL query", "dashboard design", "analyze this data", "KPI tracking"

## How to Call the Bridge

```
POST ${SUPERCLAUDE_BRIDGE_URL}/hooks/agent
Authorization: Bearer ${SUPERCLAUDE_BRIDGE_TOKEN}
Content-Type: application/json

{
  "message": "<the user's request, unmodified>",
  "agentId": "data-analyst-expert",
  "model": "sonnet",
  "thinking": "medium",
  "deliver": true
}
```

## Output Structure

```
## Data Analysis
### Query / Methodology
### Key Findings (with confidence levels)
### Visualization Recommendations
### Actionable Insights
### Follow-up Analysis Suggestions
```

## Example

**User:** Write a SQL query to calculate monthly retention cohorts for our SaaS product. We have a `users` table and an `events` table with timestamps.

**Response:** Provides a CTE-based cohort analysis query: first CTE identifies signup month per user, second CTE pivots activity months, third calculates retention percentages. Includes visualization recommendation: retention heatmap with months on x-axis, cohorts on y-axis, color encoding retention rate (green >80%, yellow 40-80%, red <40%). Identifies insight: retention drops 15% between month 1 and month 2 across all cohorts — suggests onboarding flow investigation. Follow-up: recommends segmenting by acquisition channel and plan tier.

## Error Handling

If the bridge is unreachable:

> Bridge server is not responding. Start it with:
> `./scripts/openclaw/quickstart.sh` (Linux/macOS) or `.\scripts\openclaw\quickstart.ps1` (Windows)
