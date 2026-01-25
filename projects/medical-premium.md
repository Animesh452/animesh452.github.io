---
layout: page
title: Medical Premium Prediction System
permalink: /projects/medical-premium/
---

# Medical Premium Prediction System

**Tech Stack:** Python, pandas, scikit-learn, XGBoost, SHAP, matplotlib, seaborn

## Overview
This project focuses on predicting medical insurance premiums using health and demographic factors. The goal was to build an accurate and interpretable machine learning model that captures non-linear relationships between risk factors while maintaining transparency in decision-making.

The system was developed as part of an academic project and emphasizes both predictive performance and model interpretability.

## Approach
A structured end-to-end machine learning pipeline was implemented, covering data preprocessing, feature engineering, model training, and evaluation.

- **Dataset:** Publicly available health insurance dataset (Kaggle)
- **Size:** ~986 records with demographic and medical attributes
- **Feature Engineering:**
  - BMI categorization
  - Risk scoring based on medical history
  - Premium tier segmentation
- **Models Evaluated:**
  - Linear Regression
  - Random Forest
  - XGBoost
- **Model Selection:** Hyperparameter tuning using GridSearchCV

Special emphasis was placed on interpretability using SHAP values to understand feature contributions to individual predictions.

## Results
- **Best Model:** Tuned Random Forest
- **Test R² Score:** **0.8887 (88.87%)**
- **Training R²:** 0.9193
- **RMSE:** ₹2,179
- **Key Influential Features:**
  - Age
  - Number of surgeries
  - Medical conditions
  - BMI category

SHAP analysis revealed consistent and intuitive feature importance patterns, validating both the model’s performance and its reliability for real-world interpretation.

## Learnings
- Ensemble methods significantly outperform linear models for complex insurance risk modeling.
- Interpretability tools like SHAP are critical for trust in healthcare-related ML systems.
- Feature engineering had a larger impact on performance than model complexity alone.
- Proper evaluation across premium tiers helped identify bias and error concentration.

## Resources
- Project report (PDF) — *to be linked*
