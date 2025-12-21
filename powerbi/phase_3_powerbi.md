# Phase 3 - Power BI Dashboarding (ITSM Incident Analytics)

## Overview

Phase 3 focuses on visualizing validated ITSM KPIs using Power BI.

By this stage of the project:
- Phase 1 handled data preparation and cleaning using Excel and Power Query
- Phase 2 implemented data validation and KPI logic using PostgreSQL

In this phase, Power BI is used only for visualization.
All data logic and calculations are handled upstream in SQL.

---

## Objective of Phase 3

The objectives of this phase are:
- Visualize ITSM KPIs built in PostgreSQL
- Provide operational and management-level insights
- Ensure Power BI results exactly match SQL outputs
- Follow real-world ITSM reporting practices

---

## Data Source

The Power BI dashboard connects to the following source:
- Database: PostgreSQL
- Database name: itsm_analytics
- Table used: incident_fact

Only the analytics-ready fact table is used.
Raw tables and CSV files are not consumed in Power BI.

---

## Power BI Connection Approach

The following approach is used:
- Connection type: PostgreSQL (Import mode)
- Authentication: Database credentials
- Transformations: None in Power BI
- Business logic: Implemented in SQL, not DAX

This ensures PostgreSQL remains the single source of truth.

---

## Data Model Design

The Power BI data model follows a simple structure:
- Single fact table: incident_fact
- No table relationships
- All KPIs implemented as measures

This design improves clarity, performance, and maintainability.

---

## Core Measures Implemented

The following measures are created in Power BI:
- Total Incidents
- Active Incidents
- SLA Compliance Percentage
- Mean Time to Resolution (MTTR)

All measures are validated against SQL queries.

---

## Dashboard Structure

### Page 1 - Executive Overview

This page is designed for service managers and leadership.

It includes:
- KPI cards for Total Incidents, Active Incidents, SLA Compliance, and MTTR
- Monthly incident trend chart

Purpose:
- Provide a high-level operational health view
- Monitor overall SLA performance

---

### Page 2 - SLA and Priority Analysis

This page focuses on performance and risk areas.

It includes:
- SLA compliance by priority
- MTTR by priority

Purpose:
- Identify high-risk priorities
- Support prioritization and decision-making

---

### Page 3 - Backlog and Aging

This page supports operational teams.

It includes:
- Aging distribution of open incidents
- Active backlog analysis

Purpose:
- Monitor unresolved incidents
- Support escalation and workload planning

---

## Filters and Interactivity

The following slicers are added:
- Priority
- Incident state
- Assignment group
- Created month

These allow interactive analysis without altering KPI logic.

---

## Validation and Accuracy

Before finalizing the dashboards:
- KPI values were compared with SQL outputs
- No discrepancies were found
- Any mismatch was resolved in DAX, not SQL

This ensures complete trust in the reported metrics.

---

## Repository Artifacts

The following file is included in this phase:

powerbi/
  itsm_incident_dashboard.pbix

Notes:
- The PBIX file does not store database credentials
- Users must configure their own PostgreSQL connection to refresh data

---

## Key Learnings

- Power BI should visualize data, not fix it
- Clean SQL simplifies dashboard logic
- Measure-driven design improves accuracy
- Validation between SQL and BI is critical

---

## Project Status

Phase 1 - Data Preparation and ETL - Completed  
Phase 2 - SQL Analytics and KPI Computation - Completed  
Phase 3 - Power BI Dashboarding - Completed
