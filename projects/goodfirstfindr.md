---
layout: page
title: GoodFirstFindr
permalink: /projects/goodfirstfindr/
---

# GoodFirstFindr

**Live Demo:** [goodfirstfindr.onrender.com](https://goodfirstfindr.onrender.com)  
**Note:** Built with OpenAI Codex (vibe-coded), with subsequent updates also made via Codex prompts.

## Overview
Finding a useful first open source issue is noisy — popular issues get claimed fast, labels don't guarantee fit, and keyword search has no awareness of your skills. GoodFirstFindr searches GitHub for open, unassigned `good first issue` issues, then runs each candidate through a four-dimension scoring pipeline and an LLM reranker to surface the issues most likely to be a genuine fit.

## Architecture
GitHub API
↓
Issue Fetcher (httpx)
↓
Rule-based Filters (remove assigned, PRs)
↓
Scoring Engine (4-dimension, 0–100)
↓
Groq LLM — Llama 3.3 70B (fit score, red flags, explanation)
↓
Ranked Results + Saved Issues + Email Digest

## Scoring Pipeline

| Dimension | Weight | What it measures |
|-----------|-------:|-----------------|
| Skill match | 40% | Matches issue title, body, labels, repo metadata against user's selected skills |
| Repo health | 25% | Stars, forks, activity, open issue load |
| Competition | 20% | Fewer comments = less visible competition |
| Freshness | 15% | Recent enough to still be active |

When LLM explanations are enabled, the deterministic score blends 50/50 with the Groq fit score, then penalties are applied:
- Language mismatch: −40 points
- Red flags (unclear requirements, claimed work, etc.): −15 points each, capped at −50

## Features
- **Skill profiles** — select up to 20 skills from a categorized master list on first visit; stored per browser in Neon PostgreSQL without requiring auth
- **LLM reranking** — Groq reads the actual issue description to catch mismatches that metadata alone misses
- **Saved issues** — bookmark issues across sessions, stored in PostgreSQL by browser client ID
- **Daily email digest** — APScheduler sends top ranked issues for a configured keyword every morning

## Tech Stack

| Component | Tool |
|-----------|------|
| Backend | FastAPI |
| LLM | Groq API — Llama 3.3 70B |
| Database | Neon PostgreSQL |
| Scheduler | APScheduler |
| HTTP client | httpx |
| Deployment | Render |

---
**Tech Stack:** Python, FastAPI, Groq, Llama 3.3 70B, Neon PostgreSQL, APScheduler, Render