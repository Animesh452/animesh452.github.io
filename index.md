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

<p class="hero-tagline">AI • ML • Retrieval Systems • Data Processing</p>

# Animesh Kumar

<p class="hero-intro">MS Computer Science student at Arizona State University building AI/ML systems that connect strong models with practical, reliable software.</p>

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

### Recon - Automated Job Search Pipeline

**Focus:** Automated job search with LLM-based screening

Built an applied AI pipeline for automated job discovery, LLM-based screening, and human-reviewed role triage.

**Tech Stack:** Python, LLM APIs, web automation, human-in-the-loop review

[Learn More →](/projects/recon/)

</article>

<article class="featured-project" markdown="1">

### 🏀 Courtside - AI Sports Assistant

**Achievement:** Production AI system with agentic tool calling and RAG

Full-stack AI assistant that autonomously handles sports queries, sets reminders, and provides deep insights using on-demand Wikipedia RAG. Deployed on Render with persistent storage and real-time email notifications.

**Tech Stack:** Python, FastAPI, Gemini 2.5 Flash, PostgreSQL, APScheduler

[Learn More →](/courtside/) | [Live Demo →](https://courtside-1uqy.onrender.com)

</article>

<article class="featured-project" markdown="1">

### 📊 STaB-RAG: Weighted Multi-Signal Retrieval

**Focus:** Improving table retrieval ranking for RAG systems

Proposed a weighted reranking pipeline combining dense, lexical (BM25), and structural signals for semi-structured table retrieval. Evaluated on NQ-Tables using BEIR benchmarks, achieving strong gains in early precision metrics.

**Tech Stack:** Python, Information Retrieval, RAG, BM25, Dense Embeddings

[Learn More →](/projects/stab-rag/)

</article>

</div>

</section>

<section class="portfolio-section" markdown="1">

## I build. I learn. I solve.

<div class="about-narrative" markdown="1">

I build AI systems that turn models, data, and product ideas into software people can actually use. As an MS Computer Science student at Arizona State University, my work sits at the intersection of machine learning, retrieval-augmented generation, computer vision, and distributed systems.

I care about practical impact: systems that answer real questions, support better decisions, and keep working beyond the demo. My strength is combining ML depth with systems thinking, from research prototypes to full-stack engineering and production-ready workflows.

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
