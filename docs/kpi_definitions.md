# KPI Definitions

This document describes the key performance indicators (KPIs) derived as part of the ITSM Incident Analytics project.

---

## Resolution Time (Hours / MTTR)
**Definition:**  
The total time taken to resolve an incident, measured in hours.

**Calculation:**  
Difference between incident opening time and final resolved time.

**Purpose:**  
Used to evaluate resolution efficiency and support team performance.

---

## SLA Breach Indicator
**Definition:**  
A binary flag indicating whether an incident exceeded its defined SLA threshold.

**Values:**  
- `1` — SLA breached  
- `0` — SLA met  

**Purpose:**  
Helps track compliance with service-level agreements.

---

## Incident Aging (Days)
**Definition:**  
The number of days an incident has remained open.

**Calculation:**  
- For closed incidents: `resolved_date - opened_date`  
- For open incidents: `current_date - opened_date`

**Purpose:**  
Used to identify backlog issues and long-running incidents.

---

## Reopen Count
**Definition:**  
The number of times an incident was reopened after being resolved.

**Purpose:**  
Indicates resolution quality and potential root cause issues.

---

## Reassignment Count
**Definition:**  
The number of times an incident was reassigned between teams or individuals.

**Purpose:**  
Highlights inefficiencies in routing and ownership.

---

## Monthly Incident Volume
**Definition:**  
The total number of incidents created in a given month.

**Purpose:**  
Supports trend analysis and workload planning over time.
