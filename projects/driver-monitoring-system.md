---
layout: page
title: Driver Monitoring System using Computer Vision
permalink: /projects/driver-monitoring-system/
---

# Driver Monitoring System using Computer Vision

**Tech Stack:** Python, OpenCV, TensorFlow, Keras, VGG16, Facial Landmark Detection

## Overview
This project presents a real-time driver monitoring system designed to detect signs of driver fatigue and unsafe behavior using computer vision and deep learning. The system aims to enhance road safety by continuously monitoring driver attentiveness and identifying risk patterns such as eye closure, yawning, and smoking.

This work culminated in a peer-reviewed research publication and was evaluated under real-world constraints for robustness and accuracy.

## Approach
The system processes live video streams to detect facial regions and extract meaningful behavioral cues.

- **Face & Landmark Detection:** Facial landmarks were extracted to localize eyes and mouth regions in real time.
- **Model Architecture:** A VGG16-based convolutional neural network was used for classification tasks.
- **Behavioral Classes:**
  - Eye closure (drowsiness detection)
  - Yawning
  - Smoking
- **Pipeline:**
  - Video frame preprocessing
  - Region-of-interest extraction
  - CNN-based classification
  - Temporal smoothing for stability

The design prioritized low latency and real-time performance to support continuous monitoring scenarios.

## Results
- **Closed-eye detection accuracy:** **92%**
- **Yawning detection accuracy:** **87%**
- **Smoking detection accuracy:** **89%**

The system demonstrated reliable performance across varying lighting conditions and driver appearances, validating its applicability for real-world deployment.

## Learnings
- Combining facial landmarks with CNNs significantly improves robustness over end-to-end image classification.
- Temporal consistency is essential for reducing false positives in behavioral detection.
- Model optimization is critical for real-time inference in safety-critical systems.
- Dataset diversity strongly impacts generalization in driver monitoring applications.

## Resources
- Research paper (Conference publication) — *to be linked*
