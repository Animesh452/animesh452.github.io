---
layout: page
title: STaB-RAG — Weighted Multi-Signal Retrieval
permalink: /projects/stab-rag/
---

# STaB-RAG — Weighted Multi-Signal Retrieval for Semi-Structured Tables

**Tech Stack:** Python, Retrieval-Augmented Generation (RAG) pipelines, Dense embeddings, BM25, BEIR/NQ-Tables evaluation

## Overview
STaB-RAG is a retrieval and reranking pipeline designed to improve the ranking of semi-structured tables for retrieval-augmented generation (RAG) systems. Instead of flattening tables and relying on a single similarity signal, STaB-RAG fuses dense semantic similarity, lexical overlap (BM25), and structural alignment signals to better surface the most informative table chunks for downstream generation and QA tasks. The approach was evaluated on table QA benchmarks (NQ-Tables / BEIR-style splits) and shows improved early-precision ranking performance.

## Problem
Standard RAG pipelines often linearize tables and rely on dense retrieval alone, which can miss layout and schema cues important for table-based question answering. On benchmarks like NQ-Tables, many systems retrieve the correct table but fail to rank it at the top where it can guide generation effectively. STaB-RAG addresses this ranking gap by incorporating multiple complementary signals.

## Approach
STaB-RAG is implemented as a multi-stage pipeline:

- **Corpus construction & chunking:** Tables are reconstructed into structured objects and chunked using multiple granularities (pure_table, table_row, table_column, sliding windows). The pure_table representation preserves full table structure and performed best in experiments.
- **Candidate generation:** Dense retrieval (using sentence-style encoders) produces a top-k candidate set.
- **Signal attachment:** For each candidate chunk, compute:
  - Dense semantic similarity (embedding-based),
  - BM25 lexical score,
  - Structural similarity score (alignment with table schema/layout and headers).
- **Weighted reranking:** Combine the three signals into a single weighted score (α·Domain + β·Reliability + γ·Structure) and re-rank candidates.
- **Optional cross-encoder:** Apply an optional cross-encoder on top of the aggregated scores for further refinement.
- **Ablations & encoder comparison:** Multiple embedding models and encoders were compared; the final pipeline selected the best-performing encoder and signal weights based on validation.

## Key Results
- STaB-RAG consistently improved **early-precision** metrics (notably Recall@1 and NDCG@3), which are critical for retrieval quality in RAG applications.
- In comparisons on the NQ-Tables dataset, STaB-RAG outperformed dense-only and lexical-only baselines and achieved competitive gains over strong baselines (TAPAS, BIBERT, SPLADE, etc.). Specific metric improvements and ablation details are reported in the project report. :contentReference[oaicite:1]{index=1}

## Why it matters
- For table-based QA, retrieving the right evidence at top ranks is more important than merely having it somewhere in the candidate pool. STaB-RAG’s multi-signal reranking directly targets that need.
- The structural signal—explicit awareness of headers, column types, and table layout—augments semantic retrieval to avoid common failure modes of dense embeddings when table schema matters.
- The approach is modular: each signal (dense, lexical, structural) can be replaced or extended, making STaB-RAG adaptable to new encoders and domain signals.

## Lessons & Next Steps
- **Chunking matters:** preserving table structure (pure_table) gave the most stable retrieval results.
- **Signal fusion is effective:** combining diverse signals improves ranking robustness and interpretability.
- **Future work:** refine structural scoring, explore learned weightings (meta-learned rerankers), and integrate cross-encoder reranking at scale; also evaluate on domain-specific enterprise tables.

## Resources:  
- Project report (PDF) — [Final_Report.pdf](/assets/files/CSE_576_Final_Report.pdf)
- Implementation: GitHub repo — [WeightedRAG](https://github.com/Abhijit85/WeightedRAG.git)
