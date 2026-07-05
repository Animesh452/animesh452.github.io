---
layout: page
title: Support Ticket Router + Responder
permalink: /projects/ticket-router/
---

# Support Ticket Router + Responder

**Live Demo:** [huggingface.co/spaces/AnimeshK509/ticket-router](https://huggingface.co/spaces/AnimeshK509/ticket-router)  
**Models on HF Hub:** [ticket-category-classifier](https://huggingface.co/AnimeshK509/ticket-category-classifier) · [ticket-priority-classifier](https://huggingface.co/AnimeshK509/ticket-priority-classifier) · [ticket-response-generator-lora](https://huggingface.co/AnimeshK509/ticket-response-generator-lora)

## Overview
An end-to-end ML system that takes a raw customer support ticket and automatically outputs a category, priority level, and a professional draft response — ready for a human agent to review and send. Handles the first-pass triage and drafting that would otherwise take 2–3 minutes per ticket.

## Architecture
[Raw Ticket Text]
↓
[Fine-tuned DistilBERT]
→ Category: billing / technical / feature_request / bug
→ Priority: low / medium / high / critical
↓
[Llama 3.2 3B + QLoRA Adapter]
→ Draft response
↓
[Gradio UI — classification card + editable draft]

Two independent models chained together — a discriminative classifier for fast triage, a generative model for response drafting.

## Models & Training

**Classifier — Fine-tuned DistilBERT (66M params)**
- Dataset: Bitext Customer Support LLM dataset — 26,872 samples across 27 intent categories
- Mapped to 4 categories and 4 priority levels
- 5 epochs, batch size 32, lr 2e-5 with warmup
- Trained on ASU Sol Supercomputer (A100 40GB) via SLURM
- Training time: ~15 minutes

**Generator — Llama 3.2 3B + QLoRA**
- 4-bit NF4 quantization via bitsandbytes (cuts VRAM from ~14GB to ~6GB)
- LoRA rank r=16, alpha=32, targeting q/k/v/o projection layers
- Only 0.6% of parameters trained (~20M of 3.2B) — adapter is 37MB vs 6GB full model
- 3 epochs, effective batch size 16, lr 2e-4 with cosine schedule
- Training time: ~2.1 hours on A100
- Experiment tracking via Weights & Biases

## Evaluation Results

**Classifier (4,031 held-out samples):**

| Metric | Score |
|--------|-------|
| Category accuracy | 99.9% |
| Priority accuracy | 99.9% |
| Majority class baseline | 36.9% / 41.1% |

**Generator — Qualitative improvements after fine-tuning:**
- No template placeholder leakage (e.g. `{{Customer Support Phone Number}}`)
- Asks for the right information per ticket type (order number for billing, username for account issues)
- Correctly distinguishes feature requests from how-to questions
- Structured numbered steps for technical issues

## Why Fine-Tuning Over Prompting

| Problem with prompting alone | How fine-tuning fixes it |
|------------------------------|--------------------------|
| Inconsistent classification on ambiguous tickets | Model learns exact taxonomy from 26k examples |
| Template placeholders bleed through | Model learns clean response patterns |
| Every ticket = expensive frontier API call | 3B model runs cheaply at inference |
| Slow for real-time triage | DistilBERT classifies in ~50ms |

## Tech Stack

| Component | Tool |
|-----------|------|
| Classifier | DistilBERT via HuggingFace Trainer |
| Generator | Llama 3.2 3B + QLoRA via peft + trl |
| Quantization | bitsandbytes 4-bit NF4 |
| Experiment tracking | Weights & Biases |
| Training compute | ASU Sol Supercomputer (A100 via SLURM) |
| Frontend | Gradio |
| Deployment | HuggingFace Spaces |

---
**Tech Stack:** Python, PyTorch, HuggingFace Transformers, peft, trl, bitsandbytes, Weights & Biases, Gradio, SLURM