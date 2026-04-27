---
layout: page
title: Mobile Edge Computing — DDQN Task Scheduling
permalink: /projects/mobile-edge-ddqn/
---

# Mobile Edge Computing — DDQN Task Scheduling

## Tech Stack

**Type:** Research proposal / conceptual project  
**Tech Stack (proposed):** Python, TensorFlow/PyTorch, OpenAI Gym (or custom simulator), ns-3 (or other network simulator), Docker/Kubernetes for deployment experiments

## Overview
This project investigates energy-efficient task scheduling for mobile edge computing using reinforcement learning. The goal is to design an agent that learns to allocate computation tasks across mobile/edge/cloud resources to minimize energy consumption while meeting latency and QoS constraints.

Although this work began as a conceptual/idea paper and design study rather than a fully deployed system, it captures a concrete research direction and experimental plan suitable for later implementation and evaluation.

## Problem

### Motivation
Mobile devices and edge servers increasingly run computation-heavy workloads (inference, preprocessing, analytics). Static scheduling policies either overprovision (waste energy) or underperform (miss latency targets). A data-driven RL approach can adapt to changing load, network conditions, and device states to make smarter scheduling decisions.

## Approach

### Proposed Approach
- **Problem formulation:** Model scheduling as a Markov Decision Process where the agent observes device/edge resource states (CPU, memory, battery, network RTT) and incoming task characteristics (size, deadline, priority) and selects placement and resource allocations.
- **Agent & Algorithm:** Double Deep Q-Network (DDQN) with a compact state representation and an action space encoding offload/execute decisions plus resource allocation knobs.
- **Reward design:** Multi-objective reward combining negative energy consumption, penalty for missed deadlines, and small regularization for switching costs.
- **Simulation & Environment:** Build a custom environment (or extend an existing simulator) that simulates heterogeneous mobile devices, network variability, and an edge server cluster. Use this to train and evaluate the DDQN agent.
- **Baseline comparisons:** Rule-based heuristics (round-robin, minimum-latency-first), myopic greedy strategies, and a standard DQN baseline.
- **Training stability:** Use prioritized experience replay, reward clipping, and target network updates to stabilize training. Tune hyperparameters via grid search or Bayesian optimization.

## Results

### Evaluation Plan
- **Metrics:** Average energy per task, task success rate (deadline met), average latency, and overall system throughput.
- **Scenarios:** Vary workloads (bursty vs steady), device battery levels, and network conditions (LTE/5G/unreliable).
- **Ablations:** Remove reward components or simplify state representation to measure their impact; compare DDQN vs DQN vs heuristics.
- **Deployment experiment (optional):** Small-scale testbed using Docker containers on heterogeneous VMs to measure real network/CPU effects.

## Learnings

### Expected Impact & Learnings
- Showcases how reinforcement learning can produce robust and adaptive scheduling policies for energy-critical edge settings.
- Balances theoretical RL design with practical systems constraints (latency, limited observation, partial observability).
- Provides a reproducible experimental framework that can be extended into a full implementation and publishable study.

## Limitations & Future Work

### Limitations & Next Steps
- The action space and state dimensionality must be carefully constrained to keep learning tractable.
- Partial observability (e.g., unknown network fluctuations) may require modifications such as recurrent networks or POMDP techniques.
- Next steps: build the simulator, implement DDQN agent, run baseline comparisons, and publish results.

## Resources
