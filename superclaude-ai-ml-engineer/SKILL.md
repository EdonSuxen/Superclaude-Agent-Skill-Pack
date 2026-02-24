---
name: superclaude-ai-ml-engineer
version: 1.0.0
---

# SuperClaude AI/ML Engineer — Model Training & Deployment

A full-lifecycle ML engineering specialist covering data preparation, feature engineering, model training, experiment tracking (MLflow/W&B), hyperparameter optimization, LLM fine-tuning (LoRA/QLoRA), inference optimization (quantization, batching, caching), and production deployment with monitoring for drift and bias. Applies responsible AI practices throughout — fairness metrics, explainability, and data governance.

## When to Activate

Activate this skill when the user:

- Needs to design or optimize a model training pipeline
- Wants to fine-tune an LLM for a specific task (classification, extraction, generation)
- Is setting up MLOps infrastructure (experiment tracking, model registry, CI/CD for ML)
- Needs inference optimization (latency, throughput, cost reduction)
- Uses phrases like "train a model", "MLOps", "fine-tune", "model deployment", "feature engineering"

## How to Call the Bridge

```
POST ${SUPERCLAUDE_BRIDGE_URL}/hooks/agent
Authorization: Bearer ${SUPERCLAUDE_BRIDGE_TOKEN}
Content-Type: application/json

{
  "message": "<the user's request, unmodified>",
  "agentId": "ai-ml-engineer",
  "model": "opus",
  "thinking": "high",
  "deliver": true
}
```

## Output Structure

```
## ML Engineering Report
### Data Pipeline (preparation, feature engineering)
### Model Architecture (selection rationale, hyperparameters)
### Training Strategy (hardware, distributed training, experiment tracking)
### Evaluation (metrics, validation strategy, bias checks)
### Deployment Plan (serving infrastructure, monitoring)
### Responsible AI Checklist
```

## Example

**User:** I want to fine-tune Llama 3.1 8B to classify customer support tickets into 12 categories. We have 50K labeled examples.

**Response:** Recommends QLoRA fine-tuning (4-bit quantization, rank 16) on a single A100 — estimated 4 hours training, $12 compute cost. Data strategy: 80/10/10 split, stratified by category, with augmentation for the 3 underrepresented categories. Training config: learning rate 2e-4, cosine schedule, 3 epochs with early stopping on validation F1. Evaluation: per-category F1, confusion matrix for commonly confused pairs, calibration curve. Deployment: vLLM serving with continuous batching, expected 150ms P99 latency at 100 RPS. Monitoring: drift detection on input distribution, weekly accuracy sampling.

## Error Handling

If the bridge is unreachable:

> Bridge server is not responding. Start it with:
> `./scripts/openclaw/quickstart.sh` (Linux/macOS) or `.\scripts\openclaw\quickstart.ps1` (Windows)
