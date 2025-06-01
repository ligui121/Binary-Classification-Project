# Fetal Health Classification with CTG Data

This project implements machine learning models to classify fetal health status—normal or compromised—based on features extracted from cardiotocography (CTG) recordings. It was developed as part of the ESE 588: Machine Learning for Signal Processing course at Stony Brook University.

## 📌 Overview

- **Course**: ESE 588 — Spring 2025  
- **Project**: Fetal Health Classification Using CTG  
- **Author**: Guoao Li  
- **Institution**: Stony Brook University  
- **Contact**: guoao.li@stonybrook.edu

## 🎯 Problem Statement

During labor, fetal heart rate (FHR) monitoring via CTG is critical to assess fetal well-being. Patterns in FHR signal characteristics can help identify fetuses at risk. The goal of this project is to develop a machine learning-based diagnostic tool to classify fetal status into:
- `0`: Normal (non-compromised)
- `1`: Compromised (at-risk)

## 📊 Dataset

- **Training Set**: 185 samples, 21 numerical features per sample (extracted from 10-minute FHR segments)
- **Test Set**: 4 unlabeled groups, each with 100 samples

### Dataset Challenges:
- Severe class imbalance (only 7.5% are compromised cases)
- Feature correlation violates naive independence assumptions
- Small dataset size increases risk of overfitting

## 🤖 Machine Learning Models

Two models were implemented and evaluated:
1. **Logistic Regression (Discriminative)**
   - Chosen for interpretability and robustness
   - Achieved AUC: 0.9975; CV Accuracy: 97.3%
2. **Linear Discriminant Analysis (Generative)**
   - Chosen for handling feature correlation better than Naive Bayes
   - Achieved AUC: 1.00; CV Accuracy: 97.3% (perfect classification on validation set)

## ⚙️ Implementation Details

### Preprocessing:
- Mean imputation for missing values
- Z-score standardization of features
- Pipelines used to avoid data leakage in cross-validation

### Evaluation:
- Stratified 5-fold cross-validation
- Metrics: Accuracy, Precision, Recall, Confusion Matrix, ROC-AUC

## 📈 Results

| Model                | CV Accuracy | AUC   | Class 1 Recall |
|---------------------|-------------|-------|----------------|
| Logistic Regression | 97.3%       | 0.9975| 0.83           |
| LDA                 | 97.3%       | 1.00  | 1.00           |

- **LDA** slightly outperformed LR, benefiting from assumptions matching the data structure.
- **Misclassification** in LR occurred near class boundaries.

## 🔍 Reflections

### What Could Be Improved:
- Increase training data for better generalization
- Engineer dynamic/temporal features from raw CTG
- Hyperparameter tuning or ensemble models for improved robustness

### Future Direction:
- Try **XGBoost** or **LightGBM** for better handling of class imbalance and non-linear patterns
- Further interpret feature importance for clinical insight

## 📁 File Structure
.
├── Code/
│ ├── Discriminative Model--Logistic Regression.ipynb
│ └── Generative Model--Linear Discriminant Analysis.ipynb
├── Data/
│ ├── Guoao_Li_Results.xlsx
│ ├── Test_Data_588_Project_Spring2025.xlsx
│ └── Training_Data_588_Project_Spring2025.xlsx
├── 588_Project_Spring_2025.pdf
├── ESE_588_Project_Report_Guoao_Li.pdf
└── README.md

## ▶️ How to Run

1. Open either JupyterLab or Jupyter Notebook.
2. Run the notebooks:
   - `Code/Discriminative Model--Logistic Regression.ipynb`
   - `Code/Generative Model--Linear Discriminant Analysis.ipynb`
3. Predictions are saved and formatted in `Guoao_Li_Results.xlsx` for submission.

## 📜 License

This project is for academic use in ESE 588 at Stony Brook University.

---



