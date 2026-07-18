# System Architecture

## Pipeline Overview

```
[HR CSV Data] → [Preprocessing: encode + scale + imbalance handling]
      → [ANN Architecture Search: 1-2 hidden layers, regularization variants]
      → [Ablation Testing: isolate effect of each regularization choice]
      → [Final ANN] + [Logistic Regression + Random Forest baselines]
      → [SHAP Explainability]
      → [Streamlit Scaffold (deployment)]
```

## Components

| Component | Responsibility |
|---|---|
| Preprocessing | Encode categorical features, scale numerical features, handle class imbalance |
| ANN Search | Iteratively test hidden-layer configs and regularization combinations |
| Ablation Testing | Isolate the effect of Dropout, L2, Batch Norm, EarlyStopping individually |
| Baseline Models | Logistic Regression and Random Forest for honest comparison |
| SHAP Module | Generates per-feature, per-employee explainability |
| Streamlit Scaffold | Basis for an interactive deployment app |

## Design Decisions

- **Why ablation testing instead of just tuning for best score:** isolating each regularization technique's individual contribution reveals *why* a configuration works, not just *that* it works — more defensible in an interview setting.
- **Why compare against classical ML baselines:** avoids the common mistake of assuming a neural network is automatically the best choice for small tabular data; the honest result here (LR outperforming ANN on ROC-AUC) is itself a valuable, defensible finding.
- **Why SHAP over basic feature importance:** SHAP gives direction and magnitude per feature per individual, which is directly actionable for HR stakeholders in a way global importance rankings are not.
