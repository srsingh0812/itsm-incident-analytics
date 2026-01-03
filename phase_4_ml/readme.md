# 📊 Phase 4 — Machine Learning (ITSM Incident Analytics)

This phase transitions the project from **descriptive analytics** to **predictive modeling**, using clean, validated ITSM incident data built in earlier phases.

The focus is on:

- Business-aligned machine learning
- Data leakage prevention
- Explainability and reproducibility
- A strong foundation for future **MLOps**

---

## 📓 Notebook 01 — Data Understanding

**Objective:**  
Understand the structure, quality, and behavior of the ITSM incident dataset **before** applying any transformations or models.

This notebook focuses purely on **exploration and validation**, not modification.

### ✔ Key Activities

- Loaded the raw ML dataset (`incident_ml_raw.csv`)
- Verified dataset size and column structure
- Identified modeling targets:
  - `sla_breach_flag` — binary classification
  - `resolution_time_hours` — regression
- Analyzed SLA breach distribution  
  - Observed a relatively balanced dataset (~52% breaches)
- Analyzed resolution time and aging distributions  
  - Detected right-skew and long-tail behavior
- Confirmed `aging_bucket` does not exist in raw data  
  - Will be derived later from `aging_days`
- Evaluated ITSM severity signals:
  - `priority`
  - `impact`
  - `urgency`
- Identified zero-variance features:
  - `reassignment_count`
  - `reopen_count`
- Checked high-cardinality features:
  - `assignment_group`
  - `location`
- Verified there are no missing values
- Validated time-related fields:
  - `opened_at`
  - `closed_at`
  - `final_resolved_at`
- Explicitly documented why `sys_updated_at` is excluded:
  - Represents system-level updates
  - May include post-SLA or post-resolution information
  - Poses a **data leakage risk** if used as a feature

### 📌 Outcome

- Clear understanding of which features are safe, risky, or useless
- Early detection of data leakage risks
- Strong documentation of modeling assumptions
- Dataset confirmed suitable for predictive modeling

---

## 📓 Notebook 02 — Data Preprocessing

**Objective:**  
Transform raw incident data into a **machine-learning-safe, reproducible dataset** without introducing data leakage.

This notebook prepares the data for modeling while preserving real-world prediction constraints.

### ✔ Key Activities

- Reloaded raw data to ensure notebook independence
- Dropped non-informative and unsafe columns:
  - Identifiers (`number`)
  - System metadata (`sys_updated_at`)
  - Post-resolution timestamps (`closed_at`, `final_resolved_at`)
  - Zero-variance features (`reassignment_count`, `reopen_count`)
- Converted safe timestamp fields:
  - `opened_at` converted to datetime
- Explicitly defined modeling targets:
  - Classification: `sla_breach_flag`
  - Regression: `resolution_time_hours`
- Removed additional leakage-prone fields:
  - `incident_state`
  - `is_active`
- Separated features (`X`) and targets (`y`)
- Encoded categorical variables using one-hot encoding
- Applied a **time-aware train/test split**:
  - Training on historical incidents
  - Testing on future incidents
- Saved preprocessed datasets for reproducibility:
  - `train_preprocessed.csv`
  - `test_preprocessed.csv`

### 📌 Outcome

- Clean, ML-ready datasets
- No target leakage
- Deterministic preprocessing pipeline
- Solid foundation for classification and regression modeling
- Ready for model training and later MLOps automation

---

## 🧠 Why This Matters

This approach demonstrates:

- Strong data discipline
- Awareness of real-world ML risks
- Business-aware feature selection
- Production-oriented thinking

These notebooks intentionally avoid premature modeling to ensure the models trained later are **trustworthy, explainable, and deployable**.

---

## 🔜 Next Steps

- **Notebook 03:** Feature Engineering  
  (aging buckets, temporal features, severity encoding)
- **Notebook 04:** Classification Models (SLA breach prediction)
- **Notebook 05:** Regression Models (resolution time prediction)
- **Notebook 06–07:** Model Evaluation and Explainability
