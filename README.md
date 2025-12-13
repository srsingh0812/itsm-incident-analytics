# itsm-incident-analytics
End-to-end ITSM Incident Analytics project using Excel (Power Query), SQL, and Power BI with SLA &amp; MTTR analysis.
ITSM Incident Analytics
Problem Statement

IT service management teams often struggle to track SLA compliance, resolution delays, and incident backlogs because incident data is scattered, inconsistent, and difficult to analyze.

This project focuses on transforming raw ITSM incident logs into a clean, analytics-ready dataset and defining standardized KPIs commonly used in enterprise IT support environments.

Project Overview

The goal of this project is to build an end-to-end ITSM analytics pipeline that supports operational reporting and deeper analytical use cases.

The work is structured in phases:

Data cleaning and feature engineering in Excel (Power Query)

KPI computation and aggregation using SQL

Interactive dashboards in Power BI

Optional machine learning for incident severity and SLA prediction

Tools Used

Excel (Power Query) for data cleaning and transformation

SQL for analytical queries and KPI calculation

Power BI for dashboarding and visualization

Key KPIs

Resolution Time (MTTR)

SLA Breach Indicator

Incident Aging (Days)

Reopen Count

Reassignment Count

Monthly Incident Trends

Data Preparation Summary

Standardized date and time fields

Created a single resolution timestamp across different incident states

Converted boolean and categorical fields into analytics-friendly formats

Engineered KPIs such as resolution time, aging, and SLA breach flags

Produced a SQL-ready incident fact table

Project Structure
itsm-incident-analytics/
├── data/
│   └── processed/
│       └── clean_incidents.csv
├── excel/
│   └── itsm_incident_etl.xlsx
├── docs/
│   ├── problem_statement.md
│   └── kpi_definitions.md
└── README.md

Project Status

Excel ETL: Completed

SQL modeling: In progress

Power BI dashboards: Planned

Machine learning extension: Planned

Notes

Due to GitHub file size limitations, the raw dataset is not included in this repository.
The cleaned dataset and full transformation logic are available upon request.

Author

Rahul Singh
Data Analyst
