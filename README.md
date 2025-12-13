# ITSM Incident Analytics  
_End-to-end ITSM Incident Analysis using Excel, SQL, and Power BI_

---

## 📖 Overview
This project focuses on analyzing IT Service Management (ITSM) incident data to improve visibility into SLA compliance, resolution efficiency, and incident backlog trends.

Raw incident logs are transformed into a clean, analytics-ready dataset that supports operational reporting, performance monitoring, and future advanced analytics use cases.

---

## 🎯 Business Problem
IT operations teams commonly face the following challenges:
- Inconsistent resolution timestamps across incident states
- Limited transparency into SLA breaches
- Difficulty tracking incident aging and backlog health
- Manual reporting processes that do not scale

This project addresses these issues by building a structured analytics pipeline and defining standardized KPIs aligned with real-world ITSM practices.

---

## 🧰 Tools & Technologies
- **Excel (Power Query)** — Data cleaning, transformation, validation, and feature engineering  
- **SQL** — KPI computation, aggregation, and analytical querying  
- **Power BI** — Interactive dashboards and operational reporting  

---

## 📊 Key KPIs
- Resolution Time (Hours / MTTR)
- SLA Breach Indicator
- Incident Aging (Days)
- Reopen Count
- Reassignment Count
- Monthly Incident Volume Trends

---

## 🗂 Project Phases

### Phase 1 — Data Preparation (Completed)
- Cleaned and standardized raw ITSM incident data using Excel Power Query
- Normalized date and time fields across multiple timestamps
- Implemented resolution logic based on incident state
- Converted boolean and categorical fields into analytics-friendly formats
- Engineered core KPIs such as MTTR, aging days, and SLA breach flag
- Produced a clean, SQL-ready incident dataset

### Phase 2 — SQL Analytics (In Progress)
- Load cleaned incident data into a relational database
- Write SQL queries for KPI computation and aggregation
- Analyze SLA compliance by priority, category, and assignment group
- Identify high-aging and frequently reopened incidents
- Create reusable SQL views for reporting and dashboard consumption

### Phase 3 — Power BI Visualization (Planned)
- Build interactive dashboards for IT operations teams
- Monitor SLA performance and resolution trends
- Visualize incident aging and backlog distribution
- Enable drill-down analysis by priority, category, and time
- Provide both operational and executive-level views

---

## ⚙️ Data Preparation Summary

The raw ITSM incident data was transformed into an analytics-ready dataset using a structured and reproducible data preparation process.

### ▸ Data Cleaning
- Removed duplicate incident records
- Standardized date and time formats
- Handled missing and invalid values using domain-driven logic

### ▸ Resolution Logic
- Created a single, reliable resolution timestamp based on incident state
- Applied fallback logic using system update and closure timestamps
- Ensured no null or negative resolution times remained

### ▸ Feature Engineering
- Calculated Resolution Time (Hours / MTTR)
- Derived Incident Aging (Days) for open and closed tickets
- Generated SLA Breach Flag using priority-specific thresholds
- Converted boolean fields into numeric indicators

### ▸ Validation & Quality Checks
- Verified zero null values in critical KPI fields
- Confirmed absence of negative time calculations
- Performed sanity checks across priority and incident state distributions

The final dataset is consistent, validated, and ready for SQL-based analysis and dashboarding.

---

## 📁 Repository Structure
## Repository Structure
```text
itsm-incident-analytics/
├── data/
│   └── processed/
│       └── clean_incidents.csv
│
├── excel/
│   └── itsm_incident_etl.xlsx
│
├── docs/
│   ├── problem_statement.md
│   └── kpi_definitions.md
│
└── README.md
```
---

## 📌 Current Status
- Phase 1 (Excel ETL): Completed  
- Phase 2 (SQL Analytics): In progress  
- Phase 3 (Power BI Dashboards): Planned  

---

## ℹ️ Notes
The raw incident dataset is not included in this repository due to file size limitations.  
This repository contains the cleaned dataset and transformation logic for portfolio and demonstration purposes.

---

## 👤 Author
**Rahul Singh**  
Data Analyst | Aspiring Data Scientist

