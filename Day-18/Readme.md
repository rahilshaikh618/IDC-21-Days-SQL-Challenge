# 📘 Day 18 – UNION and UNION ALL

Topics: UNION, UNION ALL, combining result sets

---
## 🔍 Overview

Day 18 focused on combining data from multiple queries using UNION and UNION ALL. These commands are essential when merging data from different tables, different conditions, or different perspectives into a single unified dataset.

### 🧠 What I Learned

**1️⃣ UNION**

Combines results from two or more SELECT statements

Removes duplicate rows

Slightly slower due to duplicate checking

Column names are taken from the first SELECT

**2️⃣ UNION ALL**

Combines results without removing duplicates

Faster and more efficient

Useful when duplicates are acceptable or guaranteed not to exist

**⚙️ Requirements for UNION / UNION ALL**

To combine queries successfully:

Each SELECT must return the same number of columns

The data types must be compatible

The final ORDER BY must be placed after all queries, not inside each one

---
## 💡 Tips & Best Practices

✔ Use UNION ALL whenever possible for better performance

✔ Use literals (e.g., 'Patient', 'Staff') to label data sources

✔ Use UNION when removing duplicates is important

✔ The final output is always sorted using a single ORDER BY at the end

✔ Test each SELECT separately before combining

---
## 🏋️ Practice Questions

1. Combine patient names and staff names into a single list.
2. Create a union of high satisfaction patients (>90) and low satisfaction patients (<50).
3. List all unique names from both patients and staff tables.

---
## 🏆 Daily Challenge
**Question:** Create a comprehensive personnel and patient list showing: identifier (patient_id or staff_id), full name, type ('Patient' or 'Staff'), and associated service. Include only those in 'surgery' or 'emergency' services. Order by type, then service, then name.

**✅ Solution:**
```
SELECT 
    p.patient_id AS identifier,
    p.name AS full_name,
    'Patient' AS type,
    p.service
FROM patients p
WHERE p.service IN ('surgery', 'emergency')

UNION

SELECT 
    s.staff_id AS identifier,
    s.staff_name AS full_name,
    'Staff' AS type,
    s.service
FROM staff s
WHERE s.service IN ('surgery', 'emergency')

ORDER BY type, service, full_name;
```
---
## 🔗 LinkedIn Post
Check out my LinkedIn post here 👉  
[Day 18 – SQL Challenge](https://www.linkedin.com/posts/mohammadrahil142_sqlwithidc-sql-union-activity-7399082094921961472-EWsL?utm_source=social_share_send&utm_medium=member_desktop_web&rcm=ACoAADocHhYBCyW3F2jiXG5MaOb0U1lc6mDQQJI)
