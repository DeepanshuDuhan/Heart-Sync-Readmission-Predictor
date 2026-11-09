# Heart Sync – 30-Day Heart Failure Readmission Predictor

An end-to-end machine learning project that predicts the likelihood of 30-day hospital readmission among heart failure patients using clinical data derived from the MIMIC-III database.

## Project Overview

Heart failure readmissions place a significant burden on healthcare systems. This project explores how machine learning can help identify patients at risk of readmission within 30 days of discharge.

The project covers data preprocessing, feature engineering, model development, hyperparameter optimization, model evaluation, and explainability using SHAP.

## Objectives

- Predict 30-day readmission among heart failure patients.
- Explore clinical and administrative features associated with readmission.
- Compare multiple machine learning models.
- Optimize model performance using Optuna.
- Interpret model predictions using SHAP.

## Dataset

- **Source:** MIMIC-III (Medical Information Mart for Intensive Care III).
- **Task:** Binary classification.
- **Target:** Readmission within 30 days (Yes/No).

*Note: The project uses prepared and processed data derived from MIMIC-III.*

## Methodology

1. **Data Preparation:** Cohort selection, data cleaning, and missing-value handling.
2. **Feature Engineering:** Preparation of clinical, demographic, diagnosis, and administrative features.
3. **Preprocessing:** Transformation of numerical and categorical variables.
4. **Model Development:** Training and comparison of Logistic Regression, Random Forest, and XGBoost.
5. **Hyperparameter Tuning:** Optuna-based optimization of XGBoost.
6. **Threshold Selection:** Selection of a classification threshold using validation data.
7. **Evaluation:** Assessment using Accuracy, Precision, Recall, F1-score, ROC-AUC, and Average Precision.
8. **Explainability:** SHAP analysis to understand the features influencing model predictions.

## Final Model Performance

The Optuna-tuned XGBoost model achieved the following results on the held-out test set:

| Metric | Score |
|---|---:|
| Accuracy | 75.30% |
| Precision | 24.48% |
| Recall | 57.23% |
| F1-Score | 34.30% |
| ROC-AUC | 75.51% |
| Average Precision | 26.77% |

### Confusion Matrix

| | Predicted: No Readmission | Predicted: Readmission |
|---|---:|---:|
| Actual: No Readmission | 1901 | 549 |
| Actual: Readmission | 133 | 178 |

The model identifies approximately 57% of actual readmissions at the selected classification threshold. The relatively low precision indicates that many predicted readmissions are false positives.

## Model Explainability – SHAP

SHAP (SHapley Additive exPlanations) was used to interpret model predictions and identify influential features.

The analysis highlighted features such as:

- Discharge location
- Abnormal laboratory events
- Admission type
- Diagnosis-related features

These findings represent model associations and should not be interpreted as causal relationships.

## Technologies Used

- **Programming:** Python
- **Data Analysis:** Pandas, NumPy
- **Visualization:** Matplotlib
- **Machine Learning:** Scikit-learn, XGBoost
- **Hyperparameter Optimization:** Optuna
- **Explainable AI:** SHAP
- **Environment:** Google Colab

## Repository Structure

```text
Heart-Sync-Readmission-Predictor/
│
├── notebooks/
│   └── Heart_Sync_Final.ipynb
│
├── README.md
└── .gitignore
```

## Limitations

- The model is a research and educational prototype, not a clinically validated decision-support system.
- Discharge location is known at discharge; therefore, the model is intended for discharge-time risk assessment rather than admission-time prediction.
- Model performance and generalizability require further validation on independent datasets.
- SHAP explanations identify model behavior, not causal relationships.

## Future Improvements

- Validate the model on independent patient populations.
- Explore additional clinical features and temporal information.
- Improve precision while maintaining clinically meaningful recall.
- Investigate calibration and decision-curve analysis.
- Evaluate deployment feasibility in a clinical workflow.

## Disclaimer

This project is intended solely for educational and research purposes. It is not intended to replace professional medical judgment or be used for clinical decision-making.
