# 📊 Phase 3 – Power BI Dashboarding
ITSM Incident Analytics

## 🔍 Overview

Phase 3 focuses on **visualizing validated ITSM KPIs** using Power BI.

At this stage of the project, the analytical foundation is already established upstream.

- Phase 1 handled **data preparation and cleaning** using Excel (Power Query)
- Phase 2 implemented **data validation and KPI logic** using PostgreSQL
- Phase 3 uses Power BI **only for visualization**

All calculations and business logic are executed in SQL to ensure consistency, auditability, and alignment with real-world ITSM reporting practices.

---

## 🎯 Objectives of Phase 3

The objectives of this phase are:

- Visualize ITSM KPIs built in PostgreSQL
- Support operational and management-level decision-making
- Ensure Power BI outputs exactly match SQL results
- Follow enterprise-grade ITSM dashboarding standards

---

## 🗄️ Data Source

Power BI connects directly to the PostgreSQL analytics layer.

Source details:

- Database: `itsm_analytics`
- Table: `incident_fact`
- Connection mode: Import
- Refresh model: Manual (development phase)

No transformations, calculated columns, or KPI logic are implemented inside Power BI.

---

## 📈 KPIs Visualized

The dashboard provides visibility into core ITSM performance metrics:

- Total incident volume
- Active incident backlog
- Mean Time to Resolve (MTTR / MTTH)
- SLA compliance percentage
- Monthly incident volume trends
- Incident aging distribution

All KPI values displayed in the dashboard are validated against SQL query outputs.

---

## 🎨 Key Design Principles Followed

This phase follows strict separation of concerns:

- No DAX-based business logic
- No Power Query transformations inside Power BI
- SQL used as the single source of truth
- Clean, minimal visuals focused on interpretability
- Reproducible and auditable KPIs

This mirrors how Power BI is used in mature ITSM analytics environments.

---

## ✅ Validation Checks Performed

Before finalizing the dashboard, the following validations were completed:

- KPI totals matched SQL query results
- Resolution times contained no negative or null values
- SLA flags contained only valid binary values (0 / 1)
- Date hierarchies aligned using `created_month`
- Aging buckets sorted using a numeric sort column

---

## 🔐 Row-Level Security (RLS) Implementation

### 🔒 Why Row-Level Security Is Implemented

In real-world ITSM environments, incident data is not globally visible. Access is typically restricted based on operational responsibility.

RLS is implemented to:

- Ensure users only see incidents relevant to their assignment groups
- Maintain data confidentiality across teams
- Deliver accurate, role-specific KPIs
- Prepare the dashboard for production BI deployment

---

### 🧩 Columns Controlling Data Access

Access control is driven by the following column:

- `assignment_group`

RLS rules filter data at row level using logic such as:

- `assignment_group IN ('Group 70', 'Group 56', 'Group 24')`

Only incidents belonging to the allowed assignment groups are visible to the user.

---

### 👥 Security Roles Defined

The following Power BI role has been configured:

- Role name: `Assignment_Group_User`
- Access limited to specific assignment groups
- Multiple values handled using an `IN` condition
- Simulates real ITSM engineer or team-level access

This design can be extended to:

- Manager-level access
- Location-based access control
- Dynamic user-to-group mapping using email-based RLS

---

### 🧪 Validation and Testing

RLS behavior was validated using:

- Power BI **View as Role** feature
- KPI cards and visuals cross-checked for correct filtering
- Consistent behavior verified across all dashboard components

---

## 🚀 Why This Matters for Analytics and ML Readiness

Implementing RLS ensures:

- Clean separation between data, logic, and access
- Trustworthy KPIs at different organizational levels
- Secure foundations for downstream analytics and ML use cases

This elevates the dashboard from exploratory reporting to **production-grade BI architecture**.

---

## 📁 Dashboard File

The Power BI dashboard file is available in this repository:

- `itsm_incident_dashboard.pbix`
