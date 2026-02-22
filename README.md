# 🏆 APPLAI 26' AI Competition Warm-up
**Faculty of Computer & Information Sciences — Ain Shams University**

---

## 📌 Competition Overview

A warm-up machine learning competition hosted at the Faculty of Computer & Information Sciences, Ain Shams University. The task is a **regression problem** on an anonymized dataset where features `X1–X11` are used to predict a continuous target variable `Y`. Column names were intentionally anonymized to simulate real-world "blind" data extraction scenarios.

---

## 📁 Dataset

| File | Description |
|------|-------------|
| `train.csv` | Training set with features and target `Y` |
| `test.csv` | Test set — features only, predict `Y` |
| `sample_submission.csv` | Correct submission format |

> Features `X1–X11` are anonymous. Target variable is `Y` (continuous).

---

## 🔧 Approach

### 1. Data Preprocessing
- Dropped `X1` (uninformative after inspection)
- Filled missing values: `X9` → mode, `X2` → mean
- Clipped outliers in `X4` using IQR method

### 2. Feature Engineering
- **Target Encoding** (leak-free via KFold): `type_mean_sales` from `X11`, `category_mean_sales` from `X5`
- **Age feature**: `age = 2026 - X8`, then dropped `X8`
- **Interaction features**: `prob_age` (age × X4), `X11X7` (X11 × X7), `X6X4` (X6 × X4)

### 3. Encoding
- Ordinal encoding: `X3` (fat content), `X9` (outlet size), `X10` (location tier)
- Label encoding: `X5`, `X7`, `X11`

### 4. Models Tried

| Model | Tuning |
|-------|--------|
| Decision Tree | GridSearchCV |
| Random Forest | RandomizedSearchCV (200 iter) |
| Gradient Boosting | RandomizedSearchCV (200 iter) |
| XGBoost | RandomizedSearchCV (200 iter) |
| LightGBM | RandomizedSearchCV (200 iter) |
| CatBoost | RandomizedSearchCV (200 iter) |

All models were tuned with **5-fold cross-validation** and scored using **R²**.

---

## 📊 Evaluation Metric

**R² Score** (coefficient of determination)

---

## 🛠️ Tech Stack

- Python 3.x
- `pandas`, `numpy`, `matplotlib`, `seaborn`
- `scikit-learn`
- `xgboost`, `lightgbm`, `catboost`

---

## 🚀 How to Run

```bash
# Install dependencies
pip install pandas numpy matplotlib seaborn scikit-learn xgboost lightgbm catboost

# Run the notebook
jupyter notebook solution.ipynb
```

> Make sure `train.csv`, `test.csv`, and `sample_submission.csv` are in the correct path (update paths in the notebook if needed).

---

## 📂 Repository Structure

```
├── solution.ipynb          # Main notebook with full pipeline
├── train.csv               # Training data (not included)
├── test.csv                # Test data (not included)
├── sample_submission.csv   # Submission format
├── submission.csv          # Final predictions on test set
└── README.md
```

---

---

## 🏅 Final Results

| | |
|---|---|
| **Team** | Nashville Chicken Pizza |
| **Final Rank** | 🎯 8th / 21 teams |
| **Score** | 736.63290 |
| **Total Submissions** | 4 |

> Ranked **8th out of 21 teams** on the private leaderboard (calculated on ~40% of test data). Achieved a competitive score with only 4 submissions — quality over quantity!

---

*Organized by APPLAI 26' — Ain Shams University, Faculty of Computer & Information Sciences. Hosted on Kaggle.*
