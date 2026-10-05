# Bankruptcy Prediction Using Logistic Regression and Explainable Boosting Machines

This repository contains a full workflow for predicting corporate bankruptcy using two modelling approaches: a **Logistic Regression model** and an **Explainable Boosting Machine (EBM)**. The project includes data preprocessing, model development, validation, and a detailed written report summarising the findings.

The accompanying report (`Credit Default Prediction Report.docx`) documents the full analysis, methodology, and results.

---

## 📁 Repository Structure

```
├── src/
│   ├── ebm-bankruptcy-prediction.ipynb
│   ├── regression-bankruptcy-prediction.ipynb
│   └── Datasets/
│       └── Bankruptcy.csv
├── Credit Default Prediction Report.docx
└── README.md   ← (this file)
```

---

## 📘 Project Overview

### 🎯 Objective
To build and compare predictive models for corporate bankruptcy, prioritising:

- Predictive accuracy  
- Interpretability  
- Robustness to non-linear relationships  
- Suitability for highly imbalanced financial data  

### 🧠 Models Implemented

---

## 1. Logistic Regression

A traditional Generalised Additive Model (GAM) used as a baseline.

Key steps (as described in the report):

- **Winsorisation** of extreme financial ratios (1st and 99th percentiles)  
- **Dimensionality reduction** using:
  - Variance Inflation Factor (VIF)
  - LASSO (L1) regularisation  
- **Linearity testing** using the Box–Tidwell test  
- **Model selection** prioritising precision due to class imbalance  
- Final model uses **10 predictors**

Despite some variables failing linearity assumptions, the model with all selected predictors achieved the strongest logistic performance.

---

## 2. Explainable Boosting Machine (EBM)

A modern interpretable machine learning model from the **InterpretML** library.

Advantages highlighted in the report:

- Handles **non-linear relationships** without transformations  
- Learns **shape functions** and **pairwise interactions**  
- Provides **feature importance** and visual interpretability  
- More stable under quasi-separation issues present in the dataset  

EBMs are ideal for this dataset due to its size, imbalance, and non-linear structure.

---

## 📊 Dataset

**File:** `src/Datasets/Bankruptcy.csv`

- 4091 observations  
- 96 numeric financial variables  
- Target variable: `Bankrupt?` (binary)  
- No missing values  
- Some extreme values due to near-zero denominators  
- Highly imbalanced (only 126 bankrupt firms)

---

## 📓 Notebooks

### `regression-bankruptcy-prediction.ipynb`
Implements the full logistic regression pipeline:

- Data profiling  
- Winsorisation  
- VIF filtering  
- LASSO variable selection  
- Linearity testing  
- Model fitting  
- ROC-AUC, precision, recall, F1-score  
- Influence diagnostics (Cook’s distance)

### `ebm-bankruptcy-prediction.ipynb`
Implements the Explainable Boosting Machine:

- Full dataset modelling  
- Feature importance extraction  
- Shape function visualisation  
- Cross-validation performance comparison  
- Interpretation of non-linear effects

---

## 🏆 Results Summary

From the report:

### Logistic Regression
- **ROC-AUC:** 0.905  
- **Precision:** 0.446  

### Explainable Boosting Machine
- **ROC-AUC:** 0.943  
- **Precision:** 0.565  

EBM outperformed logistic regression across all metrics and showed lower variance across folds.

The most influential variable in both models was:

**`retained_earnings_to_total_assets`**

This variable consistently dominated predictive power.

---

## ✅ Conclusion

The analysis demonstrates that **Explainable Boosting Machines** provide superior predictive performance and interpretability for bankruptcy modelling, especially in datasets with:

- Non-linear relationships  
- Extreme financial ratios  
- Severe class imbalance  
- Potential quasi-separation issues  

Logistic regression remains useful for stakeholder communication and baseline comparison, but **EBM is recommended for deployment**.

---

## 🚀 How to Use

1. Clone the repository  
2. Install dependencies (`interpret`, `scikit-learn`, `pandas`, `numpy`, etc.)  
3. Open the notebooks in Jupyter or VS Code  
4. Run the cells sequentially to reproduce the analysis  
5. Refer to the report for detailed methodology and interpretation

---

## 📄 Report

The full written analysis is available in:

**`Credit Default Prediction Report.docx`**

It contains:

- Data profiling  
- Full modelling pipeline  
- Statistical tests  
- Visualisations  
- Cross-validation results  
- Discussion and recommendations  

---

