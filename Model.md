# Model Documentation

## Final ANN Architecture

| Hyperparameter | Value |
|---|---|
| Hidden Layers | 2 (32 → 16 units) |
| Weight Initialization | He-normal |
| Regularization | Light L2 (0.0005) + Dropout(0.3) |
| Optimizer | Adam |
| Learning Rate | 0.001 |
| Early Stopping | Patience = 8 |

## Ablation Testing Results

| Experiment | Change | Effect |
|---|---|---|
| Baseline | No regularization | Train ~93-94% / Test ~85% (overfitting gap) |
| + Dropout(0.3) | Isolated Dropout only | Identified as the single most effective fix for the train/test gap |
| + L2 | Isolated L2 only | Smaller effect than Dropout alone |
| + Heavier regularization stack | Multiple techniques combined | Underperformed the simpler final config — more regularization was not always better |
| **Final** | Dropout(0.3) + light L2 + He-init + EarlyStopping | Best generalization balance |

## Model Comparison

| Model | ROC-AUC |
|---|---|
| Logistic Regression | 0.813 |
| Random Forest | *(see notebook for exact value)* |
| Final ANN | 0.752 |

## Explainability: SHAP

SHAP (KernelExplainer) was used to attribute each prediction to individual feature contributions, giving HR stakeholders a per-employee, directionally-signed explanation rather than a single opaque risk score.

## Key Learnings

- Simpler, well-regularized architectures often generalize better than deep, heavily regularized ones on small tabular datasets.
- SHAP values are more actionable for non-technical stakeholders than raw feature importances.
- A neural network is not automatically the best model for small tabular data — Logistic Regression outperformed the ANN here on ROC-AUC, and that result is reported honestly rather than hidden.
