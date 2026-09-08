# Pancreatic Cancer Detection Using Clinical Biomarkers

## Project Overview

Pancreatic cancer is one of the most challenging cancers to diagnose at an early stage, largely because symptoms often appear only after disease progression.

The objective of this project is to investigate whether clinical biomarkers can be used to accurately distinguish between healthy individuals, patients with benign pancreatic conditions, and patients with pancreatic cancer using machine learning techniques.

The project follows a complete data science workflow:

1. Exploratory Data Analysis (EDA)
2. Statistical Validation and Feature Engineering
3. Machine Learning Modelling
4. Model Explainability and Clinical Interpretation

---

## Dataset

The analysis uses a dataset containing **600 patient records** and **19 variables**, including demographic information and clinical biomarkers.

### Diagnosis Classes

 Class | Description |

 1 | Healthy 
 2 | Benign Pancreatic Disease 
 3 | Pancreatic Cancer 

### Biomarkers

- plasma_C
- creatinine
- LYVE1
- REG1A
- REG1B
- TFF1
- CA19_9
- CEA
- bilirubin
- glucose
- urine_volume
- urine_pH

Additional demographic variables:

- age
- sex

---

## Repository Structure

## Notebook 01 — Exploratory Data Analysis

The first notebook focuses on understanding the dataset structure and identifying potentially informative biomarkers.

### Main Findings

- Dataset contains **600 complete observations with no missing values**.
- Class distribution is relatively balanced:
  - Healthy: 256
  - Benign: 214
  - Cancer: 130
- Pancreatic cancer patients consistently showed higher concentrations of:
  - REG1A
  - REG1B
  - TFF1
  - plasma_C
  - CA19-9
  - CEA
- Biomarkers such as glucose, urine_volume and urine_pH displayed limited discriminatory power.

### Correlation Analysis

Strongest correlations with diagnosis severity:

| Biomarker | Correlation |
|------------|------------|
| REG1A | 0.80 |
| REG1B | 0.77 |
| TFF1 | 0.73 |
| plasma_C | 0.73 |
| CEA | 0.72 |
| CA19_9 | 0.70 |

These results suggested substantial predictive potential for several biomarkers.

---

## Notebook 02 — Feature Engineering

This notebook prepares the dataset for machine learning.

### Feature Engineering

- Encoded sex variable:
  - Male = 1
  - Female = 0
- Created diagnosis labels for interpretability.

### Statistical Validation

ANOVA F-tests were performed to identify the most significant predictors.

Top-performing features:

| Biomarker | F-score |
|------------|-----------|
| REG1A | 548.79 |
| REG1B | 431.51 |
| CA19_9 | 384.42 |
| TFF1 | 346.58 |
| plasma_C | 339.44 |
| CEA | 323.24 |

All showed extremely small p-values and strong statistical significance.

### Multicollinearity Check

Variance Inflation Factor (VIF) analysis was performed.

- All VIF values remained below commonly accepted concern thresholds.
- No evidence of problematic multicollinearity.
- All variables were retained for modelling.

---

## Notebook 03 — Machine Learning Modelling

Two classification models were developed and evaluated:

### Models Tested

- Logistic Regression
- Random Forest Classifier

### Logistic Regression Results

| Metric | Value |
|----------|----------|
| Accuracy | 97.5% |
| Cancer Recall | 100% |
| Cancer F1-score | 98% |
| CV Accuracy | 96.5% |
| CV ROC-AUC | 0.9945 |

### Random Forest Results

| Metric | Value |
|----------|----------|
| Accuracy | 97.5% |
| Cancer Recall | 96% |
| Cancer F1-score | 98% |
| CV Accuracy | 95.2% |
| CV ROC-AUC | 0.9934 |

### Model Selection

Although both models achieved identical test accuracy, Logistic Regression was selected as the final model because it:

- Achieved perfect cancer recall (100%)
- Produced slightly stronger cross-validation performance
- Facilitated easier model interpretation and explainability

---

## Notebook 04 — Model Explainability

The final notebook focuses on understanding which biomarkers contributed most strongly to model predictions.

### Most Important Biomarkers

Logistic Regression coefficient analysis identified:

1. REG1A
2. plasma_C
3. REG1B
4. bilirubin
5. LYVE1
6. CA19_9
7. TFF1
8. CEA

as the strongest contributors to pancreatic cancer classification.

### Agreement Across Models

The same biomarkers repeatedly appeared as important during:

- Exploratory Analysis
- Correlation Analysis
- ANOVA Testing
- Logistic Regression
- Random Forest Feature Importance

This consistency increases confidence in their potential clinical relevance.

---

## Key Results

✅ 97.5% Test Accuracy

✅ 100% Cancer Recall

✅ 0.9945 Cross-Validated ROC-AUC

✅ Strong agreement between statistical analysis and machine learning explainability

✅ Identification of a compact biomarker panel strongly associated with pancreatic cancer detection

---

## Technologies Used

- Python
- Pandas
- NumPy
- Matplotlib
- Seaborn
- Scikit-learn
- Statsmodels
- Jupyter Notebook

---

## Limitations

Although the results are highly encouraging, several limitations remain:

- Dataset size is relatively limited (600 observations).
- External clinical validation was not performed.
- Performance has only been evaluated on the available cohort.
- Further testing on independent patient populations would be required before considering clinical deployment.

---

## Future Work

Potential next steps include:

- External validation on independent cohorts
- Hyperparameter optimisation
- SHAP-based explainability
- Ensemble modelling approaches
- Deployment as a clinical decision-support prototype

---

## Author

**Laura Llorent Vázquez**