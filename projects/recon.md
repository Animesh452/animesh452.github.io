---
layout: page
title: Recon - Automated Job Search Pipeline
permalink: /projects/recon/
---

# Recon - Automated Job Search Pipeline

## Tech Stack

**Tech Stack:** Python, LiteLLM, Ollama (Qwen 2.5), SQLite, Google Sheets API, Apify, LaTeX, Task Scheduler

## Overview

Recon is an automated job search pipeline designed to make opportunity discovery more structured, scalable, and selective. Instead of manually scanning postings one by one, the system collects candidate roles, screens them with an LLM-based evaluator, and surfaces the strongest matches for human review.

The goal is not to fully automate applications. Recon is built around a human-in-the-loop workflow where automation handles repetitive filtering, while final judgment, customization, and outreach stay with the user.The system goes beyond filtering by generating tailored resumes and cold outreach drafts for approved roles, turning job search into a semi-automated pipeline.

## Problem

Job searching is noisy and repetitive. Relevant roles are spread across many sources, job descriptions vary in quality, and manual screening makes it easy to miss promising opportunities or spend time on poor matches.

Recon addresses three core challenges:
- Finding relevant postings consistently across multiple sources.
- Comparing job requirements against a candidate profile in a repeatable way.
- Keeping the workflow accountable by requiring human review before action.

## Approach

The pipeline runs as a twice-daily automated workflow: morning ingestion and screening, followed by an afternoon drafting phase based on user-approved roles.

### System Architecture

Recon is structured as a modular pipeline:

- **Ingestion:** Collects job postings from configured sources and normalizes them into a consistent format.
- **Parsing & enrichment:** Extracts key fields such as role, company, location, requirements, skills, and application metadata.
- **LLM-based screening:** Scores each posting against the candidate profile using criteria such as skill fit, role alignment, seniority, location, and relevance.
- **Ranking & triage:** Groups roles into high-priority, review, and low-fit queues so the user can focus attention where it matters.
- **Human review:** Keeps the final decision in the loop before applications, follow-ups, or saved leads are generated.

### Design Principles

The system prioritizes transparency over blind automation. Screening outputs are designed to include reasoning, fit signals, and potential concerns rather than a single opaque score.

It also separates data collection, evaluation, and review so each part can be improved independently. This makes it easier to add new job sources, adjust screening prompts, or refine ranking criteria without rewriting the whole workflow.

## Results / Impact

- Automated multi-source job discovery and screening into a daily pipeline.
- Reduced manual job filtering from hours to a structured review workflow.
- Enabled consistent, repeatable evaluation of job fit using LLM-based reasoning.
- Generated tailored resumes and outreach drafts on demand for approved roles.

## Learnings

Recon reinforced that LLMs are most useful in workflow automation when they assist judgment instead of replacing it. The strongest design pattern was using the model for structured interpretation, ranking, and explanation, then letting the user make the final decision. 

The project also highlighted the importance of system architecture in applied AI work. Clean boundaries between ingestion, screening, storage, and review make the pipeline easier to debug and extend. It also highlighted how local LLMs can be effectively integrated into production-style workflows without relying on cloud inference, reducing cost while maintaining flexibility.

## Limitations & Future Work

- Add stronger deduplication across job boards and company career pages.
- Track application status, follow-ups, and outcomes over time.
- Improve evaluation with feedback loops from accepted, rejected, or ignored roles.
- Add guardrails for stale postings, incomplete job descriptions, and inflated requirements.
- Expand reporting so the user can see which skills, titles, and companies appear most often.

## Resources

- Project repository: *to be linked*
