# 📘 Day 21 – Common Table Expressions (CTEs) & Final SQL Dashboard

Topics: CTEs, Multi-step Queries, Analytical Pipelines

---
## 🔍 Overview

Day 21 marks the final lesson of the SQL challenge, focusing on Common Table Expressions (CTEs) — one of the most powerful tools for organizing and structuring complex SQL queries.

CTEs allow you to break large problems into smaller, logical steps and build analytical workflows with clarity and precision.

---
## 🧠 What I Learned

### 1️⃣ Understanding CTEs

A CTE is a temporary named result set defined using the WITH keyword.
It helps structure multi-step logic and improves readability and maintainability.

**Key benefits:**

More readable complex queries

Reusable named sub-results

Step-by-step analytical pipelines

Easier debugging and testing

### 2️⃣ Multi-CTE Pipelines

Day 21 focused on chaining multiple CTEs to create a structured workflow:

CTE 1: Service-level metrics

CTE 2: Staff-level metrics

CTE 3: Patient demographics

CTE 4: Merge and compute final metrics

CTE 5: Add performance scoring

This modular approach mirrors real-world data engineering and analytics practices.

### 3️⃣ When to Use CTEs

CTEs are ideal for:

Breaking complex analysis into readable steps

Calculations that depend on earlier results

Dashboards and analytical reports

Organizing multi-layer aggregations

Replacing repeated subqueries

---
## 🏋️ Practice Questions

1.Create a CTE to calculate service statistics, then query from it.

2.Use multiple CTEs to break down a complex query into logical steps.

3.Build a CTE for staff utilization and join it with patient data.

---
## 🏆 Daily Challenge
**Question:** Create a comprehensive hospital performance dashboard using CTEs. Calculate: 1) Service-level metrics (total admissions, refusals, avg satisfaction), 2) Staff metrics per service (total staff, avg weeks present), 3) Patient demographics per service (avg age, count). Then combine all three CTEs to create a final report showing service name, all calculated metrics, and an overall performance score (weighted average of admission rate and satisfaction). Order by performance score descending.

**✅ Solution:**
```
WITH service_metrics AS (
    SELECT
        service,
        SUM(patients_admitted) AS total_admissions,
        SUM(patients_refused) AS total_refusals,
        AVG(patient_satisfaction) AS avg_satisfaction
    FROM services_weekly
    GROUP BY service
),

staff_metrics AS (
    SELECT
        s.service,
        COUNT(DISTINCT s.staff_id) AS total_staff,
        AVG(ss.present) AS avg_weeks_present
    FROM staff s
    LEFT JOIN staff_schedule ss
        ON s.staff_id = ss.staff_id
    GROUP BY s.service
),

patient_metrics AS (
    SELECT
        service,
        AVG(age) AS avg_age,
        COUNT(*) AS patient_count
    FROM patients
    GROUP BY service
),

combined AS (
    SELECT
        sm.service,
        sm.total_admissions,
        sm.total_refusals,
        sm.avg_satisfaction,
        stm.total_staff,
        stm.avg_weeks_present,
        pm.avg_age,
        pm.patient_count
    FROM service_metrics sm
    LEFT JOIN staff_metrics stm
        ON sm.service = stm.service
    LEFT JOIN patient_metrics pm
        ON sm.service = pm.service
),

final_dashboard AS (
    SELECT
        *,
        (
            (CAST(total_admissions AS FLOAT) 
                / NULLIF((total_admissions + total_refusals), 0)
            ) * 0.6
            +
            (avg_satisfaction / 100.0) * 0.4
        ) AS performance_score
    FROM combined
)

SELECT *
FROM final_dashboard
ORDER BY performance_score DESC;

```
## 🔗 LinkedIn Post
Check out my LinkedIn post here 👉  
[Day 21 – SQL Challenge](https://www.linkedin.com/posts/mohammadrahil142_sqlwithidc-dpdzero-indiandataclub-activity-7400290320233611265-8o9i?utm_source=social_share_send&utm_medium=member_desktop_web&rcm=ACoAADocHhYBCyW3F2jiXG5MaOb0U1lc6mDQQJI)
