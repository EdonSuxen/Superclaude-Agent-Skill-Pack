---
name: superclaude-data
version: 1.0.0
---

# SuperClaude Data — Analytics & Pipeline Engineering

Two specialists bridge the gap between business questions and data infrastructure. `data-analyst-expert` transforms raw data into actionable insights — SQL query optimization, statistical analysis, KPI definition, and dashboard design. `data-pipeline-engineer` builds the infrastructure that makes those insights reliable and repeatable — ETL/ELT orchestration with Airflow or Prefect, dbt transformations, data quality checks, and streaming pipelines with Kafka or Flink. Together they produce answers you can trust and pipelines that keep those answers fresh.

## When to Activate

Activate this skill when the user:

- Needs to analyze data and extract business insights
- Wants to build or optimize a data pipeline (ETL, ELT, streaming)
- Is designing KPI dashboards or business intelligence reports
- Needs data quality validation or anomaly detection
- Uses phrases like "analyze this data", "build a dashboard", "data pipeline", "ETL workflow"
- Is setting up dbt models, Airflow DAGs, or data warehouse architecture

Do not activate for: ML model training (use `superclaude-ai`) or database schema design (use `superclaude-database`).

## Agents in This Wave

| Agent | Role | Focus |
|-------|------|-------|
| `data-analyst-expert` | Lead | SQL analytics, statistical analysis, KPI dashboards, data visualization |
| `data-pipeline-engineer` | Specialist | ETL/ELT orchestration, Airflow/dbt, data quality, streaming |

Wave strategy: progressive | Synthesis: lead_agent | Model: Sonnet

## How to Call the Bridge

```
POST ${SUPERCLAUDE_BRIDGE_URL}/hooks/agent
Authorization: Bearer ${SUPERCLAUDE_BRIDGE_TOKEN}
Content-Type: application/json

{
  "message": "<the user's request, unmodified>",
  "agentId": "data",
  "model": "sonnet",
  "thinking": "medium",
  "deliver": true
}
```

## Output Structure

```
# Data Report

## Analytical Insights — data-analyst-expert
### Key Findings
### SQL Queries & Analysis
### Visualization Recommendations
### KPI Definitions

## Pipeline Design — data-pipeline-engineer
### Data Flow Architecture
### Transformation Logic (dbt/SQL)
### Orchestration (Airflow DAG)
### Data Quality Checks

## Recommended Next Steps
1. [Quick wins from analysis]
2. [Pipeline improvements]
```

## Examples

**Example 1 — Customer churn analysis:**

**User:** Analyze our customer data to understand churn patterns and build a daily dashboard.

**Response:** `data-analyst-expert` writes cohort analysis SQL, identifies churn correlates (first 7-day engagement, support tickets), and designs a retention dashboard with leading indicators. `data-pipeline-engineer` builds the dbt models for cohort calculation and an Airflow DAG that refreshes the dashboard daily at 6 AM UTC.

**Example 2 — Data pipeline modernization:**

**User:** Our nightly ETL job takes 6 hours and often fails. Help us fix it.

**Response:** `data-pipeline-engineer` profiles the pipeline, identifies 3 bottlenecks (full table scans, no incremental loads, serial execution), and redesigns with incremental dbt models and parallel Airflow tasks. `data-analyst-expert` validates the output data quality matches the original pipeline with reconciliation queries.

## Error Handling

If the bridge is unreachable:

> Bridge server is not responding. Start it with:
> `./scripts/openclaw/quickstart.sh` (Linux/macOS) or `.\scripts\openclaw\quickstart.ps1` (Windows)

If one specialist fails, findings from the other are presented with a note about the incomplete analysis.
