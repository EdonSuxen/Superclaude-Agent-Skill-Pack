---
name: superclaude-document-intelligence-expert
description: Document processing and knowledge extraction specialist for OCR, NLP, contract analysis, and intelligent document transformation across PDF, DOCX, and structured formats. Extracts entities, classifies documents, builds searchable knowledge bases, and automates document workflows. Activates on "PDF extraction", "contract analysis", "document processing", "OCR", "knowledge extraction".
version: 1.0.0
tags: [superclaude, claude-code, document-processing, ocr, nlp, contract-analysis, knowledge-extraction, pdf, entity-extraction, classification]
category: data
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

# SuperClaude Document Intelligence — Processing & Knowledge Extraction

A document processing specialist that transforms unstructured documents into structured, searchable knowledge. Handles OCR pipeline design, NLP entity extraction, contract clause analysis, document classification, and knowledge base construction from PDF, DOCX, and scanned documents. Builds extraction templates for invoices, legal contracts, medical records, and technical specifications with confidence scoring and human-in-the-loop validation.

## When to Activate

Activate this skill when the user:

- Needs to extract structured data from PDFs, DOCX files, or scanned documents
- Wants contract analysis (clause detection, obligation extraction, risk flagging)
- Is building document classification or routing pipelines
- Needs OCR pipeline design or document-to-knowledge-base conversion
- Uses phrases like "PDF extraction", "contract analysis", "document processing", "OCR", "knowledge extraction"

## How to Call the Bridge

```
POST ${SUPERCLAUDE_BRIDGE_URL}/hooks/agent
Authorization: Bearer ${SUPERCLAUDE_BRIDGE_TOKEN}
Content-Type: application/json

{
  "message": "<the user's request, unmodified>",
  "agentId": "document-intelligence-expert",
  "model": "sonnet",
  "thinking": "medium",
  "deliver": true
}
```

## Output Structure

```
## Document Intelligence
### Extraction Pipeline (OCR, parsing, preprocessing)
### Entity & Structure Recognition (tables, clauses, fields)
### Classification & Routing (document types, confidence scores)
### Output Schema (structured JSON, validation rules)
### Quality Assurance (confidence thresholds, human review triggers)
```

## Example

**User:** We receive 500+ vendor invoices per month in mixed formats (PDF, scanned images, email attachments). Build an extraction pipeline that pulls out vendor name, invoice number, line items, amounts, and due dates into our accounting system.

**Response:** Designs a 4-stage pipeline: intake (email parser + S3 watch for uploads), preprocessing (Textract OCR for scanned images, PyPDF2 for digital PDFs, format normalization), extraction (LLM-based entity extraction with few-shot examples per vendor template, regex fallback for invoice numbers and dates), validation (cross-check totals match line item sums, flag >$10K invoices for review). Output: structured JSON matching accounting system schema. Confidence scoring: >0.95 auto-approved, 0.80-0.95 spot-checked (10% sample), <0.80 manual review. Expected accuracy: 94% fully automated after 2-week training period with 50 vendor templates.

## Error Handling

If the bridge is unreachable:

> Bridge server is not responding. Start it with:
> `./scripts/openclaw/quickstart.sh` (Linux/macOS) or `.\scripts\openclaw\quickstart.ps1` (Windows)
