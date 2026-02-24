---
name: superclaude-ml-ops
version: 1.0.0
---

# SuperClaude MLOps — ML Platform & Feature Engineering

Two specialists build the infrastructure that makes ML models production-ready. `ai-ml-engineer` handles the model lifecycle — experiment tracking (MLflow, W&B), model registry, training pipeline automation, serving infrastructure (TorchServe, Triton, vLLM), A/B testing, and model drift detection. `data-pipeline-engineer` builds the data foundation — feature stores (Feast, Tecton), training data ETL pipelines, data versioning (DVC), Airflow DAG orchestration, and data quality validation. Together they produce ML platforms where models are reproducible, deployable, and monitorable.

## When to Activate

Activate this skill when the user:

- Needs to set up MLOps infrastructure (experiment tracking, model registry)
- Wants to deploy ML models to production (serving, scaling, A/B testing)
- Is building feature stores or training data pipelines
- Needs model monitoring and drift detection
- Uses phrases like "MLOps pipeline", "model deployment", "feature store", "model monitoring"
- Has reproducibility issues with ML experiments or training runs

Do not activate for: model training/architecture design (use `superclaude-ai`) or general data analytics (use `superclaude-data`).

## Agents in This Wave

| Agent | Role | Focus |
|-------|------|-------|
| `ai-ml-engineer` | Lead | Experiment tracking, model registry, serving, drift detection |
| `data-pipeline-engineer` | Specialist | Feature stores, training data ETL, Airflow, data versioning |

Wave strategy: enterprise | Synthesis: consensus | Model: Opus

## How to Call the Bridge

```
POST ${SUPERCLAUDE_BRIDGE_URL}/hooks/agent
Authorization: Bearer ${SUPERCLAUDE_BRIDGE_TOKEN}
Content-Type: application/json

{
  "message": "<the user's request, unmodified>",
  "agentId": "ml-ops",
  "model": "opus",
  "thinking": "high",
  "deliver": true
}
```

## Output Structure

```
# MLOps Platform Report

## Model Lifecycle — ai-ml-engineer
### Experiment Tracking Setup
### Model Registry Configuration
### Serving Infrastructure
### Monitoring & Drift Detection

## Data Infrastructure — data-pipeline-engineer
### Feature Store Design
### Training Data Pipeline
### Data Versioning Strategy
### Orchestration (Airflow DAGs)

## Recommended Next Steps
1. [Infrastructure provisioning order]
2. [First model to onboard]
```

## Examples

**Example 1 — ML platform from scratch:**

**User:** Set up an MLOps platform for our team of 5 ML engineers.

**Response:** `ai-ml-engineer` designs the platform: MLflow for experiment tracking, model registry with approval gates, Triton Inference Server for GPU serving, and Evidently AI for drift monitoring. `data-pipeline-engineer` builds the data layer: Feast feature store backed by Redis (online) and BigQuery (offline), DVC for dataset versioning, and Airflow DAGs for daily feature materialization.

**Example 2 — Model serving at scale:**

**User:** Our recommendation model needs to serve 10K requests/second with <50ms latency.

**Response:** `ai-ml-engineer` designs the serving stack: model distillation for latency, ONNX Runtime for inference, horizontal autoscaling with request batching, and shadow deployment for safe rollouts. `data-pipeline-engineer` builds the real-time feature pipeline: Kafka → Flink for streaming features, Redis for online feature serving, and feature freshness monitoring.

## Error Handling

If the bridge is unreachable:

> Bridge server is not responding. Start it with:
> `./scripts/openclaw/quickstart.sh` (Linux/macOS) or `.\scripts\openclaw\quickstart.ps1` (Windows)

If one specialist fails, findings from the other are presented with a note about the incomplete analysis.
