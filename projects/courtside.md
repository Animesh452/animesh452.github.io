---
layout: page
title: Courtside - AI Sports Assistant
permalink: /courtside/
---

# Courtside - AI Sports Assistant

## Tech Stack

**Tech Stack:** Python, FastAPI, Gemini 2.5 Flash, PostgreSQL, APScheduler, Resend API, Wikipedia API, ESPN API, HTML/JS

| Layer | Technology | Why |
|-------|-----------|-----|
| LLM | Gemini 2.5 Flash | Free tier, strong tool calling |
| Backend | FastAPI (Python) | Async-ready, lightweight |
| Frontend | Single HTML file | No build tools, focus on backend |
| Database | PostgreSQL / SQLite | Auto-detected via DATABASE_URL |
| Scheduler | APScheduler | Python-native background jobs |
| Notifications | Resend API | HTTPS-based email (SMTP blocked on Render) |
| RAG | Wikipedia + keyword scoring | No embedding model, zero cold-start overhead |
| Sports Data | ESPN Unofficial API | Free, no auth, all major sports |
| Deployment | Render (free tier) | Auto-deploy from GitHub |

## Overview
A personal AI sports assistant with agentic tool calling, on-demand RAG, and automated event reminders. Courtside replaces manual googling of sports schedules, missing match results, and researching new sports with a single conversational interface.

## Problem

### Problem Statement
Sports fans face constant challenges: manually searching for schedules across multiple leagues, missing important matches, lacking context about players and teams, and managing reminders for upcoming events across different time zones.

## Approach

### Technical Implementation

#### Architecture
Browser (HTML/JS) — sends user timezone automatically
↓
FastAPI Backend → Agentic Tool Loop (Gemini 2.5 Flash)
├── Sports Data Tool (ESPN API → schedules, scores, cricket)
├── Deep Search Tool (Wikipedia → chunk → keyword score)
├── Reminder Tool (PostgreSQL → APScheduler → Resend email)
├── Preference Tool (PostgreSQL → personalization)
└── Direct Chat (LLM answers from knowledge)
↓
APScheduler (background) → checks every 60s → sends emails

#### Core Features

**1. Agentic Tool Calling**
- LLM autonomously decides which tool to invoke based on user intent
- No hardcoded if/else routing - pure intent understanding
- Built manually (no LangChain) to demonstrate understanding of the pattern

**2. Live Sports Data**
- Real-time schedules and scores via ESPN unofficial API
- Supports 20+ sports: UFC, MMA, F1, NFL, NBA, MLB, NHL, Tennis, Soccer leagues, Cricket
- Automatic timezone conversion for global events

**3. On-Demand RAG (Retrieval-Augmented Generation)**
- Deep questions trigger Wikipedia content fetching
- Chunks passages, scores by keyword relevance
- Uses best chunks as LLM context, then discards
- Zero maintenance, no embedding model required

**4. Event Reminders**
- Natural language reminder creation: "remind me about UFC 327 on April 12 at 5pm"
- Timezone-aware storage in PostgreSQL
- APScheduler checks every 60 seconds
- Email delivery via Resend API

**5. Preference Store**
- PostgreSQL-backed personalization
- Remembers followed sports and teams
- Contextual responses: "any upcoming events?" returns UFC schedule if user follows UFC

### Key Technical Decisions

#### Why Agentic Tool Calling Over If/Else Routing?
Hardcoded routing like `if "schedule" in message` breaks with language variations. The agentic approach lets the LLM understand intent naturally - define tools with JSON schemas and the model picks which to call. This is how production AI systems work.

#### Why Build Tool-Calling Loop Manually?
LangChain abstracts the loop, making it impossible to explain internals. Building manually (~50 lines) means every step is visible and explainable. Signals understanding over framework dependency.

#### Why On-Demand RAG Instead of Vector Database?
Pre-scraping all sports data isn't feasible - data is enormous and constantly stale. On-demand RAG: fetch at query time, chunk, score, retrieve, answer, discard. No maintenance burden.

#### Why Keyword Scoring Over Embeddings?
Original implementation used ChromaDB with all-MiniLM-L6-v2 embedding model (~80MB). On Render's ephemeral filesystem, this re-downloaded on every cold start, adding 30+ seconds. Keyword scoring achieves comparable retrieval with zero model dependencies.

### Implementation Highlights

**Timezone Handling:**
- Browser automatically detects and sends user timezone
- All reminders store creation timezone
- Email notifications formatted in user's timezone

**Error Handling:**
- Graceful degradation when APIs are unavailable
- Connection retry logic for Bluetooth (in Tic-Tac-Toe integration)
- Database auto-detection between PostgreSQL and SQLite

**Real-time Synchronization:**
- APScheduler background jobs for reminder checks
- Email delivery via Resend API (SMTP ports blocked on Render)
- Persistent storage survives server restarts

## Results

### Results & Impact
- **Live deployment** on Render free tier with auto-deploy
- **Zero cold-start model downloads** after optimization
- **Instant responses** for sports queries across 20+ leagues
- **Reliable reminders** with timezone-aware email delivery
- **Personalized experience** through preference learning

**Deployment:** Render (free tier) with auto-deploy from GitHub

**Key Skills Demonstrated:** Agentic AI, RAG Architecture, Tool Calling, Real-time Systems, API Integration, Database Design, Production Deployment

## Learnings

### Challenges Overcome

**1. Deployment Constraints:**
- Ephemeral filesystem wiped database → switched to PostgreSQL
- SMTP ports blocked → implemented Resend API
- 80MB embedding model cold starts → moved to keyword scoring

**2. Production vs Development Gap:**
- Local SQLite → Production PostgreSQL auto-detection
- Manual timezone handling → browser-based detection
- Cold-start optimization → eliminated heavy dependencies

**3. Data Synchronization:**
- Real-time reminder checks without blocking requests
- Graceful handling of API failures
- Consistent state across server restarts

### What I Learned
- Agentic tool calling separates chatbots from useful AI systems
- Never let LLM do math - compute in Python, give formatted text
- On-demand RAG is more practical than vector databases for most use cases
- Every production constraint led to better architecture
- Deployed version is architecturally stronger than original design

## Limitations & Future Work

### Future Improvements
- User authentication for multi-user support
- Chat history persistence (currently resets on restart)
- Soccer/Tennis fixture APIs with actual match details
- Paid sports APIs for production reliability
- OAuth and per-user database isolation

## Resources

**Live Demo:** [courtside-1uqy.onrender.com](https://courtside-1uqy.onrender.com)

**GitHub:** [github.com/Animesh452/Courtside](https://github.com/Animesh452/Courtside)
