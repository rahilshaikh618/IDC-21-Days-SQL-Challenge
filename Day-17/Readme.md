# 📘 Day 17 – Subqueries in SELECT and FROM Clause
Topics: Subqueries in SELECT, derived tables, inline views
---
## 🔍 Overview

Day 17 focused on using subqueries inside the SELECT and FROM clauses. These techniques allow SQL queries to generate calculated fields, build intermediate result sets, and structure complex logic more clearly.

### **🧠 What I Learned**

1️⃣ Subqueries in SELECT

Subqueries inside SELECT act as calculated columns, helping derive values such as averages, counts, deviations, or any metric required per row.

---
### Key points:

-Must return one value

-Useful for row-level comparisons

-Good for quick metrics and aggregations

**2️⃣ Subqueries in FROM (Derived Tables)**

-Derived tables (inline views) are subqueries used as temporary tables that can be queried further.

**Benefits:**

-Break down complex logic into steps

-Enhance readability and maintainability

-Allow combining multiple calculations before the final query

-Must always be given an alias

---
## 💡 Key Tips

-Every derived table must have an alias

-Subqueries inside SELECT must return a single value (scalar)

-Derived tables are better than writing long, unreadable queries

-Correlated subqueries run once per row, so use carefully

-CTEs (coming later) provide an even cleaner alternative

---
## 🏋️ Practice Questions

1. Show each patient with their service's average satisfaction as an additional column.

2. Create a derived table of service statistics and query from it.

3. Display staff with their service's total patient count as a calculated field.

---
## 🏆 Daily Challenge

**Question:**
Create a report showing each service with: service name, total patients admitted, the difference between their total admissions and the average admissions across all services, and a rank indicator ('Above Average', 'Average', 'Below Average'). Order by total patients admitted descending.

**✅ Solution:**
```
WITH service_totals AS (
    SELECT 
        service,
        SUM(patients_admitted) AS total_admitted
    FROM services_weekly
    GROUP BY service
),
average_admissions AS (
    SELECT AVG(total_admitted) AS avg_admitted
    FROM service_totals
)
SELECT 
    st.service,
    st.total_admitted,
    (st.total_admitted - aa.avg_admitted) AS diff_from_avg,
    CASE
        WHEN st.total_admitted > aa.avg_admitted THEN 'Above Average'
        WHEN st.total_admitted = aa.avg_admitted THEN 'Average'
        ELSE 'Below Average'
    END AS rank_indicator
FROM service_totals st
CROSS JOIN average_admissions aa
ORDER BY st.total_admitted DESC;
```
## 🔗 LinkedIn Post

**Check out my detailed post and SQL challenge update here 👉**
[Day 17 – SQL Challenge](https://www.linkedin.com/posts/mohammadrahil142_sqlwithidc-indiandataclub-dpdzero-activity-7398050335279308800-_skL?utm_source=social_share_send&utm_medium=member_desktop_web&rcm=ACoAADocHhYBCyW3F2jiXG5MaOb0U1lc6mDQQJI)
