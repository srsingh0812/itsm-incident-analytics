# 🔍 Model Explainability — ITSM Incident Analytics

## 📌 Explainability Overview

The purpose of this section is to **explain why** the selected machine learning models make their predictions.

Rather than treating models as black boxes, explainability ensures that:

- ✅ Predictions are trustworthy
- ✅ Insights are actionable
- ✅ Outputs align with real ITSM operations
- ✅ Models can be confidently used in enterprise environments

Explainability is performed on the final selected models:

- **Random Forest Classifier** → SLA Breach Prediction
- **Random Forest Regressor** → Resolution Time Prediction

---

## 📊 Global Explainability — SLA Breach Prediction

The table below shows feature importance values from the **Random Forest Classifier**. Higher values indicate stronger influence on SLA breach risk.

### 🔢 Feature Importance Results

| Feature | Importance |
|---------|------------|
| **aging_days** | **0.9647** |
| knowledge | 0.0130 |
| hour_of_day | 0.0071 |
| location_freq | 0.0066 |
| priority | 0.0054 |
| day_of_week | 0.0026 |
| is_weekend | 0.0004 |
| u_priority_confirmation | 0.0002 |
| sys_mod_count | 0.00004 |
| made_sla | ~0.00000 |

### 🧠 Interpretation of Results

#### **aging_days (≈ 96.5%)**
Aging is the **dominant factor** driving SLA breaches. As incidents remain open longer, the likelihood of breaching SLA increases sharply. This confirms that delays compound risk, making early intervention critical.

#### **knowledge (≈ 1.3%)**
Knowledge-related handling has a measurable impact on SLA outcomes, suggesting that documentation availability and reuse influence resolution efficiency.

#### **hour_of_day (≈ 0.7%)**
The time an incident is created affects SLA risk, reflecting staffing levels, shift changes, and workload concentration during certain hours.

#### **location_freq (≈ 0.66%)**
Frequently occurring locations contribute slightly to SLA breaches, possibly due to higher ticket volume or recurring local issues.

#### **priority (≈ 0.54%)**
Priority influences SLA risk but is far less impactful than aging, indicating that time outweighs declared severity once an incident is open.

### 🏢 Business Meaning

**SLA breaches are driven primarily by incident aging, not by priority alone.**

This reinforces the need for:
- ⚡ Aging-based alerts
- ⚡ Early escalation policies
- ⚡ Active monitoring of unresolved tickets

---

## ⏱️ Global Explainability — Resolution Time Prediction

The table below shows feature importance values from the **Random Forest Regressor**, indicating which factors most strongly influence incident resolution time.

### 🔢 Feature Importance Results

| Feature | Importance |
|---------|------------|
| **aging_days** | **0.9998** |
| hour_of_day | 0.00007 |
| location_freq | 0.00006 |
| day_of_week | 0.00005 |
| priority | 0.00002 |
| knowledge | 0.00001 |
| is_weekend | 0.000001 |
| sys_mod_count | ~0.000000 |
| u_priority_confirmation | ~0.000000 |
| made_sla | ~0.000000 |

### 🧠 Interpretation of Results

#### **aging_days (≈ 99.98%)**
Aging **almost completely explains** resolution time. Once an incident starts aging, it becomes increasingly difficult to close, leading to compounding delays.

#### **hour_of_day (≈ 0.007%)**
Incidents created during certain hours take slightly longer to resolve, reflecting workforce availability and shift handovers.

#### **location_freq (≈ 0.006%)**
High-frequency locations show marginally longer resolution times, suggesting congestion or recurring infrastructure issues.

#### **day_of_week (≈ 0.005%)**
Weekday vs weekend timing affects resolution speed, often due to reduced staffing or slower cross-team coordination.

#### **priority (≈ 0.002%)**
Priority has minimal influence once aging is considered, confirming that process delays dominate over severity labels.

### 🏢 Business Meaning

**Resolution time is almost entirely driven by how long an incident remains open.**

This highlights that:
- ⚡ Preventing aging early is more effective than reacting later
- ⚡ Process improvements matter more than priority escalation
- ⚡ Aging thresholds are critical operational control points

---

## 🔗 Connecting Explainability to Operations

| Model Insight | Operational Action |
|---------------|-------------------|
| Aging drives SLA breach | Implement early aging alerts |
| Aging drives resolution time | Escalate before aging thresholds |
| Time-of-day impact | Adjust staffing for peak hours |
| Location-based delays | Investigate recurring problem areas |

---

## 🎯 Key Takeaways

1. **Aging dominates both models** (96.5% for classification, 99.98% for regression)
2. **Priority is not a primary driver** once incidents are already open
3. **Time-based patterns** (hour, day, weekend) have minor but measurable effects
4. **Operational focus** should be on preventing aging, not just responding to high-priority tickets

---

## 🧠 Interview Talking Points

> "Our explainability analysis revealed that **incident aging accounts for 96-99% of model predictions**, meaning that how long a ticket stays open is far more important than its initial priority. This led us to recommend **aging-based alerts** and **early escalation policies** rather than relying solely on priority-based workflows."

---

## 📂 Project Structure
```
explainability/
├── feature_importance_classification.csv
├── feature_importance_regression.csv
├── explainability_analysis.ipynb
└── README.md
```
