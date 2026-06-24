# Credit Card Fraud Detection with SHAP-based Explainability

A machine learning system that detects fraudulent credit card transactions and explains **why** each prediction was made — using SHAP (SHapley Additive exPlanations) to make model decisions transparent and auditable.

## Why This Project

Most fraud detection demos stop at "the model said 0.92 probability of fraud." That's not good enough for real-world use — banks, regulators, and analysts need to know **which specific transaction features drove that decision**. This project adds that explainability layer on top of a high-performing fraud classifier.

## What It Does

- Trains **XGBoost** and **Random Forest** classifiers on the Kaggle Credit Card Fraud dataset
- Handles severe class imbalance (~0.17% fraud) using **SMOTE** (Synthetic Minority Oversampling)
- Compares model performance using **AUC-ROC**
- Uses **SHAP TreeExplainer** to generate:
  - Global feature importance (which features matter most across all transactions)
  - Per-transaction waterfall plots (why *this specific* transaction was flagged)
- Wraps everything in an interactive **Streamlit dashboard** — adjust transaction features with sliders and watch the fraud risk score and SHAP explanation update live

## Results

| Model | AUC-ROC |
|---|---|
| XGBoost | 0.976 |
| Random Forest | 0.979 |

## Project Structure

```
fraud-detection-shap/
├── notebook/
│   └── fraud_detection_analysis.ipynb   # Full analysis: EDA, SMOTE, training, SHAP
├── app/
│   └── app.py                            # Streamlit dashboard
├── models/
│   ├── xgb_model.pkl
│   ├── rf_model.pkl
│   ├── scaler.pkl
│   └── feature_names.json
├── images/
│   └── (screenshots)
├── requirements.txt
└── README.md
```

## Dataset

This project uses the [Credit Card Fraud Detection dataset](https://www.kaggle.com/mlg-ulb/creditcardfraud) from Kaggle (284,807 transactions, 492 fraudulent). The dataset is not included in this repo due to size — download it from Kaggle and place `creditcard.csv` in the `notebook/` folder before running the notebook.

## How to Run

### 1. Set up the environment
```bash
pip install -r requirements.txt
```

### 2. Run the analysis notebook
Open `notebook/fraud_detection_analysis.ipynb` and run all cells. This reproduces the full pipeline: data loading, SMOTE balancing, model training, and SHAP analysis.

### 3. Launch the dashboard
```bash
cd app
streamlit run app.py
```
Opens at `http://localhost:8501`. Use the sidebar sliders (or the "Load Fraud Sample" / "Load Legit Sample" buttons) to test different transaction profiles and see the model's reasoning.

## Key Techniques

- **SMOTE applied only to training data** — the test set retains the real-world class imbalance so evaluation metrics reflect genuine performance, not inflated by synthetic balance.
- **SHAP TreeExplainer** — exact, fast Shapley value computation for tree-based models (XGBoost/Random Forest), rather than the slower model-agnostic SHAP methods.
- **Waterfall plots** — show exactly how each feature pushed a single prediction up or down from the baseline, in order of impact.

## Tech Stack

Python · pandas · scikit-learn · XGBoost · imbalanced-learn (SMOTE) · SHAP · Streamlit# Credit Card Fraud Detection with SHAP-based Explainability

A machine learning system that detects fraudulent credit card transactions and explains **why** each prediction was made — using SHAP (SHapley Additive exPlanations) to make model decisions transparent and auditable.

## Why This Project

Most fraud detection demos stop at "the model said 0.92 probability of fraud." That's not good enough for real-world use — banks, regulators, and analysts need to know **which specific transaction features drove that decision**. This project adds that explainability layer on top of a high-performing fraud classifier.

## What It Does

- Trains **XGBoost** and **Random Forest** classifiers on the Kaggle Credit Card Fraud dataset
- Handles severe class imbalance (~0.17% fraud) using **SMOTE** (Synthetic Minority Oversampling)
- Compares model performance using **AUC-ROC**
- Uses **SHAP TreeExplainer** to generate:
  - Global feature importance (which features matter most across all transactions)
  - Per-transaction waterfall plots (why *this specific* transaction was flagged)
- Wraps everything in an interactive **Streamlit dashboard** — adjust transaction features with sliders and watch the fraud risk score and SHAP explanation update live

## Results

| Model | AUC-ROC |
|---|---|
| XGBoost | 0.976 |
| Random Forest | 0.979 |

## Project Structure

```
fraud-detection-shap/
├── notebook/
│   └── fraud_detection_analysis.ipynb   # Full analysis: EDA, SMOTE, training, SHAP
├── app/
│   └── app.py                            # Streamlit dashboard
├── models/
│   ├── xgb_model.pkl
│   ├── rf_model.pkl
│   ├── scaler.pkl
│   └── feature_names.json
├── images/
│   └── (screenshots)
├── requirements.txt
└── README.md
```

## Dataset

This project uses the [Credit Card Fraud Detection dataset](https://www.kaggle.com/mlg-ulb/creditcardfraud) from Kaggle (284,807 transactions, 492 fraudulent). The dataset is not included in this repo due to size — download it from Kaggle and place `creditcard.csv` in the `notebook/` folder before running the notebook.

## How to Run

### 1. Set up the environment
```bash
pip install -r requirements.txt
```

### 2. Run the analysis notebook
Open `notebook/fraud_detection_analysis.ipynb` and run all cells. This reproduces the full pipeline: data loading, SMOTE balancing, model training, and SHAP analysis.

### 3. Launch the dashboard
```bash
cd app
streamlit run app.py
```
Opens at `http://localhost:8501`. Use the sidebar sliders (or the "Load Fraud Sample" / "Load Legit Sample" buttons) to test different transaction profiles and see the model's reasoning.

## Key Techniques

- **SMOTE applied only to training data** — the test set retains the real-world class imbalance so evaluation metrics reflect genuine performance, not inflated by synthetic balance.
- **SHAP TreeExplainer** — exact, fast Shapley value computation for tree-based models (XGBoost/Random Forest), rather than the slower model-agnostic SHAP methods.
- **Waterfall plots** — show exactly how each feature pushed a single prediction up or down from the baseline, in order of impact.

## Tech Stack

Python · pandas · scikit-learn · XGBoost · imbalanced-learn (SMOTE) · SHAP · Streamlit
