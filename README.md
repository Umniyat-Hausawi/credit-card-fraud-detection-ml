# Credit Card Fraud Detection using Machine Learning

## Project Overview

This project focuses on detecting fraudulent credit card transactions using Machine Learning techniques.

The objective of this project was not only to build a high-performing fraud detection model, but also to understand and apply the complete machine learning workflow in a real-world classification problem.

The project includes:

- Exploratory Data Analysis (EDA)
- Handling imbalanced datasets
- Model comparison
- Threshold tuning
- Feature importance analysis
- Business-driven model selection

Several machine learning models were evaluated to identify the most practical fraud detection solution.

---

## Business Problem

Fraud detection is a highly imbalanced classification problem because fraudulent transactions represent only a very small percentage of total transactions.

Because of this, accuracy alone is not a reliable metric.

For example, a model can achieve very high accuracy simply by predicting all transactions as legitimate while failing to detect fraud.

To solve this problem, the project focused on metrics that better reflect fraud detection performance:

- Precision
- Recall
- F1-score
- ROC-AUC
- Confusion Matrix

---

## Dataset

This project uses the publicly available **Credit Card Fraud Detection Dataset**.

Dataset Source:

- https://www.kaggle.com/datasets/mlg-ulb/creditcardfraud

The dataset contains anonymized credit card transactions.

Features include:

- `V1` → `V28` (anonymized transformed features)
- `Time`
- `Amount`

Target variable:

- `0` → Legitimate Transaction
- `1` → Fraudulent Transaction

The dataset is highly imbalanced, making fraud detection more challenging.

---

## Project Workflow

### 1. Exploratory Data Analysis (EDA)

Performed:

- Dataset inspection
- Class imbalance analysis
- Correlation analysis
- Distribution visualization
- Feature understanding

### Key Insight

Low correlation does not necessarily mean a feature is unimportant.

Some features may contribute through:

- Non-linear relationships
- Feature interactions

especially when using models like XGBoost.

---

### 2. Data Preparation

Performed:

- Train/Test Split
- Stratified Sampling
- Feature Scaling (`Time`, `Amount`)
- Data Leakage Prevention

### Important Note

Scaling was only applied for Logistic Regression.

Tree-based models such as:

- Random Forest
- XGBoost

do not require feature scaling.

---

### 3. Model Training

Three machine learning models were evaluated:

### Logistic Regression
- Used as a baseline model
- Strong fraud detection (high Recall)
- Produced many false positives

### Random Forest
- Very high Precision
- Extremely low false positives
- More conservative fraud detection

### XGBoost
- Strong balance between Precision and Recall
- Best overall fraud detection performance
- Highest ROC-AUC score

---

## Threshold Tuning

Instead of relying only on the default threshold (`0.5`), threshold tuning was applied to optimize model behavior.

For XGBoost:

- Default threshold: `0.5`
- Final selected threshold: `0.6`

Why?

Because it improved:

- Precision
- F1-score

while maintaining nearly the same Recall performance.

This reduced unnecessary fraud alerts without significantly sacrificing fraud detection performance.

---

## Final Model Comparison

| Model | Precision | Recall | F1-score | ROC-AUC |
|--------|------------|--------|----------|----------|
| Logistic Regression | 0.06 | 0.92 | 0.11 | 0.972 |
| Random Forest | 0.96 | 0.74 | 0.84 | 0.953 |
| XGBoost (Final) | 0.62 | 0.86 | 0.72 | 0.976 |

---

## Final Decision

XGBoost was selected as the final model because it provided the best balance between:

- Fraud detection capability
- Customer experience
- False fraud alerts
- Business practicality

Rather than selecting the model with the highest single metric, the final decision considered both machine learning performance and real-world business trade-offs.

---

## Tools & Technologies

- Python
- Pandas
- NumPy
- Matplotlib
- Seaborn
- Scikit-learn
- XGBoost
- Jupyter Notebook

---

## Key Learning Outcomes

Through this project, the following concepts were applied and reinforced:

- Imbalanced classification
- Precision vs Recall trade-offs
- ROC-AUC interpretation
- Threshold tuning
- Feature importance
- Data leakage prevention
- Linear vs Non-linear models
- Model comparison
- Business-driven decision making
