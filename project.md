---
layout: page
title: Projects
permalink: /projects/
---

# My Projects

## Agentic AI

### MatchDay — World Cup 2026 AI Assistant

**Tech Stack:** Python, FastAPI, Gemini (Vertex AI), MongoDB Atlas, GCP Cloud Run, Discovery Engine

Built for the **Google Cloud Rapid Agent Hackathon** (MongoDB partner track). Multi-tool AI agent handling live match data, trip planning, fantasy predictions, match reminders, and head-to-head history through a single chat interface. Custom tool-calling loop with 13+ tools, RAG via Discovery Engine, persistent state in MongoDB Atlas via MCP server. Deployed on Cloud Run.

**Live Demo:** [wc2026-agent-623255749732.us-central1.run.app](https://wc2026-agent-623255749732.us-central1.run.app/)

[Learn More →](/projects/matchday/)

---

### Courtside — AI Sports Assistant

**Tech Stack:** Python, FastAPI, Gemini 2.5 Flash, PostgreSQL, RAG

Production-deployed AI assistant with agentic tool calling and on-demand RAG. Features live sports data across 20+ leagues, Wikipedia-based RAG for deep questions, timezone-aware email reminders, and preference-based personalization. Tool-calling loop built manually without LangChain.

**Live Demo:** [courtside-1uqy.onrender.com](https://courtside-1uqy.onrender.com)

[Learn More →](/projects/courtside/) | [GitHub →](https://github.com/Animesh452/Courtside)

---

## ML/NLP

### Support Ticket Router + Responder

**Tech Stack:** Python, DistilBERT, Llama 3.2 3B, QLoRA, bitsandbytes, Weights & Biases, SLURM

End-to-end ML system for customer support triage. Fine-tuned DistilBERT (99.9% accuracy) for classification + Llama 3.2 3B with QLoRA for response generation. Trained on ASU Sol Supercomputer (A100) via SLURM. Only 0.6% of parameters trained — 37MB adapter vs 6GB full model.

**Live Demo:** [huggingface.co/spaces/AnimeshK509/ticket-router](https://huggingface.co/spaces/AnimeshK509/ticket-router)

[Learn More →](/projects/ticket-router/)

---

### STaB-RAG: Weighted Multi-Signal Retrieval for Tables

**Focus:** RAG ranking for semi-structured data

Designed a weighted reranking pipeline combining dense embeddings, BM25 lexical matching, and structural similarity for table-based QA. Evaluated on NQ-Tables with BEIR benchmarks.

[Learn More →](/projects/stab-rag/)

---

### Medical Premium Prediction System

**Tech Stack:** Python, Random Forest, XGBoost, SHAP

Built an interpretable ML pipeline for insurance premium prediction with strong generalization and SHAP-based analysis.

[Learn More →](/projects/medical-premium/)

---

### Driver Monitoring System using Computer Vision

**Tech Stack:** OpenCV, TensorFlow, VGG16

Peer-reviewed research (ACCAI 2024) on real-time detection of driver drowsiness and unsafe behavior using facial landmarks and CNNs.

[Learn More →](/projects/driver-monitoring-system/)

---

### Speech Recognition Model Optimization

**Tech Stack:** CNN, LSTM, Transformer

Compared deep learning architectures for speech command recognition with attention mechanisms and accuracy benchmarking.

[Learn More →](/projects/speech-recognition/)

---

### Emotion Detection System

**Tech Stack:** Deep Learning, Computer Vision

Explored facial emotion recognition techniques using CNN-based models and feature extraction methods.

[Learn More →](/projects/emotion-detection/)

---

### E-commerce Recommendation System

**Tech Stack:** Machine Learning, Recommendation Systems

Developed a recommendation pipeline using collaborative and content-based filtering approaches.

[Learn More →](/projects/ecom-recommendation-system/)

---

## Systems / Applied AI

### GoodFirstFindr

**Tech Stack:** Python, FastAPI, Groq, Llama 3.3 70B, Neon PostgreSQL, Render

GitHub good-first-issue finder with a four-dimension scoring pipeline (skill match, repo health, competition, freshness) and LLM reranking via Groq. Persistent skill profiles and saved issues in Neon PostgreSQL. Built with OpenAI Codex.

**Live Demo:** [goodfirstfindr.onrender.com](https://goodfirstfindr.onrender.com)

[Learn More →](/projects/goodfirstfindr/)

---

### Recon — Automated Job Search Pipeline

**Tech Stack:** Python, LLM APIs, web automation, human-in-the-loop review

Built an applied AI pipeline for automated job discovery, LLM-based screening, resume tailoring, and human-reviewed role triage.

[Learn More →](/projects/recon/)

---

### Data Processing Pipeline (DPS)

**Tech Stack:** Kafka, Kubernetes, Neo4j

Built a distributed data processing pipeline with graph-based analytics and scalable ingestion.

[Learn More →](/projects/data-pipeline-dps/)

---

### Mobile Edge Computing with DDQN

**Focus:** Conceptual design for energy-efficient task scheduling

Proposed a reinforcement-learning-based framework for optimizing task scheduling in mobile edge environments.

[Learn More →](/projects/mobile-edge-ddqn/)

---

## Applications

### Oneironauts 🌙

**Tech Stack:** Python, Llama 3.2 3B, Modal, Whisper, Gradio

Built for the **HuggingFace Build Small Hackathon** (Track 2) — won two achievements: Offbrand and Fieldnotes. A dream fragment becomes a branching narrative with voice input via Whisper, scene generation via Llama 3.2 3B on a Modal A10G endpoint, and 4-level deep choice trees.

**Live App:** [huggingface.co/spaces/build-small-hackathon/oneironauts](https://huggingface.co/spaces/build-small-hackathon/oneironauts)

[Learn More →](/projects/oneironauts/)

---

### TrustMed-AI

**Tech Stack:** RAG, Neo4j, Knowledge Graphs

Developed a healthcare-focused conversational system integrating structured medical knowledge with retrieval-augmented generation.

[Learn More →](/projects/trustmed-ai/)

---

### Tic-Tac-Toe with AI (Android)

**Tech Stack:** Android, Minimax, Bluetooth

Implemented an AI-powered Tic-Tac-Toe game with multiplayer support and optimized decision-making.

[Learn More →](/projects/tic-tac-toe/)

---

### Scribee

**Tech Stack:** NLP, Text Processing

An exploratory project focused on transcription, summarization, and text intelligence workflows.

[Learn More →](/projects/scribee/)