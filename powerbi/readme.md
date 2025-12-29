# Phase 3 – Power BI Dashboarding  
ITSM Incident Analytics

## Overview

Phase 3 focuses on **visualizing validated ITSM KPIs** using Power BI.

At this stage of the project:
- Phase 1 handled **data preparation and cleaning** using Excel (Power Query)
- Phase 2 implemented **data validation and KPI logic** using PostgreSQL
- Phase 3 uses Power BI **only for visualization**

All calculations and business logic are handled upstream in SQL to ensure
consistency, auditability, and alignment with real-world ITSM reporting.

---

## Objectives of Phase 3

The key goals of this phase are:

- Visualize ITSM KPIs built in PostgreSQL
- Provide operational and management-level insights
- Ensure Power BI results exactly match SQL outputs
- Follow real ITSM reporting and dashboarding practices

---

## Data Source

Power BI connects directly to the PostgreSQL analytics layer.

Source details:
- Database: `itsm_analytics`
- Table: `incident_fact`
- Connection mode: Import
- Refresh model: Manual (for development)

No transformations or calculations are performed in Power BI.

---

## KPIs Visualized

The dashboard includes the following KPIs:

- Total Incidents
- Active Incidents
- Mean Time to Resolve (MTTR / MTTH)
- SLA Compliance Percentage
- Monthly Incident Volume Trend
- Incident Aging Distribution

All KPI values are validated against SQL query outputs.

---

## Key Design Principles Followed

- No DAX-based business logic
- No Power Query transformations in Power BI
- Clean, minimal visuals focused on clarity
- One source of truth: SQL
- Reproducible and auditable metrics

This mirrors how Power BI is used in mature ITSM analytics environments.

---

## Validation Checks Performed

Before finalizing the dashboard:

- KPI totals matched SQL query results
- No negative or null resolution times
- SLA flags contained only valid values (0 / 1)
- Date hierarchies aligned with created_month
- Aging buckets sorted correctly using a numeric sort column

---

## Dashboard File

The Power BI dashboard file is available here:

