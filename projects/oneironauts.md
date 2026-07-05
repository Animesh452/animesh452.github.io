---
layout: page
title: Oneironauts
permalink: /projects/oneironauts/
---

# Oneironauts 🌙

**Live App:** [huggingface.co/spaces/build-small-hackathon/oneironauts](https://huggingface.co/spaces/build-small-hackathon/oneironauts)  
**Demo video:** [youtu.be/BxoNeiBMID8](https://youtu.be/BxoNeiBMID8)  
**Field notes:** [huggingface.co/blog/AnimeshK509/oneironauts](https://huggingface.co/blog/AnimeshK509/oneironauts)  
**Built for:** HuggingFace Build Small Hackathon — Track 2 (An Adventure in Thousand Token Wood)  
**Achievements:** 🏆 Offbrand · 🏆 Fieldnotes

## Overview
A fragment of a half-remembered dream becomes a branching, exploratory narrative. Type or speak a dream fragment, walk through scenes the dream weaver generates, make choices that shape where the dream goes, and end with a journal-voice interpretation reflecting on what your choices revealed.

## How It Works

1. **Input** — type or speak a dream fragment (Whisper transcribes voice input on the HF Space)
2. **Opening scene** — Llama 3.2 3B generates an atmospheric opening passage from the fragment
3. **Branch** — at each node, the user picks from generated choices; the story evolves based on the path taken
4. **Depth** — branching continues up to 4 levels deep
5. **Closing scene** — the final scene wraps the narrative arc
6. **Journal interpretation** — a reflective journal-voice passage comments on what the user's choices revealed

## Architecture
User input (text or voice)
↓
Whisper base (voice → text, runs on HF Space)
↓
Modal A10G endpoint (persistent)
↓
Llama 3.2 3B Instruct
→ Opening scene generation
→ Branching choice generation
→ Closing scene
→ Journal interpretation
↓
Gradio frontend (gr.State manages branching depth)

## Key Design Decisions

**Why a persistent Modal endpoint?**  
HF Spaces free tier CPUs are far too slow for generative inference. Serving Llama 3.2 3B on a Modal A10G as a persistent endpoint keeps response times fast enough to maintain narrative immersion — cold starts would break the experience.

**Why Whisper on the HF Space rather than Modal?**  
Whisper base is small enough to run on CPU without painful latency. Keeping it on the Space avoids an extra network hop and simplifies the architecture.

**Why manage branching state in `gr.State`?**  
The branching tree needs to survive across Gradio interactions without a backend database. `gr.State` holds the full path history per session — lightweight and zero infrastructure overhead for a hackathon project.

## Tech Stack

| Component | Tool |
|-----------|------|
| LLM | Llama 3.2 3B Instruct |
| Inference | Modal (A10G GPU endpoint) |
| Voice input | Whisper base |
| Frontend | Gradio (custom eerie-liminal theme) |
| State management | gr.State |
| Deployment | HuggingFace Spaces |

---
**Tech Stack:** Python, Llama 3.2 3B, Modal, Whisper, Gradio, HuggingFace Spaces