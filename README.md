# Explainable Machine Learning for Multi-Class Cancer Classification

## Overview

This project develops an explainable machine learning pipeline for classifying cancer types from gene-expression data. The pipeline combines feature selection, machine learning classification, model comparison, and explainable AI to identify important genes associated with model predictions.

## Dataset

- Samples: **11,014**
- Unique genes: **20,530**
- Cancer types: **33**
- Training samples: **8,811**
- Test samples: **2,203**
- Selected genes: **2,000**

## Methodology

1. Load and clean the gene-expression and clinical label datasets.
2. Match gene-expression samples with their corresponding cancer labels.
3. Remove duplicated gene columns.
4. Split the data into stratified training and test sets.
5. Handle missing gene-expression values using statistics calculated from the training data.
6. Apply **SelectKBest with ANOVA F-test** to select 2,000 genes.
7. Train and evaluate Random Forest and XGBoost classifiers.
8. Compare model performance using accuracy, balanced accuracy, macro F1, and weighted F1.
9. Apply SHAP-based analysis to investigate model explanations and important genes.
10. Develop a prediction pipeline for new gene-expression samples.

## Model performance

| Model | Accuracy | Balanced Accuracy | Macro F1 | Weighted F1 |
|---|---:|---:|---:|---:|
| Random Forest | 94.33% | 91.08% | 90.88% | 94.02% |
| **XGBoost** | **95.01%** | **91.42%** | **91.41%** | **94.68%** |

XGBoost was selected as the final model because it achieved the stronger overall performance on the held-out test set.

## Test-set results

The final XGBoost model correctly classified **2,093 of 2,203 test samples**, corresponding to an accuracy of **95.01%**.

The model produced:

- Accuracy: **95.01%**
- Balanced accuracy: **91.42%**
- Macro F1: **91.41%**
- Weighted F1: **94.68%**

## Explainable AI

SHAP-based analysis was used to examine feature contributions and identify genes that were important to the Random Forest predictions. XGBoost feature importance was also analysed.

Examples of highly ranked genes included:

- PAX8
- PA2G4P4
- UTF1
- OR2D3
- NKX2-1
- TSHR
- TG
- CDX2

CDX2 and TSHR appeared among the highly ranked features in both analysed importance lists.

## Prediction application

The project includes a prediction pipeline that accepts new gene-expression samples and returns:

- Predicted cancer type
- Prediction confidence

The pipeline was verified using an unseen test sample and correctly predicted **MESO** with approximately **99.91% confidence**.

## Technologies

- Python
- Pandas
- NumPy
- Scikit-learn
- XGBoost
- SHAP
- Matplotlib
- Explainable AI
- Machine Learning
- Gene-expression analysis

## Project outputs

The project produces:

- Final model performance comparison
- Cancer-wise performance analysis
- XGBoost gene-importance results
- SHAP-based gene-importance results
- Confusion matrices
- Prediction-confidence analysis
- New-sample prediction pipeline
- Saved XGBoost application model

## Important note

The reported performance represents evaluation on the held-out dataset used in this project. The model should not be interpreted as a clinically validated diagnostic system.