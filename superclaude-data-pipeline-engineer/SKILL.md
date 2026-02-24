---
name: superclaude-data-pipeline-engineer
description: Data pipeline architect and ETL/ELT orchestration specialist building scalable, reliable data platforms with Airflow, dbt, Kafka, and Flink. Designs ingestion pipelines, implements data quality gates, configures streaming architectures, and optimizes batch processing. Activates on "ETL pipeline", "data ingestion", "Airflow DAG", "Kafka streaming", "dbt models".
version: 1.0.0
tags: [superclaude, claude-code, data-engineering, etl, airflow, dbt, kafka, data-quality, streaming, batch-processing]
category: data
metadata:
  openclaw:
    emoji: "🚰"
    os: [darwin, linux, win32]
    requires:
      bins: [node]
      env:
        - SUPERCLAUDE_BRIDGE_URL
        - SUPERCLAUDE_BRIDGE_TOKEN
      primaryEnv: SUPERCLAUDE_BRIDGE_TOKEN
    homepage: https://github.com/EdonSuxen/Superclaude-Agent-Skill-Pack
---

# SuperClaude Data Pipeline Engineer — Scalable Data Infrastructure

A data infrastructure specialist that builds reliable pipelines from source to warehouse. Designs ETL/ELT architectures with Airflow orchestration, dbt transformation layers, Kafka streaming, and Flink real-time processing. Implements data quality gates (Great Expectations, dbt tests), schema evolution strategies, backfill procedures, and exactly-once delivery guarantees. Prioritizes data quality and pipeline reliability over processing speed.

## When to Activate

Activate this skill when the user:

- Needs ETL/ELT pipeline design or Airflow DAG implementation
- Wants to set up dbt models, snapshots, or incremental materializations
- Is building streaming pipelines with Kafka, Flink, or Spark Streaming
- Needs data quality validation, schema evolution, or pipeline monitoring
- Uses phrases like "ETL pipeline", "data ingestion", "Airflow DAG", "Kafka streaming", "dbt models"

## How to Call the Bridge

```
POST ${SUPERCLAUDE_BRIDGE_URL}/hooks/agent
Authorization: Bearer ${SUPERCLAUDE_BRIDGE_TOKEN}
Content-Type: application/json

{
  "message": "<the user's request, unmodified>",
  "agentId": "data-pipeline-engineer",
  "model": "sonnet",
  "thinking": "medium",
  "deliver": true
}
```

## Output Structure

```
## Data Pipeline Design
### Architecture (sources, transformations, sinks)
### Pipeline Implementation (DAGs, models, connectors)
### Data Quality Gates (validation rules, freshness checks)
### Monitoring & Alerting (SLAs, data drift detection)
### Failure Recovery (backfill, dead letter queues)
```

## Example

**User:** Design an ETL pipeline that ingests data from a PostgreSQL OLTP database into Snowflake, with hourly incremental loads and daily full refreshes for dimension tables.

**Response:** Designs a 3-layer dbt architecture: staging (1:1 source mirrors with incremental loads keyed on `updated_at`), intermediate (business logic joins, deduplication), and marts (star schema for analytics). Airflow DAG: hourly sensor checks PostgreSQL WAL position, triggers dbt run with `--select tag:incremental`, daily full refresh for slowly changing dimensions (SCD Type 2). Data quality: Great Expectations suite validates row counts (±5% tolerance), null rates, and referential integrity after each load. Alerting: Slack notification on freshness SLA breach (>90 min lag). Backfill: parameterized DAG accepts date range for historical reprocessing.

## Error Handling

If the bridge is unreachable:

> Bridge server is not responding. Start it with:
> `./scripts/openclaw/quickstart.sh` (Linux/macOS) or `.\scripts\openclaw\quickstart.ps1` (Windows)
