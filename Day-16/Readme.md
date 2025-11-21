# 📘 Day 16 – Subqueries in WHERE Clause
Topics: Subqueries in WHERE, nested queries, filtering with subqueries
---
## 🔍 Overview

Day 16 focused on Subqueries in the WHERE clause. These are powerful tools that allow SQL queries to filter data based on results from other queries, enabling deeper logic and more dynamic filtering.

---
## 🧠 What I Learned
### 1️⃣ Subqueries in WHERE Clause

**Basic structure:**
```
SELECT columns
FROM table
WHERE column IN (
    SELECT column
    FROM another_table
    WHERE condition
);
```

**2️⃣ Types of Subqueries**

**a) Single-value Subquery**

Returns one value.
```
SELECT name, age
FROM patients
WHERE age > (
    SELECT AVG(age) FROM patients
);
```
**b) Multi-value Subquery**

Returns multiple values.
```
SELECT *
FROM patients
WHERE service IN (
    SELECT service
    FROM services_weekly
    GROUP BY service
    HAVING AVG(patient_satisfaction) > 80
);
```
**c) EXISTS Subquery**

Best for checking existence efficiently.
```
SELECT DISTINCT service
FROM services_weekly sw1
WHERE EXISTS (
    SELECT 1
    FROM services_weekly sw2
    WHERE sw2.service = sw1.service
      AND sw2.patients_refused > 0
);
```
**d) Correlated Subquery**

Uses values from the outer query.
```
SELECT *
FROM patients p1
WHERE satisfaction > (
    SELECT AVG(satisfaction)
    FROM patients p2
    WHERE p2.service = p1.service
);
```
---
## 💡 Key Tips

✔ Use EXISTS instead of IN for large datasets.

✔ Avoid NOT IN when NULL values may appear.

✔ Subqueries are evaluated per row — optimize for performance.

✔ Always test subqueries independently before embedding them.

---
## 🏋️ Practice Questions

Find patients who are in services with above-average staff count.

List staff who work in services that had any week with patient satisfaction below 70.

Show patients from services where total admitted patients exceed 1000.

---

## 🏆 Daily Challenge

**Question:**
Find all patients admitted to services that had at least one week with refused patients AND had average satisfaction below the overall hospital average.

**Solution:**
```
SELECT 
    p.patient_id, 
    p.name, 
    p.service, 
    p.satisfaction
FROM patients p
JOIN (
    SELECT service 
    FROM services_weekly 
    GROUP BY service 
    HAVING 
        MAX(patients_refused) > 0
        AND AVG(patient_satisfaction) < (
            SELECT AVG(patient_satisfaction)
            FROM services_weekly
        )
) bad_services
ON p.service = bad_services.service;
```
---
## 🔗 LinkedIn Post

Check out my detailed post and SQL journey update here 👉
[Day 16 – SQL Challenge](https://www.linkedin.com/posts/mohammadrahil142_sql-datascience-learningjourney-activity-7397717007414247424-7B4k?utm_source=social_share_send&utm_medium=member_desktop_web&rcm=ACoAADocHhYBCyW3F2jiXG5MaOb0U1lc6mDQQJI)
