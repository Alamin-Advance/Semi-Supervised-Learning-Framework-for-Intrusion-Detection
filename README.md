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
## Dataset Information
- **Dataset Name:** UNSW-NB15
- **Source:** UNSW Canberra Cyber Centre
- **URL:** https://research.unsw.edu.au/projects/unsw-nb15-dataset
- **Total Records:** 257,673 (175,341 training + 82,332 testing)
- **Features:** 45 (including protocol, service, state, attack category)
- **Classes:** Binary (0 = Normal, 1 = Attack)

The dataset is publicly available and does not require any license for research use. Users must cite the original dataset paper (Moustafa & Slay, 2015).

## Code Information
The following notebooks are included:

| File | Description |
|------|-------------|
| `Active_Learning.ipynb` | Implements active learning with uncertainty sampling (entropy) using scikit-activeml |
| `Co_Training model.ipynb` | Implements co-training with two feature views using Random Forest and XGBoost |
| `Self_Training model.ipynb` | Implements self-training with confidence-based pseudo-labeling using Random Forest |

## Usage Instructions

### Step 1: Download the Dataset
1. Download the UNSW-NB15 dataset from the official source.
2. Place the files in a folder named `UNSW Datasets`:
   - `UNSW_NB15_training-set.csv`
   - `UNSW_NB15_testing-set.csv`

### Step 2: Set Up Google Colab or Local Environment
1. Open the notebooks in Google Colab or Jupyter Notebook.
2. If using Colab, mount your Google Drive to access the dataset.
3. If using locally, update the file paths in the notebooks accordingly.

### Step 3: Run the Notebooks
1. Open the notebook for the method you want to run.
2. Run all cells sequentially.
3. The output will show:
   - Classification reports (precision, recall, F1-score)
   - Confusion matrix
   - AUC score
   - Validation and test accuracies

### Step 4: Adjust Labeled Data Percentage
In each notebook, you can change the `labeled_percentage` variable to test different label ratios:
- `0.01` for 1% labeled data
- `0.05` for 5% labeled data
- `0.10` for 10% labeled data
- `0.20` for 20% labeled data
- `0.50` for 50% labeled data

## Requirements
The code requires the following Python libraries:
python>=3.8
pandas>=1.3
numpy>=1.21
scikit-learn>=1.0
xgboost>=1.5
scikit-activeml>=0.6
matplotlib>=3.5
shap>=0.40 (for XAI interpretation)

text

Install all dependencies using:
pip install pandas numpy scikit-learn xgboost scikit-activeml matplotlib shap

text

## Methodology
The following steps describe the methodology implemented in the code:

1. **Data Preprocessing:**
   - Load training and testing datasets
   - Concatenate and shuffle data
   - Balance classes using random oversampling
   - Encode categorical features using LabelEncoder
   - Normalize features using MinMaxScaler
   - Split data into training (80%), validation (10%), and test (10%)

2. **Active Learning:**
   - Initialize Random Forest classifier
   - Use entropy-based uncertainty sampling to query the most informative samples
   - Iteratively label samples and retrain the classifier
   - Evaluate on validation and test sets

3. **Self-Training:**
   - Split data into labeled and unlabeled sets
   - Train base Random Forest classifier on labeled data
   - Iteratively pseudo-label high-confidence unlabeled samples
   - Retrain the classifier and evaluate performance

4. **Co-Training:**
   - Split features into two independent views using ShuffleSplit
   - Train Random Forest on view 1 and XGBoost on view 2
   - Use each classifier to pseudo-label confident samples for the other
   - Retrain both classifiers iteratively
   - Evaluate on validation and test sets

5. **Evaluation:**
   - Compute accuracy, precision, recall, F1-score, and AUC
   - Generate confusion matrices
   - Compare performance across different label ratios (1%, 5%, 10%, 20%, 50%)

## Citations
**Dataset:**
Moustafa, N., & Slay, J. (2015). UNSW-NB15: A comprehensive data set for network intrusion detection systems (UNSW-NB15 network data set). In 2015 Military Communications and Information Systems Conference (MilCIS) (pp. 1-6). IEEE.

**Libraries:**
- Pedregosa, F., et al. (2011). Scikit-learn: Machine Learning in Python. JMLR, 12, 2825-2830.
- Chen, T., & Guestrin, C. (2016). XGBoost: A Scalable Tree Boosting System. In Proceedings of the 22nd ACM SIGKDD (pp. 785-794).
- Trittenbach, H., et al. (2022). scikit-activeml: A Library for Active Learning. Journal of Machine Learning Research, 23(1), 1-6.

## License
This code is provided for research purposes only. Redistribution and use in source and binary forms, with or without modification, are permitted provided that the original authors are credited.
