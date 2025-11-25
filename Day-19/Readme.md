# 📘 Day 19 – Window Functions: ROW_NUMBER, RANK, DENSE_RANK

Topics: ROW_NUMBER(), RANK(), DENSE_RANK(), OVER clause

---
## 🔍 Overview

Day 19 focused on Window Functions, one of the most powerful features in SQL for analytical queries. They allow calculations across sets of rows without collapsing the result, unlike GROUP BY.

### 🧠 What I Learned

**1️⃣ Introduction to Window Functions** 

Window functions use the OVER clause to perform calculations across related rows.

General form:
```
function() OVER (PARTITION BY ... ORDER BY ...)
```

**2️⃣ Ranking Functions**

**⭐ ROW_NUMBER()**

Assigns unique sequential values (1, 2, 3, 4…).
Useful for:

Deduplicating rows

Selecting one row per group

Pagination

**⭐ RANK()**

Gives the same rank to ties, but leaves gaps.
Example: 1, 2, 2, 4

**⭐ DENSE_RANK()**

Gives the same rank to ties, but no gaps.
Example: 1, 2, 2, 3

---
## 💡 Key Tips & Concepts

PARTITION BY creates groups (e.g., by service).

ORDER BY inside the window defines ranking logic.

Window functions don’t reduce rows—every input row stays in the output.

You cannot filter directly on window results; wrap them in a subquery or CTE.

ORDER BY inside the window is different from the query’s final ORDER BY.

Choose the right ranking function depending on how you want to handle ties.

---
## 🏋️ Practice Questions

1. Rank patients by satisfaction score within each service.

2. Assign row numbers to staff ordered by their name.

3. Rank services by total patients admitted.

---
## 🏆 Daily Challenge 
**Question:** For each service, rank the weeks by patient satisfaction score (highest first). Show service, week, patient_satisfaction, patients_admitted, and the rank. Include only the top 3 weeks per service.

**✅ Solution:**
```
SELECT 
    service,
    week,
    patient_satisfaction,
    patients_admitted,
    sat_rank
FROM (
    SELECT
        service,
        week,
        patient_satisfaction,
        patients_admitted,
        RANK() OVER (
            PARTITION BY service
            ORDER BY patient_satisfaction DESC
        ) AS sat_rank
    FROM services_weekly
) AS ranked_weeks
WHERE sat_rank <= 3
ORDER BY service, sat_rank;

```
## 🔗 LinkedIn Post

**Check out my detailed post and SQL challenge update here 👉**
[Day 10 – SQL Challenge](https://www.linkedin.com/posts/mohammadrahil142_sqlwithidc-sql-windowfunctions-activity-7399162024309731328-mUya?utm_source=social_share_send&utm_medium=member_desktop_web&rcm=ACoAADocHhYBCyW3F2jiXG5MaOb0U1lc6mDQQJI)
