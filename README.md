<p align="center">
  <strong>Superclaude Agent Skill Pack</strong><br>
  <em>92 multi-agent skills for <a href="https://docs.openclaw.ai">OpenClaw</a> / <a href="https://clawhub.ai">ClawHub</a></em>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/skills-92-7c3aed?style=flat-square" alt="92 skills">
  <img src="https://img.shields.io/badge/agents-56-6366f1?style=flat-square" alt="56 agents">
  <img src="https://img.shields.io/badge/domain_packs-38-8b5cf6?style=flat-square" alt="38 domain packs">
  <img src="https://img.shields.io/badge/license-MIT-22c55e?style=flat-square" alt="MIT">
  <img src="https://img.shields.io/badge/pricing-free-10b981?style=flat-square" alt="Free">
  <img src="https://img.shields.io/badge/v1.0.0-stable-0ea5e9?style=flat-square" alt="v1.0.0">
</p>

---

## How It Works

```
You install a skill ──► OpenClaw activates it ──► Bridge routes to specialists ──► Parallel wave execution ──► Synthesized result
```

**Domain Packs** bundle 2–7 specialist agents for coordinated wave execution.
**Individual Agents** are single-specialist skills for focused tasks.

## Quick Start

```bash
# Install the core dispatcher (auto-routes to best agent)
clawhub install superclaude-core

# Or install a domain pack
clawhub install superclaude-code-review
clawhub install superclaude-security-audit
clawhub install superclaude-architecture
```

## Requirements

- [OpenClaw](https://docs.openclaw.ai) installed
- A running SuperClaude bridge server (self-hosted)
- `SUPERCLAUDE_BRIDGE_URL` — your bridge server URL
- `SUPERCLAUDE_BRIDGE_TOKEN` — shared authentication secret

---

## Browse by Category

| | Category | Skills | Jump |
|---|---|---|---|
| 🛠️ | Developer Tools | 46 | [View](#-developer-tools-46) |
| ☁️ | Cloud & Infra | 10 | [View](#%EF%B8%8F-cloud--infra-10) |
| 🎨 | Design | 8 | [View](#-design-8) |
| 📋 | Productivity | 7 | [View](#-productivity-7) |
| 📊 | Data | 6 | [View](#-data-6) |
| 🤖 | AI & ML | 5 | [View](#-ai--ml-5) |
| 🔒 | Security | 5 | [View](#-security-5) |
| 🔬 | Research | 3 | [View](#-research-3) |
| 🎬 | Media | 2 | [View](#-media-2) |

---

## 🛠️ Developer Tools (46)

<details>
<summary><strong>Domain Packs</strong> — multi-agent teams</summary>

&nbsp;

**SuperClaude Core** — Auto-routes any task to the best specialist from 56 agents.
```
clawhub install superclaude-core
```

**SuperClaude Code Review** — Three specialists in parallel: refactorer, QA, and security analyst.
```
clawhub install superclaude-code-review
```

**SuperClaude Architecture** — Architecture review using three expert architects.
```
clawhub install superclaude-architecture
```

**SuperClaude Debug** — Root cause analysis using two specialists.
```
clawhub install superclaude-debug
```

**SuperClaude Full Stack** — 7-agent enterprise wave for complex multi-domain tasks.
```
clawhub install superclaude-full-stack
```

**SuperClaude Refactor** — Evidence-based code quality improvement using two specialists.
```
clawhub install superclaude-refactor
```

**SuperClaude Testing** — Test pyramid strategy and quality engineering using two specialists.
```
clawhub install superclaude-testing
```

**SuperClaude Performance** — Performance optimization using two specialists.
```
clawhub install superclaude-performance
```

**SuperClaude API Design** — Contract-first API design using two specialists.
```
clawhub install superclaude-api-design
```

**SuperClaude Accessibility** — WCAG 2.2 auditing and inclusive design using two specialists.
```
clawhub install superclaude-accessibility
```

**SuperClaude Event Driven** — Event-driven architecture using two specialists.
```
clawhub install superclaude-event-driven
```

**SuperClaude Document** — Document processing and technical writing using two specialists.
```
clawhub install superclaude-document
```

**SuperClaude Game Dev** — Game development using two specialists.
```
clawhub install superclaude-game-dev
```

**SuperClaude IoT** — IoT and embedded systems using two specialists.
```
clawhub install superclaude-iot
```

**SuperClaude i18n** — Internationalization and localization.
```
clawhub install superclaude-i18n
```

**SuperClaude WASM** — WebAssembly development using two specialists.
```
clawhub install superclaude-wasm
```

**SuperClaude Web3** — Blockchain and decentralized application development.
```
clawhub install superclaude-web3
```

**SuperClaude Systems Programming** — High-performance systems using two specialists.
```
clawhub install superclaude-systems-programming
```

**SuperClaude Sustainability** — Green technology and sustainable software engineering.
```
clawhub install superclaude-sustainability
```

</details>

<details>
<summary><strong>Individual Agents</strong> — single specialists</summary>

&nbsp;

| Agent | Specialty |
|---|---|
| `superclaude-architect` | C4 modeling, ADRs, trade-off analysis |
| `superclaude-backend-architect` | Server-side architecture, microservices, API patterns |
| `superclaude-api-architect` | REST, GraphQL, gRPC design and governance |
| `superclaude-frontend-architecture-specialist` | React, Next.js, RSC vs client components |
| `superclaude-mobile-architect` | Native and cross-platform mobile architecture |
| `superclaude-event-driven-architect` | Kafka, RabbitMQ, event sourcing, CQRS |
| `superclaude-analyzer` | Evidence-based root cause investigation |
| `superclaude-refactorer` | Code quality and technical debt management |
| `superclaude-performance-engineer` | Bottleneck identification and profiling |
| `superclaude-testing-strategist` | Test pyramid, mutation testing, strategy |
| `superclaude-qa` | Test automation, quality gates, defect management |
| `superclaude-devops-engineer` | CI/CD automation and infrastructure deployment |
| `superclaude-platform-engineer` | Developer experience and internal platforms |
| `superclaude-observability-engineer` | Monitoring, logging, tracing, visibility |
| `superclaude-incident-commander` | Production incident and crisis management |
| `superclaude-accessibility-champion` | WCAG 2.2 and inclusive design |
| `superclaude-conversational-ux-optimizer` | Chatbot and voice UI design |
| `superclaude-embedded-systems-engineer` | RTOS, bare-metal, hardware interfacing |
| `superclaude-game-development-specialist` | Unity/Unreal, real-time graphics |
| `superclaude-rust-systems-engineer` | High-performance Rust systems programming |
| `superclaude-webassembly-specialist` | WASM, WASI, cross-platform compilation |
| `superclaude-blockchain-web3-specialist` | Smart contract security, DeFi, NFTs |
| `superclaude-green-tech-sustainability-expert` | Carbon measurement, energy-efficient architecture |
| `superclaude-localization-internationalization-expert` | i18n/l10n, RTL support, ICU/CLDR |
| `superclaude-prompt-architect` | Requirements discovery and structuring |
| `superclaude-mentor` | Knowledge transfer and education |
| `superclaude-scribe` | Technical writing and documentation |

</details>

---

## ☁️ Cloud & Infra (10)

<details>
<summary><strong>Domain Packs</strong></summary>

&nbsp;

**SuperClaude Cloud Infra** — Cloud infrastructure and Kubernetes engineering using two specialists.
```
clawhub install superclaude-cloud-infra
```

**SuperClaude DevOps** — CI/CD pipeline engineering and platform operations using two specialists.
```
clawhub install superclaude-devops
```

**SuperClaude SRE** — Site reliability engineering using three specialists.
```
clawhub install superclaude-sre
```

**SuperClaude Observability** — Observability and reliability engineering using two specialists.
```
clawhub install superclaude-observability
```

**SuperClaude Incident Response** — Incident management using two specialists.
```
clawhub install superclaude-incident-response
```

**SuperClaude Vercel** — Vercel deployment intelligence using two specialists.
```
clawhub install superclaude-vercel
```

</details>

<details>
<summary><strong>Individual Agents</strong></summary>

&nbsp;

| Agent | Specialty |
|---|---|
| `superclaude-cloud-native-architect` | Kubernetes orchestration, multi-cloud, service mesh |
| `superclaude-edge-computing-specialist` | Ultra-low latency, IoT, real-time processing |
| `superclaude-finops-specialist` | Cloud cost optimization, resource rightsizing |
| `superclaude-sre-chaos-engineer` | SLO/SLI, chaos experiments, disaster recovery |

</details>

---

## 🎨 Design (8)

<details>
<summary><strong>Domain Packs</strong></summary>

&nbsp;

**SuperClaude Creative** — Creative design using three specialists.
```
clawhub install superclaude-creative
```

**SuperClaude Design** — UX and visual design using two specialists.
```
clawhub install superclaude-design
```

</details>

<details>
<summary><strong>Individual Agents</strong></summary>

&nbsp;

| Agent | Specialty |
|---|---|
| `superclaude-digital-experience-designer` | UX research, WCAG 2.2, interaction design |
| `superclaude-visual-communication-architect` | Brand identity, logo systems, typography, data viz |
| `superclaude-motion-media-specialist` | Motion graphics, sound design, game design |
| `superclaude-spatial-experience-architect` | Spatial design, experiential installations |
| `superclaude-product-material-designer` | Industrial design, materials, fashion |
| `superclaude-systems-innovation-strategist` | Strategic design, service design, AI-assisted design |

</details>

---

## 📋 Productivity (7)

<details>
<summary><strong>Domain Packs</strong></summary>

&nbsp;

**SuperClaude Product** — Product strategy using two specialists.
```
clawhub install superclaude-product
```

**SuperClaude Growth** — Growth strategy using two specialists.
```
clawhub install superclaude-growth
```

**SuperClaude Notion** — Notion workspace intelligence using two specialists.
```
clawhub install superclaude-notion
```

</details>

<details>
<summary><strong>Individual Agents</strong></summary>

&nbsp;

| Agent | Specialty |
|---|---|
| `superclaude-product-manager` | Product strategy, roadmaps, PRDs, user stories |
| `superclaude-project-manager-orchestrator` | Agile PM, sprint planning, team velocity |
| `superclaude-business-strategy-expert` | Strategic planning, market analysis, GTM |
| `superclaude-growth-marketing-strategist` | Growth hacking, campaigns, A/B testing |

</details>

---

## 📊 Data (6)

<details>
<summary><strong>Domain Packs</strong></summary>

&nbsp;

**SuperClaude Data** — Data analytics and pipeline engineering using two specialists.
```
clawhub install superclaude-data
```

**SuperClaude Database** — Database design and migration planning using two specialists.
```
clawhub install superclaude-database
```

</details>

<details>
<summary><strong>Individual Agents</strong></summary>

&nbsp;

| Agent | Specialty |
|---|---|
| `superclaude-database-architect` | Schema design, query optimization, migrations |
| `superclaude-data-analyst-expert` | SQL analytics, BI dashboards, visualization |
| `superclaude-data-pipeline-engineer` | ETL/ELT orchestration, Airflow, dbt, Kafka |
| `superclaude-document-intelligence-expert` | OCR, NLP, contract analysis, document processing |

</details>

---

## 🤖 AI & ML (5)

<details>
<summary><strong>Domain Packs</strong></summary>

&nbsp;

**SuperClaude AI** — AI and ML engineering using two specialists.
```
clawhub install superclaude-ai
```

**SuperClaude ML Ops** — MLOps and feature engineering using two specialists.
```
clawhub install superclaude-ml-ops
```

</details>

<details>
<summary><strong>Individual Agents</strong></summary>

&nbsp;

| Agent | Specialty |
|---|---|
| `superclaude-ai-ml-engineer` | Model training, deployment, LLM integration |
| `superclaude-ai-agent-orchestrator` | Multi-agent coordination, RAG, tool orchestration |
| `superclaude-meta-orchestrator` | Complex task decomposition, wave coordination |

</details>

---

## 🔒 Security (5)

<details>
<summary><strong>Domain Packs</strong></summary>

&nbsp;

**SuperClaude Security Audit** — Three security specialists: threat modeling, DevSecOps, compliance.
```
clawhub install superclaude-security-audit
```

**SuperClaude Compliance** — Regulatory compliance and audit preparation using two specialists.
```
clawhub install superclaude-compliance
```

</details>

<details>
<summary><strong>Individual Agents</strong></summary>

&nbsp;

| Agent | Specialty |
|---|---|
| `superclaude-security` | OWASP, STRIDE, threat modeling, vulnerability assessment |
| `superclaude-devsecops-automation-engineer` | SAST, DAST, dependency scanning, shift-left security |
| `superclaude-compliance-auditor` | GDPR, SOC 2, HIPAA, PCI-DSS, audit readiness |

</details>

---

## 🔬 Research (3)

<details>
<summary><strong>Domain Packs</strong></summary>

&nbsp;

**SuperClaude Research** — Deep research and evidence synthesis using two specialists.
```
clawhub install superclaude-research
```

</details>

<details>
<summary><strong>Individual Agents</strong></summary>

&nbsp;

| Agent | Specialty |
|---|---|
| `superclaude-research-analyst` | Market research, literature reviews, fact-checking |
| `superclaude-quantum-computing-researcher` | NISQ algorithms, quantum circuit design, Qiskit/Cirq |

</details>

---

## 🎬 Media (2)

<details>
<summary><strong>All Skills</strong></summary>

&nbsp;

**SuperClaude Spotify** — Spotify music intelligence using two specialists.
```
clawhub install superclaude-spotify
```

| Agent | Specialty |
|---|---|
| `superclaude-multimedia-pipeline-orchestrator` | Audio/video workflow automation |

</details>

---

## Choosing: Pack vs Agent

```
Need coordinated multi-expert analysis?  ──►  Use a Domain Pack
Need one focused specialist?              ──►  Use an Individual Agent
Not sure what you need?                   ──►  Install superclaude-core (auto-routes)
```

| | Domain Pack | Individual Agent |
|---|---|---|
| **Agents** | 2–7 in parallel | 1 |
| **Best for** | Complex, multi-faceted tasks | Focused, single-domain tasks |
| **Example** | `superclaude-security-audit` (3 agents) | `superclaude-security` (1 agent) |

## Skill Structure

Each skill directory contains:

```
superclaude-<name>/
  SKILL.md        # Skill definition (frontmatter + instructions)
  clawhub.json    # ClawHub marketplace metadata
```

## License

MIT
