
# 📊 Predicting Low Math Performance Using PISA 2022 UK Data

This project explores student-level predictors of low mathematics performance using the **PISA 2022 UK Student Questionnaire** data. It uses interpretable machine learning models (decision trees, random forests, and XGBoost) and survey weights to generate population-representative predictions and insights.

---

## 📁 Project Structure

```
mini_project_2/
│
├── data/
│   ├── raw/                            # Original OECD UK data
│   │   ├── pisa_2022_uk_selected.csv
│   │   └── uk_pisa_2022.csv
│   │
│   └── processed/                      # Cleaned and split datasets
│       ├── train.csv, test.csv, val.csv
│       ├── *_cont.csv                 # Continuous target splits
│       ├── final_test_predictions_*.csv
│
├── notebooks/
│   ├── 00_data_selection.ipynb        # Select target and relevant features
│   ├── 01_eda.ipynb                   # Exploratory data analysis
│   ├── 02_preprocessing_binary.ipynb  # Preprocessing for binary target
│   ├── 02_preprocessing_continuous.ipynb # Preprocessing for regression
│   ├── 03_decision_trees_pre_pruning.ipynb
│   ├── 04_decision_trees_post_pruning.ipynb
│   ├── 05_ensemble_random_forest.ipynb
│   └── 06_XGBoost.ipynb               # Gradient boosting for regression
│
├── requirements.txt
└── README.md
└── reflection.md 

```

---

## 🎯 Objectives

* ✅ Predict students at risk of **low math performance**
* ✅ Use interpretable models with **weighted samples** (PISA design)
* ✅ Explore **demographic, school, family, and psychological factors**
* ✅ Build both **binary classification** and **continuous regression** models

---

## 🧠 Target Variables

* **Binary**: `math_binary` → below minimum proficiency level
* **Continuous**: `math_1` → Plausible Value 1 (PV1MATH)

---

## ⚖️ Sampling Weights

All training and evaluation use the **`W_FSTUWT` survey weight** for population-representative modeling.

| Step               | Weight Used? |
| ------------------ | ------------ |
| EDA                | Optional     |
| Training models    | ✅ Yes        |
| Evaluation metrics | ✅ Yes        |

---

## 📊 Models Trained

### 🔹 Decision Trees

* Overfit quickly on training data
* Pre-pruning (e.g., `max_depth`, `min_samples_leaf`) improved generalization
* Post-pruning (using `ccp_alpha`) simplified trees

### 🔹 Random Forests

* Better performance and stability
* Consistent top features: **SES**, **parent support**, **school belonging**

### 🔹 XGBoost (for Regression)

* Models continuous `math_1` outcome
* Best performance with shallow trees and tuned learning rates
* Captures nonlinear relationships better than trees

---

## 🧮 Key Features Used

* Socioeconomic status (ESCS)
* Student wellbeing and confidence
* Family background and support
* School belonging and instructional support
* Peer relationships and academic motivation

---

## 📈 Evaluation Metrics

### For Classification:

* Accuracy
* Precision, Recall, F1
* Confusion Matrix

### For Regression:

* MAE
* RMSE
* R² Score

---

## 🔍 How to Reproduce

1. Clone the repo:

   ```bash
   git clone https://github.com/your-username/mini_project_2.git
   cd mini_project_2
   ```

2. Install requirements:

   ```bash
   pip install -r requirements.txt
   ```

3. Open notebooks in Jupyter or VS Code and run in order:

   * `00_data_selection.ipynb`
   * `01_eda.ipynb`
   * `02_preprocessing_binary.ipynb` or `02_preprocessing_continuous.ipynb`
   * Modeling notebooks (03–06)

---

## 📌 Findings

* **SES is consistently the top predictor** across all models.
* **Family support** and **school belonging** strongly correlate with performance.
* Regression models (XGBoost) yield more nuanced predictions than binary models.

---

## 📎 References

* [OECD PISA 2022 Data](https://www.oecd.org/pisa/data/2022database/)
* [XGBoost Documentation](https://xgboost.readthedocs.io/)
* [PISA Technical Manual](https://www.oecd.org/pisa/data/pisa2022technicalreport.htm)

