# Fetal Health Classification using Cardiotocography Data

## Overview

This project aims to classify fetal health status—**normal** or **compromised**—based on features extracted from Cardiotocography (CTG) recordings. CTG is commonly used in obstetrics to monitor fetal heart rate (FHR) and uterine contractions during labor. Early identification of at-risk fetuses can guide timely clinical intervention and improve neonatal outcomes.

Two classical machine learning models were implemented and evaluated:

- **Logistic Regression (LR)**
- **Linear Discriminant Analysis (LDA)**

## Dataset

The dataset consists of:
- **185 labeled training samples** with 21 numerical features per sample, derived from 10-minute CTG segments.
- **Four test sets**, each containing 100 unlabeled samples with the same feature structure.

**Label Encoding:**
- `0`: Normal (healthy fetus)
- `1`: Compromised (at-risk fetus)

## Key Challenges

- **Small sample size**: Risk of overfitting
- **Class imbalance**: ~92.5% normal vs. ~7.5% compromised
- **Correlated features**: Violates assumptions of naive models

## Methods

### Preprocessing
- Mean imputation for missing values
- Z-score normalization
- Implemented using `scikit-learn` Pipelines to prevent data leakage during cross-validation

### Models
#### 1. Logistic Regression
- Chosen for simplicity and robustness
- Effective for linearly separable problems
- Provides interpretable coefficients and probabilistic outputs

#### 2. Linear Discriminant Analysis
- Selected to handle correlated features better than naive Bayes
- Assumes normally distributed features with equal class covariance
- Achieved perfect classification on validation sets

### Evaluation
- 5-fold stratified cross-validation
- Metrics: Accuracy, Precision, Recall, ROC-AUC, Confusion Matrix

## Results

| Model               | Accuracy | AUC   | Class 1 Recall |
|--------------------|----------|-------|----------------|
| Logistic Regression| 97.3%    | 0.9975| 0.83           |
| LDA                | 97.3%    | 1.000 | 1.00           |

LDA outperformed LR slightly, with perfect classification on the validation data. Both models generalized well and were consistent across folds.

## Reflections

If more data and compute resources were available:
- Explore **gradient boosting models** (e.g., XGBoost, LightGBM)
- Engineer **temporal features** from raw CTG signals
- Apply **model ensembling** and **Bayesian optimization**

## Repository Structure

