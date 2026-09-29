# Datasets Overview

This document describes the document-parsing datasets and test data located in the project root directory, including their sources and purposes.

## Summary

| Directory | Type | Purpose |
|-----------|------|---------|
| `docling/` | Test fixtures | Regression tests for the Docling parser |
| `OmniDocBench/` | Gold-standard benchmark | Layout analysis + end-to-end parsing evaluation |
| `DocParsingBench/` | Gold-standard benchmark | Chinese/English Markdown parsing evaluation |
| `ParseBench/` | Gold-standard benchmark | RAG-oriented parsing evaluation |

---

## docling (tests/data)

- **Source:** <https://github.com/docling-project/docling/tree/main/tests/data>
- **Purpose:** Regression test fixtures shipped with the [Docling](https://github.com/docling-project/docling) document parser. Each format directory contains `sources/` (input documents) and `groundtruth/` (expected parse results) used to verify the parser's output.
- **Content:** 36+ document formats including `pdf`, `docx`, `xlsx`, `pptx`, `html`, `md`, `latex`, `epub`, `csv`, `email`, `audio`, and images.

> Note: This is function-level test data, not an independent benchmark. It is bound to Docling's own output schema.

---

## OmniDocBench

- **Source:** <https://huggingface.co/datasets/opendatalab/OmniDocBench>
- **Purpose:** A gold-standard benchmark for evaluating document layout analysis and end-to-end document parsing. Widely used as a reference for layout detection, reading-order, table, and formula extraction.
- **Content:** 1,651 document page images with structured annotations (`layout_dets` containing category, polygon coordinates, text, and reading order), plus `page_info` and element relations.
- **Metrics:** TextEdit (text accuracy), TableTEDS (table structure), FormulaCDM (formula), ReadingOrder.

---

## DocParsingBench

- **Source:** <https://huggingface.co/datasets/SoMarkAI/DocParsingBench>
- **Purpose:** A gold-standard benchmark with fully human-annotated (no model-assisted annotation) Markdown ground truth, targeting Chinese and English business documents.
- **Content:** 1,400 pages across five domains — finance, law, research, manufacturing, and education — with Markdown annotations (chemical structures use SMILES + LaTeX).
- **Metrics:** DPB composite metric covering text, formula, and table.

---

## ParseBench

- **Source:** <https://huggingface.co/datasets/llamaindex/ParseBench>
- **Purpose:** A benchmark for evaluating document parsing quality in RAG workflows, released by LlamaIndex.
- **Content:** ~2,000 human-verified enterprise document pages organized into four capability dimensions: `chart`, `layout`, `table`, and `text`, with JSONL annotations and an `eval.yaml` evaluation config.
- **Metrics:** Five dimensions — content fidelity, semantic formatting, visual location, table extraction, and chart analysis.
