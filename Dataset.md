# Dataset Documentation

## Source

[IBM HR Analytics Employee Attrition & Performance (Kaggle)](https://www.kaggle.com/datasets/pavansubhasht/ibm-hr-analytics-attrition-dataset)

## Structure

| Attribute | Value |
|---|---|
| Records | 1,470 employees |
| Features | 35 (demographics, job role, satisfaction scores, compensation, tenure, etc.) |
| Target Variable | `Attrition` (Yes/No) |
| Class Balance | Imbalanced — minority class is "Yes" (attrition) |

## Preprocessing Applied

- Categorical feature encoding (one-hot / label encoding as appropriate per feature)
- Numerical feature scaling
- Class imbalance handling in the attrition target
- Train / validation / test split (see notebook for exact ratios)

## Known Limitations

- Single-company, synthetic-style IBM sample dataset — results may not generalize directly to other organizations' attrition patterns without revalidation
- 1,470 records is relatively small for deep learning, which partly explains why the classical Logistic Regression baseline was competitive with the ANN
