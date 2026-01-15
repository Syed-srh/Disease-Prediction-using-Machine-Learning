# Disease Prediction using Machine Learning – Heart Disease Analysis

This notebook (`Intern.ipynb`) implements a complete machine learning pipeline for predicting heart disease using the UCI Heart Disease dataset, with comprehensive evaluation, interpretability, and fairness analysis.

## Overview

This project demonstrates best practices in clinical machine learning, including:

- **Data preprocessing** with proper train/validation/test splits
- **Multiple model training** (Logistic Regression, Random Forest, XGBoost)
- **Hyperparameter tuning** using cross-validation
- **Comprehensive evaluation** with multiple metrics
- **Model interpretability** using SHAP
- **Fairness analysis** across demographic subgroups
- **Threshold optimization** for clinical operating points

## Dataset

- **Source**: UCI Heart Disease dataset (via OpenML)
- **Size**: 303 patients, 13 features
- **Task**: Binary classification (presence/absence of heart disease)
- **Features**: Age, sex, chest pain type, resting blood pressure, cholesterol, fasting blood sugar, resting ECG, maximum heart rate, exercise-induced angina, ST depression, slope, number of vessels, thalassemia

## Key Results

Based on the notebook execution:

- **Best Model**: Random Forest (selected by validation ROC-AUC)
- **Test Performance**:
  - ROC-AUC: 0.876
  - PR-AUC: 0.895
  - F1 Score: 0.800
  - Sensitivity: 0.848
  - Specificity: 0.679
  - Brier Score: 0.1459

- **Optimized Threshold** (specificity ≥ 0.90):
  - Threshold: 0.66
  - Sensitivity: 0.606
  - Specificity: 0.929

## Requirements

Install the required Python packages:

```bash
pip install numpy pandas matplotlib seaborn scikit-learn xgboost imbalanced-learn shap
```

Or use the `requirements.txt` from the main project directory if available.

## Usage

1. **Open the notebook**:
   ```bash
   jupyter notebook Intern.ipynb
   ```

2. **Run all cells** sequentially from top to bottom.

3. **Key sections**:
   - **Cell 1**: Import libraries and set random seed for reproducibility
   - **Cell 2**: Load dataset from OpenML
   - **Cell 3**: Create train/validation/test splits (60/20/20)
   - **Cell 4**: Define preprocessing pipeline
   - **Cell 5**: Define evaluation helper functions
   - **Cell 6**: Train and tune three models (Logistic Regression, Random Forest, XGBoost)
   - **Cell 7**: Evaluate models and select best performer
   - **Cell 8**: Generate calibration curve and compute Brier score
   - **Cell 9**: Visualize global feature importance
   - **Cell 10**: Generate SHAP explanations for individual predictions
   - **Cell 11**: Analyze fairness across sex subgroups

## Reproducibility

- Random seed is set to `42` throughout the notebook
- All data splits, model training, and resampling use this seed
- Run cells in order from a fresh kernel for consistent results

## Model Interpretability

The notebook includes:

1. **Global explanations**: Feature importance plots showing which features drive predictions overall
2. **Local explanations**: SHAP values for 5 individual test cases, showing feature contributions to specific predictions
3. **Clinical plausibility**: Discussion of whether important features align with known medical risk factors

## Fairness Analysis

The notebook evaluates model performance separately for:
- **Male patients** (n=42 in test set)
- **Female patients** (n=19 in test set)

Metrics are compared across subgroups to identify potential disparities.

## Important Notes

- **This is a research/educational project only** – not for clinical use
- The dataset is small (303 patients), which limits generalizability
- Results should be interpreted with caution and not used for medical decision-making
- For production use, external validation on independent datasets would be required

## Outputs

The notebook generates:
- ROC and Precision-Recall curves
- Calibration plots
- Feature importance visualizations
- SHAP beeswarm and bar plots
- Performance metrics tables
- Subgroup analysis results

## References

- UCI Heart Disease Dataset: Available via OpenML (`heart-disease`)
- SHAP: Lundberg & Lee (2017), "A Unified Approach to Interpreting Model Predictions"
- SMOTE: Chawla et al. (2002), "SMOTE: Synthetic Minority Over-sampling Technique"

---

**Disclaimer**: This notebook is for educational and research purposes only. The models and results must not be used for clinical diagnosis or treatment decisions. Only qualified healthcare professionals should make medical decisions.


