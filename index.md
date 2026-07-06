---
layout: home
title: Home
---

<style>
  .home-hero {
    display: grid;
    grid-template-columns: minmax(0, 1fr) auto;
    gap: clamp(1.5rem, 4vw, 3rem);
    align-items: center;
    margin-bottom: clamp(2.75rem, 5vw, 4rem);
    padding: clamp(0.75rem, 3vw, 1.5rem) 0 clamp(2.5rem, 5vw, 3.25rem);
    text-align: left;
  }

  .home-hero h1 {
    font-size: clamp(2.8rem, 8vw, 5rem);
    margin-bottom: 0.65rem;
  }

  .home-hero .profile-image {
    height: clamp(150px, 22vw, 210px);
    margin: 0;
    width: clamp(150px, 22vw, 210px);
  }

  .hero-tagline {
    color: var(--site-accent);
    font-size: 0.9rem;
    font-weight: 800;
    letter-spacing: 0.08em;
    margin: 0 0 0.8rem;
    text-transform: uppercase;
  }

  .hero-intro {
    color: var(--site-muted);
    font-size: clamp(1.08rem, 2.5vw, 1.28rem);
    line-height: 1.65;
    margin-bottom: 1.4rem;
    max-width: 42rem;
  }

  .hero-actions {
    justify-content: flex-start;
  }

  .about-narrative {
    color: var(--site-muted);
    font-size: 1.04rem;
    line-height: 1.75;
    max-width: 46rem;
  }

  @media (max-width: 720px) {
    .home-hero {
      grid-template-columns: 1fr;
      text-align: center;
    }

    .home-hero .profile-image {
      justify-self: center;
      order: -1;
    }

    .hero-actions {
      justify-content: center;
    }
  }
</style>

<section class="portfolio-hero home-hero" markdown="1">

<div class="hero-copy" markdown="1">

<p class="hero-tagline">AI • ML • Agentic Systems • LLM Engineering</p>

# Animesh Kumar

<p class="hero-intro">MS Computer Science (GPA 4.0, Arizona State University) building production AI systems — agentic pipelines, fine-tuned models, and full-stack LLM applications.</p>

<div class="button-row hero-actions">
  <a class="button" href="/projects/">View Projects</a>
  <a class="button button--secondary" href="/contact/">Contact Me</a>
</div>

</div>

<img class="profile-image" src="/assets/img/WhatsApp%20Image%202025-09-23%20at%2023.26.05_acdcd051.jpg" alt="Animesh Kumar">

</section>

<section class="portfolio-section portfolio-section--featured" markdown="1">

## 🚀 Featured Projects

<div class="featured-projects" markdown="1">

<article class="featured-project" markdown="1">

### MatchDay — World Cup 2026 AI Assistant

**Built for:** Google Cloud Rapid Agent Hackathon (MongoDB partner track)

Multi-tool AI agent for the FIFA World Cup 2026 fan experience — live match data, trip planning, fantasy predictions, match reminders, and head-to-head history. Custom tool-calling loop, RAG via Discovery Engine, persistent state via MongoDB MCP. Deployed on Cloud Run.

**Tech Stack:** Python, FastAPI, Gemini (Vertex AI), MongoDB Atlas, GCP Cloud Run, Discovery Engine

[Learn More →](/projects/matchday/) | [Live Demo →](https://wc2026-agent-623255749732.us-central1.run.app/)

</article>

<article class="featured-project" markdown="1">

### Support Ticket Router + Responder

**Achievement:** 99.9% classification accuracy, trained on ASU's A100 supercomputer

End-to-end ML system for customer support triage. Fine-tuned DistilBERT for fast classification + Llama 3.2 3B with QLoRA for response generation. Only 0.6% of parameters trained — 37MB adapter vs 6GB full model. Trained via SLURM on ASU Sol.

**Tech Stack:** Python, DistilBERT, Llama 3.2 3B, QLoRA, bitsandbytes, Weights & Biases, SLURM

[Learn More →](/projects/ticket-router/) | [Live Demo →](https://huggingface.co/spaces/AnimeshK509/ticket-router)

</article>

<article class="featured-project" markdown="1">

### Recon — Automated Job Search Pipeline

**Focus:** Automated job search with LLM-based screening

Built an applied AI pipeline for automated job discovery, LLM-based screening, resume tailoring, and human-reviewed role triage.

**Tech Stack:** Python, LLM APIs, web automation, human-in-the-loop review

[Learn More →](/projects/recon/)

</article>

</div>

</section>

<section class="portfolio-section" markdown="1">

## I build. I learn. I solve.

<div class="about-narrative" markdown="1">

I build AI systems that turn models, data, and product ideas into software people can actually use. As a recent MS Computer Science graduate from Arizona State University (GPA 4.0, May 2026), my work sits at the intersection of agentic AI, LLM engineering, fine-tuning, and production deployment.

I care about practical impact: systems that answer real questions, support better decisions, and keep working beyond the demo. My strength is combining ML depth with systems thinking — from research prototypes to full-stack engineering and production-ready workflows.

</div>

</section>

<section class="portfolio-section" markdown="1">

## 📚 Publications

- **Real-time Driver Monitoring using Facial Landmarks and Deep Learning** *(ACCAI 2024)*
- **Intelligent Texture Feature-Based Defects Classification of Aircraft Engine Blades** *(INFUS 2024)*

</section>

<section class="portfolio-cta">
<div class="button-row">
  <a class="button" href="/projects/">View All Projects</a>
  <a class="button button--secondary" href="/contact/">Contact Me</a>
</div>
</section>