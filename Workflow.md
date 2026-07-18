# Project Workflow

```
1. Load IBM HR Analytics dataset
      ↓
2. Preprocessing (encode categorical, scale numerical, handle imbalance)
      ↓
3. ANN architecture search (1-2 hidden layers, regularization variants)
      ↓
4. Ablation testing (isolate Dropout / L2 / Batch Norm / EarlyStopping effects)
      ↓
5. Select final ANN architecture
      ↓
6. Train Logistic Regression + Random Forest baselines
      ↓
7. Compare all models (ROC-AUC and other metrics)
      ↓
8. SHAP explainability on final model
      ↓
9. Streamlit deployment scaffold
```

## Reproducing This Workflow

```bash
# 1. Download WA_Fn-UseC_-HR-Employee-Attrition.csv from Kaggle (link in README)
# 2. Open ANN_Employee_Attrition_Expanded.ipynb in Colab/Jupyter
# 3. Upload the CSV or update the file path in the notebook
# 4. Run all cells top to bottom
```
