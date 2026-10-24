# Explainable Machine Learning for Multi-Class Cancer Classification

An explainable machine learning pipeline for classifying **33 cancer types from gene-expression data**. The project combines gene-level feature selection, Random Forest and XGBoost classification, model comparison, SHAP-based explainability, and prediction-confidence analysis.

## Project overview

The main objective is to develop a machine learning workflow that can classify cancer types from high-dimensional gene-expression data while also identifying the genes that contribute most to model predictions.

The pipeline includes:

1. Gene-expression data exploration and preprocessing
2. Matching gene-expression samples with cancer labels
3. Feature selection from approximately 20,530 genes
4. Selection of the final **2,000 genes**
5. Multi-class cancer classification
6. Random Forest and XGBoost model comparison
7. SHAP-based feature importance analysis
8. Confusion-matrix analysis
9. Prediction-confidence analysis
10. Export of final results and model artifacts

## Dataset

| Property | Value |
|---|---:|
| Samples | 11,014 |
| Unique genes | 20,530 |
| Cancer types | 33 |
| Training samples | 8,811 |
| Test samples | 2,203 |
| Selected genes | 2,000 |

The classification task contains 33 cancer categories.

## Methodology

### 1. Data preparation

Gene-expression data and cancer labels are loaded and matched at the sample level. The resulting dataset is prepared for multi-class classification.

### 2. Feature selection

The original gene-expression space contains approximately 20,530 genes. A feature-selection process was used to reduce the dimensionality to **2,000 selected genes** for the final machine learning models.

### 3. Model development

Two tree-based machine learning models were evaluated:

- Random Forest
- XGBoost

Both models were evaluated on the same test set containing **2,203 samples**.

### 4. Explainable AI

SHAP was used to examine the contribution of individual genes to model predictions.

The analysis produced gene-level importance rankings and identified genes that were consistently important across models.

Among the compared top-gene lists, **CDX2** and **TSHR** were common to both models.

## Model performance

The final test-set comparison was:

| Model | Accuracy | Balanced Accuracy | Macro F1 | Weighted F1 |
|---|---:|---:|---:|---:|
| Random Forest | 0.9433 | 0.9108 | 0.9088 | 0.9402 |
| **XGBoost** | **0.9501** | **0.9142** | **0.9141** | **0.9468** |

XGBoost achieved the higher score across all four reported evaluation metrics.

### XGBoost test results

- Test samples: **2,203**
- Correct predictions: **2,093**
- Incorrect predictions: **110**
- Accuracy: **95.01%**

The results correspond to an error rate of approximately **4.99%** on the test set.

## Prediction confidence

The final XGBoost predictions were also evaluated by prediction confidence.

| Prediction category | Count | Percentage | Mean confidence |
|---|---:|---:|---:|
| Correct | 2,093 | 95.01% | 0.9814 |
| Incorrect | 110 | 4.99% | 0.7490 |

The model therefore showed substantially higher average confidence for correct predictions than for incorrect predictions.

## Explainable AI results

SHAP analysis was used to rank genes according to their mean absolute SHAP contribution.

Examples of highly ranked genes in the overall SHAP analysis included:

- PAX8
- PA2G4P4
- UTF1
- OR2D3
- NKX2-1
- PRO1768
- TSHR
- TG
- CDX2
- LOC407835

The SHAP ranking provides a model-based view of which genes contribute most strongly to the classification decisions.

## Cancer-type performance

Performance was also examined separately across cancer types.

Several cancer categories achieved perfect or near-perfect classification performance, while lower-performing categories showed more confusion between classes.

Examples of higher-performing categories included:

- GBM
- UVM
- LGG
- LAML
- THYM
- THCA
- TGCT
- PRAD
- OV

Examples of comparatively difficult categories included:

- READ
- CHOL
- KICH
- UCS
- ESCA

The class-level results are included in the generated classification reports and confusion matrices.

## Visualizations

The repository contains model evaluation visualizations, including:

- Random Forest vs XGBoost performance comparison
- XGBoost confusion matrix
- Normalized XGBoost confusion matrix
- SHAP feature-importance analysis

The final visual outputs are available in the [`results`](results/) directory.

## Repository structure

```text
cancer-gene-xai/
│
├── notebooks/
│   └── 01_data_exploration.ipynb
│
├── results/
│   ├── FINAL_XGBoost_confusion_matrix_normalized.png
│   └── FINAL_model_comparison_full_scale.png
│
├── .gitignore
└── README.md
```

## Reproducibility

The main analysis notebook is available at:

[`notebooks/01_data_exploration.ipynb`](notebooks/01_data_exploration.ipynb)

The original high-dimensional dataset and generated model artifacts are excluded from the public repository through `.gitignore`.

## Limitations

This project evaluates machine learning classification performance on the available gene-expression dataset. The reported results should therefore be interpreted as computational model performance rather than clinical diagnostic performance.

The identified important genes represent model-associated features and should not automatically be interpreted as causal biomarkers or clinically validated cancer markers.

Further validation on independent datasets would be required before considering clinical applications.

## Technologies

- Python
- Jupyter Notebook
- Pandas
- NumPy
- Scikit-learn
- XGBoost
- SHAP
- Matplotlib

## Project status

**Completed**

The current repository contains the final analysis notebook, selected results, model comparison, and explainability outputs.