---
layout: page
title: Emotion Detection using Computer Vision
permalink: /projects/emotion-detection/
---

# Emotion Detection using Computer Vision

## Tech Stack

**Tech Stack:** Python, OpenCV, Deep Learning, CNNs

## Overview
This project explores facial emotion detection using computer vision and deep learning techniques. The goal was to classify human emotions from facial expressions in images or video frames, focusing on understanding the challenges involved in affective computing tasks.

The project serves as an exploratory study into emotion recognition rather than a production-ready system.

## Problem
Facial emotion recognition is challenging due to:
- Subtle variations in expressions
- Differences across individuals and cultures
- Sensitivity to lighting, pose, and occlusion

Accurately mapping facial features to discrete emotional categories requires robust feature extraction and generalization.

## Approach
- **Face Detection:**  
  Detected and cropped facial regions using classical computer vision techniques.
- **Feature Learning:**  
  Trained convolutional neural networks to learn discriminative facial features associated with basic emotions (e.g., happy, sad, angry, surprised).
- **Training Setup:**  
  Used labeled facial expression datasets with standard preprocessing and augmentation to improve generalization.
- **Evaluation:**  
  Model performance was analyzed across different emotion classes to identify confusion patterns.

## Results
- Achieved reasonable classification accuracy on basic emotion categories.
- Performance varied across emotions, with visually distinct expressions being easier to classify.
- Highlighted common failure modes in emotion recognition, such as confusion between similar expressions.

## Learnings
- Emotion detection is highly sensitive to data quality and diversity.
- Simple CNN architectures can capture basic facial cues but struggle with subtle emotions.
- Bias and subjectivity are important considerations in affective computing systems.
- Evaluation beyond raw accuracy is necessary to understand real-world performance.

## Limitations & Future Work
- Expand datasets to improve diversity and reduce bias.
- Explore temporal models using video sequences instead of static frames.
- Investigate multimodal emotion recognition (audio + visual cues).
- Study ethical implications and responsible use of emotion recognition systems.

## Resources
- Project report / experiments — *to be linked*
