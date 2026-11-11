# Predicting Hospital Readmission in Diabetes Patients

Predictive modeling and exploratory data analysis of hospital readmissions using R and the Diabetes 130-US Hospitals dataset.

## Overview

This project analyzes factors associated with 30-day hospital readmission among patients with diabetes using approximately 71,500 patient encounters. The objective is to identify meaningful predictors of readmission, compare classification models, and evaluate their predictive performance.

The analysis was conducted in R using statistical analysis, data visualization, feature engineering, and machine learning.

## Project Deliverables

- **Reproducible R Markdown Notebook:** Complete analysis with executable R code, documented methodology, and rendered PDF report.
- **Exploratory Data Analysis:** Readmission distributions, missingness assessment, specialty comparisons, length-of-stay analysis, and predictor correlations.
- **Feature Engineering Pipeline:** Missing-value handling, categorical encoding, normalization, interaction terms, and class downsampling.
- **Model Comparison:** Four classification models trained and evaluated using stratified five-fold cross-validation.
- **Hyperparameter Optimization:** Tuned Elastic Net, Random Forest, and XGBoost; PCA-based preprocessing for LDA.
- **Model Evaluation:** Cross-validation ROC-AUC comparisons and final held-out test-set evaluation.
- **Feature Importance Analysis:** Ranked predictors identifying the relative contributions of healthcare utilization, clinical complexity, and demographic characteristics.

## Dataset

**Source:** Strack et al. (2014), *Diabetes 130-US Hospitals for Years 1999–2008*.

- Approximately 71,500 patient encounters analyzed.
- Hospital admission and discharge information.
- Clinical diagnoses and comorbidities.
- Medication prescriptions and changes.
- Healthcare utilization history.
- 30-day readmission outcome.

[UCI Machine Learning Repository](https://archive.ics.uci.edu/dataset/296/diabetes+130-us-hospitals+for+years+1999-2008)

## Methods

### Exploratory Data Analysis
- Examined readmission distributions and missingness.
- Compared readmission rates across physician specialties and hospital lengths of stay.
- Analyzed correlations between numerical predictors and readmission.
- Investigated relationships between healthcare utilization and clinical complexity.

### Data Preparation
- Stratified 75/25 training and testing split.
- Five-fold cross-validation on training data.
- Explicit handling of missing categorical values.
- One-hot encoding of categorical predictors.
- Feature normalization.
- Engineered interaction terms between healthcare utilization and clinical variables.
- Majority-class downsampling at a 10:1 ratio within cross-validation folds.

### Model Development

Four classification models were compared:

1. Elastic Net Logistic Regression
2. Linear Discriminant Analysis (LDA)
3. Random Forest
4. XGBoost

Hyperparameters were tuned using five-fold cross-validation, with ROC-AUC as the primary evaluation metric.

## Results

**Best-performing model: Random Forest**

- Test ROC-AUC: **0.695**
- Cross-validation ROC-AUC: approximately **0.67**
- Cross-validation fold variability: approximately **0.00680**
- Outperformed Elastic Net, LDA, and XGBoost in cross-validated ROC-AUC.

### Key Findings

Healthcare utilization and clinical complexity were more informative predictors than static demographic characteristics.

The strongest predictors included:
- Number of prior inpatient visits.
- Length of hospital stay.
- Number of recorded diagnoses.
- Medication burden.
- Laboratory procedures.
- Interactions between healthcare utilization and clinical complexity.

These findings suggest that cumulative disease burden and repeated healthcare engagement provide more predictive information about readmission than demographic characteristics alone.

## Technologies

- **Language:** R
- **Data Manipulation:** dplyr, tidyr
- **Visualization:** ggplot2
- **Modeling:** tidymodels, glmnet, ranger, xgboost, MASS
- **Feature Engineering:** recipes, themis
- **Model Evaluation:** ROC-AUC, cross-validation
- **Feature Importance:** vip

## Potential Extensions

- Evaluate additional gradient boosting methods, including LightGBM and CatBoost.
- Expand hyperparameter optimization.
- Investigate additional clinical and patient-level predictors.

## References

Strack, B., DeShazo, J. P., Gennings, C., Olmo, J. L., Ventura, S., Cios, K. J., & Clore, J. N. (2014). *Impact of HbA1c Measurement on Hospital Readmission Rates: Analysis of 70,000 Clinical Database Patient Records*. BioMed Research International, 2014, 781670.

Strack, B., et al. (2014). *Diabetes 130-US Hospitals for Years 1999–2008*. UCI Machine Learning Repository.
