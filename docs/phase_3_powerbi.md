# 💼 Phase 3 - Power BI Dashboarding (ITSM Incident Analytics)

---

## 📌 Overview

Phase 3 focuses on visualizing validated ITSM KPIs using Power BI.

At this stage of the project:
- Phase 1 handled data preparation and cleaning using Excel and Power Query
- Phase 2 implemented data validation and KPI logic using PostgreSQL

In this phase, Power BI is used strictly for visualization.
All business logic and calculations are handled upstream in SQL.

---

## 🎯 Objective of Phase 3

The objectives of this phase are:

- 📊 Visualize ITSM KPIs built in PostgreSQL
- 📈 Provide operational and management-level insights
- ✅ Ensure Power BI results exactly match SQL outputs
- 🧩 Follow real-world ITSM reporting practices

---

## 🗄 Data Source

Power BI connects directly to PostgreSQL with the following configuration:

- Database: `itsm_analytics`
- Table: `incident_fact`
- Connection Mode: Import
- Refresh: Manual (controlled)

---

## 📊 KPIs Visualized

The following KPIs are visualized in Power BI:

- Total Incidents
- SLA Compliance Percentage
- SLA Breach Count
- Mean Time to Resolution (MTTR)
- Average Incident Aging (Days)
- Active vs Closed Incidents
- Monthly Incident Trends
- Priority-wise Incident Distribution

---

## 🛠 Dashboard Design Principles

The dashboard follows these principles:

- One KPI = One clear visual
- No calculations inside Power BI visuals
- SQL is the single source of truth
- Simple layout focused on decision-making
- Consistent filters across all visuals

---

## 🔍 Validation Approach

To ensure accuracy:

- SQL KPI outputs were cross-checked against Power BI values
- Random samples were manually verified
- Filters applied in Power BI were matched with SQL WHERE clauses
- Any mismatch was treated as a data issue, not a visualization issue

---

## 🧠 Key Learnings from Phase 3

- Power BI should visualize, not calculate
- Clean SQL logic simplifies dashboards
- KPI trust depends on upstream data quality
- ITSM reporting improves when metrics are clearly defined

---

## 📂 Project Status

- Phase 1: Data Preparation and ETL — Completed
- Phase 2: SQL Data Modeling and KPI Analysis — Completed
- Phase 3: Power BI Dashboarding — Completed

---

## 🚀 Next Steps

- Publish dashboard screenshots
- Add executive summary visuals
- Extend analysis with historical trend comparisons
