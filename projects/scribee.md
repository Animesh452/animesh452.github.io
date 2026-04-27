---
layout: page
title: Scribee — Speech to Braille & Hand Sign Recognition
permalink: /projects/scribee/
---

# Scribee — Speech to Braille & Hand Sign Recognition

## Tech Stack

**Tech Stack:** Streamlit, MediaPipe, TensorFlow/Keras (LSTM), AssemblyAI (speech transcription), Python, Docker (optional)

## Overview
Scribee is an assistive-technology project that converts spoken audio into Braille images and recognizes hand signs for alphabetic sign language. It combines practical engineering (Streamlit UI, Docker orchestration) with machine learning (LSTM-based sign recognition) and production-ready transcription services to create an end-to-end accessibility tool.

The project has two primary components:
1. **Speech → Braille:** upload or record audio, transcribe it, convert the resulting text to Braille dot patterns, and render the Braille as PNG pages for download or display.  
2. **Hand Sign Recognition:** live webcam video processed with MediaPipe Holistic to extract hand landmarks; sequences of keypoints are fed to an LSTM model trained to classify letters (A–Z).

## Problem

## Approach

### Key features
- **Interactive UI:** Streamlit web app with modes for Speech→Braille and Video (real-time sign recognition).  
- **High-quality transcription:** Uses AssemblyAI for robust speech-to-text transcription (upload/poll flow) and saves transcripts for conversion into Braille. 
- **Braille rendering engine:** A `Paper` class maps characters to Braille dot patterns and produces paginated PNG outputs for the entire transcript.   
- **Sign language model:** MediaPipe extracts 42 hand landmarks (left + right) per frame; a 30-frame sequence is used as an input to a stacked-LSTM classifier (trained weights: `Trained_on_all_letters.h5`) to predict alphabetic signs with a stabilizing voting logic.   
- **Post-processing:** Spell-correction is applied to assembled letters to form likely words (improves UX for noisy predictions). 

### Implementation notes
- The app supports **recorded audio upload** and in-browser recording; uploaded files are sent to AssemblyAI via chunked upload, transcribed, polled until completion, and the transcript is saved locally before conversion to Braille PNG pages.  
- Hand sign recognition uses MediaPipe Holistic for landmark extraction and a Keras LSTM model for sequence classification; the UI displays the current letter and the word being formed in real time. 

## Results

### Evaluation & usage
- The project is primarily a functional demo for accessibility workflows. For sign recognition, a trained model exists (weights referenced in the code) — classification stability uses thresholding + short-term consensus to reduce spurious predictions. 
- Suggested evaluation metrics for future work: WER for speech transcription, per-class accuracy and confusion matrices for sign recognition, end-to-end user time saved in practical tests.

## Learnings

> **Short note:** This project is a collaborative team effort focused on accessibility. It demonstrates full-stack engineering (UI, APIs, ML, model serving) and a thoughtful approach to real user problems.

## Limitations & Future Work

### Privacy & security
- The transcription uses an external API (AssemblyAI). **Do not** publish API keys in the repository. The code should be updated to read keys from environment variables and not from literals. (If the key was ever committed, rotate it immediately.)

### Limitations & next steps
- Improve multi-speaker handling and noisy environments for transcription.  
- Add speaker diarization and diarized braille output (optional).  
- Expand sign recognition to full words or phrases (sequence models / language model fusion).  
- Provide downloadable model weights via Releases or cloud storage and add a small demo video or GIF for the site.

## Resources
- Repo : [Scribee](https://github.com/mustafa-droid18/Scribee.git)
