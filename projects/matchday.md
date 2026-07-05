---
layout: page
title: MatchDay — World Cup 2026 AI Assistant
permalink: /projects/matchday/
---

# MatchDay — World Cup 2026 AI Assistant

**Live Demo:** [wc2026-agent-623255749732.us-central1.run.app](https://wc2026-agent-623255749732.us-central1.run.app/)  
**Built for:** Google Cloud Rapid Agent Hackathon — MongoDB Partner Track  
**Built solo**

## Overview
A multi-tool conversational AI agent that handles the full fan experience for FIFA World Cup 2026 — live match data, trip planning, fantasy predictions, match reminders, and head-to-head history, all through a single chat interface.

## Architecture
User (Browser)
↓
FastAPI Backend (Cloud Run)
↓
Gemini 3.1 Pro Preview — Custom Tool-Calling Loop
├── ESPN API          → Live schedules, results, standings
├── MongoDB MCP       → User state, reminders, predictions
├── Discovery Engine  → Venue knowledge base (RAG)
└── Google Search     → News, head-to-head queries
↓
Background Worker (asyncio) → Email reminders via Brevo SMTP

## Features
- **Live match data** — schedules, results, standings from ESPN's live API
- **Team following** — persistent preferences stored in MongoDB Atlas via MCP server
- **Match reminders** — natural language reminder setting, delivered via email
- **Trip planning** — itineraries chaining match schedules with venue knowledge from Discovery Engine RAG
- **Fantasy predictions** — predict scores, get scored when results arrive (3pts exact, 1pt correct winner), compete on a leaderboard
- **Head-to-head queries** — historical matchup data via Gemini's grounded Google Search
- **Conversation memory** — context persists across turns within a session

## Tech Stack

| Layer | Technology |
|-------|-----------|
| LLM | Gemini 3.1 Pro Preview (Vertex AI) |
| Agent | Custom Python tool-calling loop |
| Backend | FastAPI (Python 3.11) |
| Deployment | Google Cloud Run (containerized) |
| Database | MongoDB Atlas via MongoDB MCP server |
| RAG | Google Cloud Discovery Engine |
| Email | Brevo SMTP |
| Secrets | GCP Secret Manager |

## Key Design Decisions

**Why a custom tool-calling loop over a framework?**  
Frameworks like LangChain abstract the orchestration layer, making it hard to explain what's happening. Building the loop manually means every step — tool selection, argument parsing, result handling — is visible and debuggable.

**Why MongoDB MCP?**  
Every user-state operation (follows, reminders, predictions, leaderboard) goes through the MCP server rather than direct DB calls. This keeps the agent layer clean and makes the integration non-trivial — the MCP responses required a custom parser to extract document arrays from the server's structured responses.

**Why Discovery Engine for RAG?**  
Venue knowledge (stadiums, cities, travel logistics) is static and well-structured — a perfect fit for a managed search index. Discovery Engine handles chunking, indexing, and retrieval without maintaining a custom vector store.

## Results
- Production deployment on Cloud Run with auto-scaling
- Persistent multi-user state across sessions via MongoDB Atlas
- Background reminder worker running every 30 seconds alongside the main API
- End-to-end fan experience from match tracking to trip planning in one interface

---
**Tech Stack:** Python, FastAPI, Gemini (Vertex AI), MongoDB Atlas, GCP Cloud Run, Discovery Engine, ESPN API, Brevo SMTP