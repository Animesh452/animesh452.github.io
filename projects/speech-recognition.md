---
layout: page
title: Speech Recognition Model Optimization
permalink: /projects/speech-recognition/
---

# Speech Recognition Model Optimization

## Tech Stack

**Tech Stack:** Python, TensorFlow, PyTorch, CNNs, LSTMs, Transformers, Attention Mechanisms

## Overview
This project explores and compares multiple deep learning architectures for speech command recognition. The objective was to evaluate how different sequence modeling approaches perform on short audio commands and to understand the trade-offs between accuracy, model complexity, and generalization.

The work focuses on systematic experimentation rather than deploying a single model, with an emphasis on architectural choices and attention mechanisms.

## Problem
Speech recognition tasks must handle variability in speakers, accents, background noise, and recording conditions. Traditional architectures capture local or temporal features well, but may struggle to model long-range dependencies effectively.

This project investigates how modern transformer-based architectures compare against CNNs and RNN-based models for speech command classification.

## Approach
The pipeline follows a consistent evaluation framework across models:

- **Data Processing:**  
  Audio signals were converted into time–frequency representations (e.g., spectrograms / MFCCs) for model input.
- **Model Architectures:**
  - Convolutional Neural Networks (CNNs) for local pattern extraction
  - Long Short-Term Memory networks (LSTMs) for temporal modeling
  - Transformer-based models with attention mechanisms for global context
- **Training & Evaluation:**  
  Models were trained under comparable settings to ensure fair comparison, with hyperparameters tuned for stability and performance.

## Results
- **Best Performance:** Transformer-based model achieved **94.03% accuracy**.
- Attention mechanisms improved robustness to temporal variations in speech.
- CNNs performed efficiently with lower computational cost but slightly lower accuracy.
- LSTMs captured temporal dependencies well but were more sensitive to sequence length and noise.

## Learnings
- Attention-based models provide strong gains for short audio sequence modeling.
- Architectural choice has a significant impact even when using the same input representations.
- Transformers offer superior performance but require careful regularization and tuning.
- Model comparison under consistent conditions is critical for meaningful conclusions.

## Limitations & Future Work
- Evaluate robustness under noisy and real-world audio conditions.
- Explore lightweight transformer variants for edge deployment.
- Extend to continuous speech recognition and multilingual datasets.
- Analyze model interpretability for attention-based predictions.

## Resources
- Project report / notebooks — *to be linked*
