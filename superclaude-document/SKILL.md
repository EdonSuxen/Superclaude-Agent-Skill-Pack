---
name: superclaude-document
description: Document processing and technical writing using two specialists — document-intelligence-expert (OCR, NLP, contract analysis, knowledge extraction from PDF/DOCX) and scribe (technical writing, READMEs, API docs, user guides). Extracts knowledge from existing documents and produces audience-ready documentation. Activates on "write documentation", "analyze this document", "extract from PDF", "README for this project".
version: 1.0.0
tags: [superclaude, claude-code, documentation, technical-writing, knowledge-extraction, pdf, readme, api-docs, user-guide, nlp]
category: developer-tools
metadata:
  openclaw:
    emoji: "📄"
    os: [darwin, linux, win32]
    requires:
      bins: [node]
      env:
        - SUPERCLAUDE_BRIDGE_URL
        - SUPERCLAUDE_BRIDGE_TOKEN
      primaryEnv: SUPERCLAUDE_BRIDGE_TOKEN
    homepage: https://github.com/EdonSuxen/Superclaude-Agent-Skill-Pack
---

# SuperClaude Document — Knowledge Extraction & Technical Writing

Two specialists handle the full document lifecycle. `document-intelligence-expert` extracts structured knowledge from unstructured sources — PDFs, contracts, DOCX files, code comments, and scattered wikis. `scribe` transforms that extracted knowledge into polished, audience-appropriate documentation — READMEs, API references, user guides, architecture decision records, and onboarding materials. Together they turn messy information into clear, maintainable documentation.

## When to Activate

Activate this skill when the user:

- Needs documentation written for a codebase, API, or feature
- Wants to extract structured information from PDFs, contracts, or legacy docs
- Is creating a README, user guide, or API reference
- Needs to analyze and summarize technical documents
- Uses phrases like "write documentation", "analyze this document", "extract from PDF", "README"
- Wants to convert scattered knowledge into organized documentation

Do not activate for: code explanation without documentation output (use `superclaude-mentor`) or research synthesis (use `superclaude-research`).

## Agents in This Wave

| Agent | Role | Focus |
|-------|------|-------|
| `document-intelligence-expert` | Lead | OCR, NLP, contract analysis, knowledge extraction, structured output |
| `scribe` | Specialist | Technical writing, README structure, API docs, audience adaptation |

Wave strategy: progressive | Synthesis: lead_agent | Model: Sonnet

## How to Call the Bridge

```
POST ${SUPERCLAUDE_BRIDGE_URL}/hooks/agent
Authorization: Bearer ${SUPERCLAUDE_BRIDGE_TOKEN}
Content-Type: application/json

{
  "message": "<the user's request, unmodified>",
  "agentId": "document",
  "model": "sonnet",
  "thinking": "medium",
  "deliver": true
}
```

## Output Structure

```
# Documentation Report

## Knowledge Extraction — document-intelligence-expert
### Source Analysis
### Key Entities & Relationships
### Structured Data Output

## Documentation — scribe
### Generated Documentation
### Style & Audience Notes
### Maintenance Recommendations

## Recommended Next Steps
1. [Review and publish locations]
2. [Follow-up documentation needs]
```

## Examples

**Example 1 — Project README:**

**User:** Write a comprehensive README for this TypeScript monorepo.

**Response:** `document-intelligence-expert` scans package.json files, entry points, test configs, and CI files to extract project structure, dependencies, and scripts. `scribe` produces a README with badges, installation guide, architecture overview, usage examples, contributing guidelines, and license section.

**Example 2 — Contract analysis:**

**User:** Extract the key terms from these 5 vendor contracts (PDFs).

**Response:** `document-intelligence-expert` parses the PDFs, extracts parties, obligations, termination clauses, SLAs, pricing terms, and renewal conditions into a structured comparison table. `scribe` writes an executive summary highlighting risks and differences across vendors.

## Error Handling

If the bridge is unreachable:

> Bridge server is not responding. Start it with:
> `./scripts/openclaw/quickstart.sh` (Linux/macOS) or `.\scripts\openclaw\quickstart.ps1` (Windows)

If one specialist fails, findings from the other are presented with a note about the incomplete analysis.
