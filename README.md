## Title
A Hybrid Semi-Supervised Learning Framework for Interpretable Intrusion Detection Under Data Scarcity

## Description
This repository contains the code and implementation for the paper titled "A Hybrid Semi-Supervised Learning Framework for Interpretable Intrusion Detection Under Data Scarcity." The framework integrates three semi-supervised learning paradigms — active learning, co-training, and self-training — to build accurate intrusion detection models with minimal labeled data.

The code implements:
- Data preprocessing and feature engineering for the UNSW-NB15 dataset
- Random Forest as the primary classifier
- XGBoost as the supplemental co-training learner
- Active learning using uncertainty sampling (entropy-based)
- Self-training with confidence-based pseudo-labeling
- Co-training with two independent feature views
- Explainable AI (SHAP) for model interpretation
- Comprehensive evaluation metrics (accuracy, precision, recall, F1-score, AUC)
