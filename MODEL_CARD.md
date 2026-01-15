## Model Card – Heart Disease Risk Prediction

### 1. Overview

- **Model purpose**: Predict the likelihood that a patient has heart disease based on clinical measurements.
- **Intended use**: Educational and research exploration of clinical risk prediction, interpretability techniques (SHAP), and fairness analysis.
- **Not for clinical use**: This model **must not** be used to make real‑world medical decisions.

### 2. Data

- **Dataset**: UCI Heart Disease dataset (Cleveland subset) via OpenML.
- **Target variable**: Binary indicator of presence of heart disease.
- **Features** (examples): age, sex, chest pain type, resting blood pressure, cholesterol, fasting blood sugar, resting ECG, max heart rate, exercise‑induced angina, oldpeak (ST depression), slope, number of major vessels, thalassemia.
- **Population**: Patients undergoing evaluation for suspected heart disease; demographics are limited (e.g., sex, age), and may not represent the general population.

### 3. Modeling

- **Algorithms evaluated**:
  - Logistic Regression (baseline linear model)
  - Random Forest (tree‑based ensemble)
  - Gradient‑boosted or XGBoost‑type model (non‑linear ensemble)
- **Best model (example)**:
  - Chosen based on validation ROC‑AUC and calibration performance.
  - Hyper‑parameters tuned via stratified cross‑validation on the training set.

### 4. Performance (Example – fill with your actual results)

All metrics below are computed on the **held‑out test set**.

- **Discrimination**
  - ROC‑AUC: `<to fill>`
  - PR‑AUC: `<to fill>`
- **Threshold‑dependent metrics** (at selected operating point)
  - Threshold: `<to fill>`
  - Sensitivity (Recall for positive class): `<to fill>`
  - Specificity: `<to fill>`
  - F1‑score: `<to fill>`
- **Calibration**
  - Brier score: `<to fill>`
  - Calibration curve plotted in the notebook.

### 5. Interpretability

- **Global explanations**
  - Feature importances from tree‑based model(s) and/or permutation importance.
  - Logistic regression coefficients indicating direction and magnitude of effects.
  - Clinically plausible key predictors typically include age, sex, chest pain type, ST‑segment measurements, and exercise‑induced angina.
- **Local explanations**
  - SHAP values computed for 3–5 representative patients.
  - Visualizations (e.g., force plots, bar plots) highlight which features drive each individual prediction.

### 6. Fairness & Subgroup Analysis

- **Subgroup evaluated**: Sex (male vs female) – derived from the `sex` feature in the dataset.
- **Metrics per subgroup** (example placeholders, fill with results):
  - ROC‑AUC (male / female)
  - Sensitivity and specificity at the chosen threshold
  - F1‑score
- **Observed issues**:
  - Note any meaningful performance gaps between subgroups.
  - Discuss potential reasons (e.g., sample size differences, historical bias in data collection).

### 7. Ethical Considerations & Limitations

- **Data limitations**
  - Historical, single‑center dataset with limited demographic diversity.
  - Potential measurement and selection bias (patients likely already suspected of heart disease).
  - Limited or no information on race/ethnicity, socioeconomic status, or comorbidities.
- **Model limitations**
  - Trained on a relatively small dataset; performance estimates may be unstable.
  - Risk of overfitting despite cross‑validation.
  - May not generalize to other hospitals, countries, or to screening populations.
- **Privacy**
  - Dataset is de‑identified and publicly available; no direct identifiers are used.
  - Users of this repository should still follow local data governance policies.
- **Non‑diagnostic disclaimer**
  - The model is for research and teaching only.
  - It does not replace clinician judgment or institutional protocols.

### 8. Threshold Optimization (Bonus)

- **Clinical operating point**:
  - Example goal: maximize **sensitivity** subject to **specificity ≥ X** (e.g., 0.85 or 0.90).
- **Result**:
  - Selected threshold: `<to fill>`
  - Achieved sensitivity: `<to fill>`
  - Achieved specificity: `<to fill>`
- **Rationale**:
  - In many screening or triage settings, missing true cases (false negatives) can be more harmful than additional work‑up for false positives, so higher sensitivity may be prioritized within an acceptable false‑positive rate.

### 9. Intended Users and Uses

- **Intended users**:
  - Students learning about ML in healthcare.
  - Researchers exploring modeling, interpretability, and fairness workflows.
- **Appropriate use**:
  - Education, prototyping, and methodological research.
- **Inappropriate use**:
  - Direct clinical decision‑making or patient triage.
  - Deployment in real‑world healthcare settings without rigorous validation, clinical trials, and regulatory approval.


