# 🏦 Company Bankruptcy Prediction System

<div align="center">

![Python](https://img.shields.io/badge/Python-3.10+-blue?style=for-the-badge&logo=python&logoColor=white)
![Scikit-Learn](https://img.shields.io/badge/Scikit--Learn-1.7.2-orange?style=for-the-badge&logo=scikit-learn&logoColor=white)
![Streamlit](https://img.shields.io/badge/Streamlit-1.32+-red?style=for-the-badge&logo=streamlit&logoColor=white)
![Status](https://img.shields.io/badge/Status-Complete-brightgreen?style=for-the-badge)
![License](https://img.shields.io/badge/License-MIT-yellow?style=for-the-badge)

**An end-to-end Machine Learning project that predicts company bankruptcy risk using 95 financial ratios — with an interactive Streamlit dashboard.**

[Features](#-features) • [Demo](#-demo) • [Dataset](#-dataset) • [Models](#-models-trained) • [Installation](#-installation) • [Usage](#-usage) • [Results](#-results)

</div>

---

## 📌 Project Overview

This project builds a **binary classification system** to predict whether a company is at risk of bankruptcy based on its financial data. The model is trained on the **Taiwan Economic Journal (TEJ) dataset** containing 6,819 company records with 95 financial features.

The key challenge of this dataset is **severe class imbalance** — only 3.2% of companies are bankrupt. A naive model that always predicts "not bankrupt" would score 96.7% accuracy but catch zero real bankruptcies. This project tackles that problem head-on using **SMOTE** and focuses on meaningful metrics like **ROC-AUC, Recall, and F1-score**.

---

## ✨ Features

- ✅ Full ML pipeline — EDA → Preprocessing → SMOTE → Training → Evaluation → Deployment
- ✅ 5 supervised learning models trained and compared
- ✅ Class imbalance handled with SMOTE (Synthetic Minority Oversampling Technique)
- ✅ Interactive Streamlit dashboard with real-time risk prediction
- ✅ Visual risk meter, probability breakdown, and feature importance chart
- ✅ Preset loader (Healthy / High-Risk / Borderline company examples)
- ✅ 95 financial inputs organized across 8 logical tabs

---

## 🎬 Demo

> **Screenshots coming soon**

To run locally, follow the [Installation](#-installation) steps below.

---

## 📊 Dataset

| Property | Details |
|---|---|
| **Source** | Taiwan Economic Journal (TEJ) |
| **Records** | 6,819 companies |
| **Features** | 95 financial ratios |
| **Target** | `Bankrupt?` (0 = Solvent, 1 = Bankrupt) |
| **Class Distribution** | 6,599 solvent (96.8%) · 220 bankrupt (3.2%) |
| **Missing Values** | None |

### Feature Categories

The 95 features are grouped into 8 categories:

| Category | # Features | Examples |
|---|---|---|
| Profitability Ratios | 15 | ROA, Operating Gross Margin, Cash Flow Rate |
| Per Share Metrics | 8 | EPS, Net Value Per Share, Cash Flow Per Share |
| Growth Rates | 9 | Net Profit Growth Rate, Total Asset Growth Rate |
| Liquidity Ratios | 17 | Current Ratio, Quick Ratio, Working Capital |
| Leverage & Solvency | 20 | Debt Ratio, Net Worth/Assets, Equity to Liability |
| Capital & Income | 3 | Operating Profit/Paid-in Capital |
| Turnover Efficiency | 13 | Asset Turnover, Receivable Turnover, Collection Days |
| Cash Flow Ratios | 10 | Cash Flow to Sales, CFO to Assets |

---

## 🤖 Models Trained

Five supervised learning models were trained and compared:

| Model | Notes |
|---|---|
| Logistic Regression | Baseline model, `class_weight='balanced'` |
| Decision Tree | `class_weight='balanced'`, `random_state=42` |
| Random Forest ⭐ | **Best model** · 100 estimators · `class_weight='balanced'` |
| Gradient Boosting | Ensemble boosting approach |
| SVM | `probability=True`, `class_weight='balanced'` |

> ⭐ **Random Forest** was selected as the final model based on ROC-AUC and F1-score performance.

---

## 📈 Results

> Evaluated on a held-out test set (20% of data) after training on SMOTE-balanced data.

### Why Not Accuracy?

| Metric | Value |
|---|---|
| Naive Accuracy (always predict "safe") | 96.7% |
| **Meaningful metrics used instead** | ROC-AUC, F1-Score, Precision, Recall |

### Top 10 Most Important Features

| Rank | Feature | Importance |
|---|---|---|
| 1 | Non-industry income and expenditure/revenue | 0.0608 |
| 2 | Net Income to Total Assets | 0.0517 |
| 3 | After-tax net Interest Rate | 0.0436 |
| 4 | Continuous interest rate (after tax) | 0.0393 |
| 5 | Borrowing dependency | 0.0386 |
| 6 | Persistent EPS in the Last Four Seasons | 0.0370 |
| 7 | Liability to Equity | 0.0357 |
| 8 | Net Income to Stockholder's Equity | 0.0340 |
| 9 | Total income/Total expense | 0.0335 |
| 10 | Net worth/Assets | 0.0320 |

---

## 🛠️ Tech Stack

```
Python 3.10+
├── Data Processing    → pandas, numpy
├── Visualization      → matplotlib, seaborn
├── ML Models          → scikit-learn
├── Class Imbalance    → imbalanced-learn (SMOTE)
├── Model Saving       → joblib
└── Deployment         → Streamlit
```

---

## ⚙️ Installation

### 1. Clone the repository

```bash
git clone https://github.com/YOUR_USERNAME/bankruptcy-prediction.git
cd bankruptcy-prediction
```

### 2. Create a virtual environment (recommended)

```bash
python -m venv venv
source venv/bin/activate        # Linux / Mac
venv\Scripts\activate           # Windows
```

### 3. Install dependencies

```bash
pip install -r requirements.txt
```

---

## 🚀 Usage

### Run the Streamlit App

```bash
streamlit run app.py
```

Then open your browser at `http://localhost:8501`

### Using the App

1. **Load a Preset** — Use the sidebar to load a Healthy, High-Risk, or Borderline company example
2. **Enter Financial Data** — Fill in the 95 financial ratios across 8 tabs
3. **Analyze** — Click "Analyze Bankruptcy Risk" to get the prediction
4. **Review Results** — See the risk verdict, probability score, risk meter, and top feature drivers

### Run the Notebook

Open `Bankruptcy_Prediction_Model.ipynb` in Jupyter or Google Colab to walk through the full ML pipeline step by step.

```bash
jupyter notebook Bankruptcy_Prediction_Model.ipynb
```

---

## 📁 Project Structure

```
bankruptcy-prediction/
│
├── app.py                              ← Streamlit dashboard
├── Bankruptcy_Prediction_Model.ipynb   ← Full ML pipeline notebook
├── COMPANY_BANKRUPTCY_PREDICTION.csv   ← Dataset
├── requirements.txt
├── README.md
│
└── model/
    ├── model.pkl                       ← Trained Random Forest model
    ├── scaler.pkl                      ← Fitted StandardScaler
    └── features.pkl                    ← Feature list (95 features)
```

---

## 🔄 ML Pipeline Summary

```
Raw Dataset (6,819 records, 95 features)
        ↓
Exploratory Data Analysis
  • Class distribution visualization
  • Correlation heatmap
  • Feature distribution plots
        ↓
Preprocessing
  • Train-test split (80/20, stratified)
  • StandardScaler (fit on train, transform both)
        ↓
Handle Class Imbalance
  • SMOTE applied on training set only
  • Before: 5,279 safe | 176 bankrupt
  • After:  5,279 safe | 5,279 bankrupt (balanced)
        ↓
Model Training & Comparison
  • 5 models trained with cross-validation
  • Evaluated on ROC-AUC, F1, Precision, Recall
        ↓
Best Model: Random Forest
  • Saved with joblib
        ↓
Streamlit Deployment
  • Real-time prediction dashboard
```

---

## 📋 Requirements

```
streamlit>=1.32.0
scikit-learn==1.7.2
imbalanced-learn
joblib
numpy
pandas
matplotlib
seaborn
```

---

## 🙋 About

Built by **Sitesh** — Electronics & Communication Engineering student at **BPIT, New Delhi**.

This project was built to practice the complete supervised learning workflow — from raw data to a deployed web application — covering every step that matters in a real ML project.

---

## 📄 License

This project is licensed under the MIT License — see the [LICENSE](LICENSE) file for details.

---

## 🌟 If you found this useful, please give it a star!

<div align="center">

[![GitHub stars](https://img.shields.io/github/stars/YOUR_USERNAME/bankruptcy-prediction?style=social)](https://github.com/YOUR_USERNAME/bankruptcy-prediction)

</div>
