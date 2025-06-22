# 🎯 Predicting Low Maths Performance Using PISA 2022 UK Data

This machine learning project uses the PISA 2022 UK student data to predict low student performance in mathematics. The goal is to identify at-risk students using background, SES, wellbeing, ICT use, and school support variables, with population-level accuracy and interpretability.

---

## 📁 Project Structure

- `notebooks/`: EDA, preprocessing, modeling
- `data/`: Raw and cleaned PISA datasets
- `models/`: Trained model files
- `outputs/`: Visualizations, evaluation results
- `README.md`: Project overview and methodology

---

## 🧼 Data Preparation

We use the PISA 2022 Student Questionnaire data for the United Kingdom (England, Wales, Scotland, Northern Ireland).

### Key Steps:
- Identify variables by theme (e.g. SES, demographics, wellbeing, ICT use)
- Check and handle missing values
- Encode categorical variables appropriately
- Select `PV1MATH` as the initial target for classification (binary: below Level 2 or not)

> 💡 **Plausible values** are multiple imputed test scores that estimate a student's ability, accounting for measurement uncertainty and ensuring accurate population-level analysis.  
> Analysis is first run using `PV1MATH`, then repeated across all 10 plausible values (`PV1MATH` to `PV10MATH`) and averaged to ensure robust results.

---

## ⚖️ Understanding & Applying Weights

PISA uses **stratified sampling** to ensure representation by region, gender, and school type. Because the sample is not purely random, results may be biased unless we correct for the sampling design.

### Why Use Weights?

- Each student is assigned a **final student weight** (`W_FSTUWT`) that reflects how many students they represent in the full population.
- Without applying these weights, your model may overrepresent or underrepresent certain groups, leading to incorrect insights.

### When to Use `W_FSTUWT`:

- ❌ **Do not use** when engineering or computing features.
- ✅ **Use during:**
  - **Training**: `model.fit(X_train, y_train, sample_weight=W_FSTUWT)`
  - **Evaluation**: Pass `sample_weight` to metrics like accuracy or F1
  - **Interpretation**: Optionally use for SHAP/feature importance for generalizable insights

---

## 📏 Measuring Uncertainty (Optional)

To calculate **standard errors** or **confidence intervals**, use the **replicate weights** (`W_FSTR1` to `W_FSTR80`).

- These represent 80 resampled versions of the dataset.
- They allow estimation of how much a result (e.g. accuracy, feature importance) would vary across repeated samples.

### Key Concepts:

- **Standard Error (SE)**: How much a sample estimate is expected to vary.
  - Small SE = more precise estimate
  - Large SE = more uncertainty

- **Confidence Interval (CI)**: A range where we expect the true value to fall, e.g., “We are 95% confident the population mean lies between X and Y.”

---

## 🧠 Model Training & Evaluation

Models used:
- Decision Tree Classifier
- Random Forest
- XGBoost Classifier

All models are trained using `sample_weight=W_FSTUWT` for unbiased learning.

Evaluation includes:
- Accuracy
- F1 Score
- Precision/Recall
- ROC-AUC
- Confusion Matrix

Weighted metrics are used where appropriate to reflect population-level performance.

---

## 📊 Interpretability

We use:
- Feature importance plots
- SHAP beeswarm plots
- Grouped performance by student characteristics (e.g. gender, SES)

Weights can be optionally applied during interpretation to generalize insights to the student population.

---

## ✅ Summary

| Step                        | Use Weights? |
|-----------------------------|--------------|
| Feature engineering         | ❌ No         |
| Model training              | ✅ Yes        |
| Evaluation metrics          | ✅ Recommended|
| SHAP / Feature Importance   | ✅ Optional   |
| Standard errors / CI        | ✅ If needed  |

---

## 📎 References
- [OECD PISA 2022 Database](https://www.oecd.org/pisa/data/2022database/)
- PISA Data Analysis Manual (SPSS and SAS)
