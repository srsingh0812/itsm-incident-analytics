# 🚀 Phase 4 — Machine Learning (ITSM Incident Analytics)

## 📌 Phase Overview

Phase 4 transitions the project from **descriptive analytics** to **predictive machine learning**, using clean and validated ITSM incident data prepared in earlier phases.

The goal is to build **business-aligned, explainable ML models** that answer forward-looking operational questions:

- Which incidents are likely to breach SLA?
- Which incidents should be prioritized early?
- How long will an incident take to resolve?

This phase is designed with a **production mindset**, emphasizing:
- ✅ Data leakage prevention
- ✅ Time-aware validation
- ✅ Explainability and reproducibility
- ✅ Readiness for future MLOps integration

---

## 🎯 Business Objectives

### 1️⃣ SLA Breach Prediction (Classification)

**Predict**, at incident creation time, whether an incident will breach SLA.

**Business value:**
- Early risk identification
- Proactive prioritization
- Reduced SLA penalties

### 2️⃣ Resolution Time Prediction (Regression)

**Predict** the total time required to resolve an incident (in hours).

**Business value:**
- Capacity planning
- Workload forecasting
- SLA buffer estimation

---

## 📓 Notebook 01 — Data Understanding

### Objective
Understand the structure, quality, and behavior of the ITSM incident dataset before modeling.

### Key Activities

- ✅ Loaded raw ML dataset (`incident_ml_raw.csv`)
- ✅ Verified dataset size, schema, and column types
- ✅ Identified modeling targets:
  - `sla_breach_flag` → classification
  - `resolution_time_hours` → regression
- ✅ Analyzed SLA breach distribution
  - ~52% breach rate (relatively balanced)
- ✅ Analyzed aging and resolution-time distributions
  - Observed right-skew and long-tail behavior
- ✅ Confirmed `aging_bucket` does not exist in raw data
  - Planned derivation from `aging_days`
- ✅ Reviewed severity indicators:
  - `priority`, `impact`, `urgency`
- ✅ Identified zero-variance features:
  - `reassignment_count`, `reopen_count`
- ✅ Reviewed high-cardinality features:
  - `assignment_group`, `location`
- ✅ Validated timestamp fields:
  - `opened_at`, `closed_at`, `final_resolved_at`
- ⚠️ **Explicitly excluded `sys_updated_at`:**
  - Contains system-level updates
  - May include post-resolution information
  - **Poses data leakage risk**

### Outcome
- Clear understanding of safe vs risky features
- Early identification of leakage risks
- Dataset confirmed suitable for predictive modeling

---

## 📓 Notebook 02 — Data Preprocessing

### Objective
Prepare a machine-learning-safe, reproducible dataset without introducing leakage.

### Key Activities

- ✅ Reloaded raw data for notebook independence
- ✅ Dropped unsafe or non-informative columns:
  - Identifiers (`number`)
  - System metadata (`sys_updated_at`)
  - Post-resolution timestamps (`closed_at`, `final_resolved_at`)
  - Zero-variance features
- ✅ Converted safe timestamps:
  - `opened_at` → datetime
- ✅ Defined modeling targets:
  - **Classification:** `sla_breach_flag`
  - **Regression:** `resolution_time_hours`
- ✅ Removed additional leakage-prone columns:
  - `incident_state`, `is_active`
- ✅ Separated features (X) and targets (y)
- ✅ Encoded categorical variables (one-hot encoding)
- ✅ Applied **time-aware train/test split**
- ✅ Saved preprocessed datasets for reproducibility

### Outcome
- Clean, ML-ready datasets
- No target leakage
- Deterministic preprocessing pipeline

---

## 📓 Notebook 03 — Feature Engineering

### Objective
Convert preprocessed data into business-meaningful ML features.

### Key Activities

- ✅ Created aging buckets from `aging_days`:
  - 0–1, 2–7, 8–30, 30+ days
- ✅ Extracted temporal features:
  - `hour_of_day`, `day_of_week`, `is_weekend`
- ✅ Preserved severity signals:
  - `priority`, `urgency`
- ✅ Handled high-cardinality features:
  - Frequency encoding for `location`
- ✅ Dropped raw timestamps after feature creation
- ✅ Saved final dataset as `incident_ml_features.csv`

### Outcome
- Explainable, non-leaky feature set
- Reduced noise and dimensionality
- Strong alignment with ITSM operations

---

## 📓 Notebook 04 — Classification Models (SLA Breach Prediction)

### Models Trained

#### Logistic Regression (Baseline)

| Metric | Value |
|--------|-------|
| **Recall (SLA Breach)** | 0.99 |
| **ROC-AUC** | 0.9999 |
| **False Negatives** | 12 |

**Interpretation:**
- Strong, explainable baseline
- Misses very few SLA breaches

#### Random Forest Classifier

| Metric | Value |
|--------|-------|
| **Recall (SLA Breach)** | 1.00 |
| **ROC-AUC** | 0.99999 |
| **False Negatives** | 9 |

**Interpretation:**
- Captures non-linear patterns
- Reduces missed SLA breaches

### ✅ Final Choice: Random Forest Classifier
**Reason:** Fewer missed SLA breaches directly reduces operational risk.

---

## 📓 Notebook 05 — Regression Models (Resolution Time Prediction)

### Models Trained

#### Linear Regression (Baseline)

| Metric | Value |
|--------|-------|
| **MAE** | 6.11 hrs |
| **RMSE** | 7.39 hrs |
| **R²** | 0.9997 |

**Interpretation:**
- Predicts resolution time within ~6–7 hours
- Strong linear baseline

#### Random Forest Regressor

| Metric | Value |
|--------|-------|
| **MAE** | 4.64 hrs |
| **RMSE** | 6.99 hrs |
| **R²** | 0.9997 |

**Interpretation:**
- ~1.5 hour improvement in MAE
- Better handling of complex resolution behavior

### ✅ Final Choice: Random Forest Regressor
**Reason:** Significant MAE reduction improves capacity planning accuracy.

---

## 📊 Final Model Selection Summary

### Classification

| Model | Recall | Missed Breaches |
|-------|--------|-----------------|
| Logistic Regression | 0.99 | 12 |
| **Random Forest** | **1.00** | **9** |

### Regression

| Model | MAE (hrs) | RMSE (hrs) |
|-------|-----------|------------|
| Linear Regression | 6.11 | 7.39 |
| **Random Forest** | **4.64** | **6.99** |

### ✅ Final Selection

- **Classification:** Random Forest Classifier
- **Regression:** Random Forest Regressor

Selection is based on **business risk reduction**, not marginal metric gains.

---

## ⚠️ Note on Metrics

Near-perfect metrics are **uncommon** in real-world ITSM systems.

These results indicate strong predictive signals but require:
- ✅ Validation on future time windows
- ✅ Monitoring for data drift
- ✅ Careful review before production deployment

This consideration reflects **production-grade ML thinking**.

---

## 📊 Business Impact

Phase 4 enables:

✅ **Early SLA breach detection**  
✅ **Smarter incident prioritization**  
✅ **Improved capacity planning**  
✅ **Explainable ML outputs** suitable for enterprise use

---

## 🔜 Next Steps

- [ ] **Model Explainability** — Feature importance & SHAP analysis
- [ ] **MLOps Extensions** — MLflow tracking, model monitoring
- [ ] **Production Deployment** — Azure/Databricks integration
- [ ] **Drift Detection** — Continuous monitoring setup

---

## 🧠 Interview One-Liner

> "In Phase 4, I built explainable ML models to predict SLA breach risk and resolution time, selecting Random Forest models based on recall and error reduction aligned with operational impact."

---

## 📂 Project Structure
```
phase_4_ml/
├── notebooks/
│   ├── 01_data_understanding.ipynb
│   ├── 02_data_preprocessing.ipynb
│   ├── 03_feature_engineering.ipynb
│   ├── 04_classification_models.ipynb
│   └── 05_regression_models.ipynb
├── data/
│   ├── incident_ml_raw.csv
│   ├── incident_ml_preprocessed.csv
│   └── incident_ml_features.csv
└── README.md
```
