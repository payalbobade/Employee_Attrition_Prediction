<div align="center">

# 👥 Employee Attrition Prediction using Artificial Neural Networks
### ANN with systematic ablation testing, SHAP explainability, and classical ML benchmarks

![Python](https://img.shields.io/badge/Python-3.10-blue?style=flat-square&logo=python)
![Keras](https://img.shields.io/badge/Keras-D00000?style=flat-square&logo=keras&logoColor=white)
![Status](https://img.shields.io/badge/Status-Complete-success?style=flat-square)
![License](https://img.shields.io/badge/License-MIT-yellow?style=flat-square)

[Overview](#-overview) • [Approach](#-approach) • [Installation](#️-installation--how-to-run) • [Results](#-results) • [Contact](#-contact)

</div>

---

## 📌 Overview

An ANN built to predict whether an employee is likely to leave a company, using the IBM HR Analytics dataset. The project involved systematic ablation testing across multiple architectures and regularization strategies to find the most effective, generalizable model.

Employee turnover is expensive — replacing an employee typically costs 6-9 months of their salary. This project predicts attrition risk from HR data so companies can intervene early with at-risk employees.

## 🎯 Problem Statement

HR teams need an early, reliable signal of attrition risk to intervene before it happens — and need to trust *why* a given employee is flagged, not just the score itself.

## 💼 Business Objective

Provide HR with a ranked attrition-risk score per employee, backed by SHAP-based explainability, to support proactive, targeted retention strategies.

## 🧠 Approach

- **Data preprocessing**: encoded categorical HR features, scaled numerical features, handled class imbalance in the attrition target.
- **Model architecture search**: iteratively tested 1-2 hidden layer ANNs with different combinations of L1/L2 regularization, Batch Normalization, and Dropout.
- **Key finding**: a simplified **2-hidden-layer architecture with Dropout, He-normal initialization, light L2 regularization, and EarlyStopping** outperformed more heavily regularized variants — more regularization was not always better.
- **Bonus comparison**: added Logistic Regression and Random Forest baselines, plus SHAP explainability to interpret which features drive attrition predictions.
- Includes a Streamlit scaffold for deploying the model as an interactive app.

Full detail in [`docs/Model.md`](docs/Model.md) and [`docs/Workflow.md`](docs/Workflow.md).

## 📂 Dataset

[IBM HR Analytics Employee Attrition & Performance (Kaggle)](https://www.kaggle.com/datasets/pavansubhasht/ibm-hr-analytics-attrition-dataset) — 1,470 employee records with 35 features (demographics, job role, satisfaction scores, etc.)

See [`docs/Dataset.md`](docs/Dataset.md) for preprocessing details.

## 🗂️ Project Structure

```text
employee-attrition-prediction-ann/
│
├── ANN_Employee_Attrition_Expanded.ipynb   # Full pipeline: preprocessing → ANN → ablation → SHAP → comparison
├── docs/
│   ├── Architecture.md
│   ├── Dataset.md
│   ├── Workflow.md
│   └── Model.md
├── README.md
├── LICENSE
├── CONTRIBUTING.md
├── CODE_OF_CONDUCT.md
└── .gitignore
```

## ⚙️ Installation & How to Run

```bash
git clone https://github.com/payalbobade/employee-attrition-prediction-ann.git
cd employee-attrition-prediction-ann
```

1. Download the dataset from the Kaggle link above (`WA_Fn-UseC_-HR-Employee-Attrition.csv`).
2. Open `ANN_Employee_Attrition_Expanded.ipynb` in Google Colab or Jupyter.
3. Upload the CSV when prompted (or place it in the same folder and update the file path).
4. Run all cells top to bottom.

## ✨ Features

- ✅ ANN model with systematic overfitting diagnosis
- ✅ Controlled ablation testing (Dropout, L2, EarlyStopping isolated and compared)
- ✅ SHAP-based explainability (KernelExplainer)
- ✅ Benchmark comparison against Logistic Regression and Random Forest
- ✅ Streamlit deployment scaffold included

## 📏 Results

Final architecture: **2 hidden layers (32→16)**, He-normal initialization, light L2 (0.0005), Adam at 0.001 LR, EarlyStopping (patience=8), Dropout(0.3) — identified via ablation testing as the single most effective regularization change.

| Model | ROC-AUC |
|---|---|
| Logistic Regression | 0.813 |
| Final ANN | 0.752 |

*(Logistic Regression outperformed the ANN on ROC-AUC in this dataset — reported honestly, as a genuine and instructive finding rather than an inflated claim.)*

## 🧭 Key Learnings

- Simpler, well-regularized architectures often generalize better than deep, heavily regularized ones on small tabular datasets — a form of the bias-variance tradeoff in practice.
- SHAP values are far more actionable for HR stakeholders than raw feature importances, since they show direction and magnitude of each feature's effect per employee.

## 🚀 Future Improvements

- [ ] Test on a larger, more diverse HR dataset to validate generalizability beyond IBM's sample data
- [ ] Turn the Streamlit scaffold into a fully deployed internal HR dashboard
- [ ] Add cost-sensitive learning to weight false negatives (missed at-risk employees) more heavily

## 🛠️ Technologies Used

`Python` `TensorFlow/Keras` `Scikit-learn` `SHAP` `Pandas` `NumPy` `Matplotlib` `Seaborn`

## 📄 License

MIT — see [LICENSE](LICENSE)

## 🤝 Contributing

See [CONTRIBUTING.md](CONTRIBUTING.md) and our [Code of Conduct](CODE_OF_CONDUCT.md).

## 📬 Contact

**Payal Prabhakar Bobade** — [LinkedIn](https://www.linkedin.com/in/payal-bobade-0b7725309) • [Email](mailto:bpayal477@gmail.com) • [GitHub](https://github.com/payalbobade)

---
<div align="center">⭐ Part of my <a href="https://github.com/payalbobade/payalbobade">GitHub profile portfolio</a> — feel free to star if you find it useful!</div>
