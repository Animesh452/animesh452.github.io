---
layout: page
title: Medical Premium Prediction System
---

# Medical Premium Prediction System

## Overview
Developed a comprehensive machine learning system to predict insurance premiums using health and demographic factors as part of CSE 475 Capstone project.

## Problem Statement
Insurance companies need accurate premium calculation methods that balance risk assessment with fair pricing. Traditional methods often lack the sophistication to handle complex feature interactions.

## Technical Implementation

### Data Processing
- **Dataset**: 986 records with 11 features
- **Features**: Age, BMI, medical conditions, surgery history
- **Engineering**: Created risk scores, BMI categories, premium tiers

### Model Development
- **Algorithms**: Linear Regression, Random Forest, XGBoost
- **Optimization**: GridSearchCV hyperparameter tuning
- **Best Model**: Tuned Random Forest (88.87% R²)

### Key Results
- **Training R²**: 0.9193
- **Test R²**: 0.8887  
- **RMSE**: ₹2,179
- **Feature Importance**: Age (primary factor), surgeries, medical conditions

## Technical Highlights
- SHAP analysis for model interpretability
- Comprehensive error analysis by premium tiers
- Deployment architecture with monitoring systems
- Ethical considerations and bias analysis

## Tools & Technologies
Python, pandas, scikit-learn, XGBoost, SHAP, matplotlib, seaborn

## Outcomes
Successfully demonstrated that ensemble methods significantly outperform linear approaches for insurance premium prediction, with clear interpretability through SHAP analysis.
