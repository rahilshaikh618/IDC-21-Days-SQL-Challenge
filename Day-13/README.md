# 📅 Day 13 – SQL Challenge

🔗 Understanding INNER JOIN (Connecting Data Across Tables)

INNER JOIN is one of the most important SQL operations for combining related data from multiple tables. It allows you to merge records where values match in both tables — giving you clean, meaningful, and connected insights.

---
## Key Concepts

### 📘 What is INNER JOIN?

INNER JOIN returns only the rows where there is a match in both tables based on a specified condition.

**✔ Basic Syntax**
```
SELECT columns
FROM table1
INNER JOIN table2 
    ON table1.column = table2.column;
```

### 🔍 How INNER JOIN Works

Takes each row from table1

Searches for matching rows in table2

Returns only rows that match in both tables

Excludes all non-matching rows

### 🧪 Examples

**✅ 1. Join patients with staff (same service)**
```
SELECT
    p.patient_id,
    p.name AS patient_name,
    p.service,
    s.staff_name,
    s.role
FROM patients p
INNER JOIN staff s 
    ON p.service = s.service
ORDER BY p.service, p.name;
```

**✅ 2. Count number of staff per patient service**
```
SELECT
    p.patient_id,
    p.name,
    p.service,
    COUNT(s.staff_id) AS staff_count
FROM patients p
INNER JOIN staff s 
    ON p.service = s.service
GROUP BY p.patient_id, p.name, p.service;
```

**✅ 3. Joining with multiple conditions**
```
SELECT *
FROM services_weekly sw
INNER JOIN staff_schedule ss
    ON sw.service = ss.service
    AND sw.week = ss.week;
```

### 💡 Tips & Best Practices

✔ Use table aliases for cleaner queries
```
FROM patients p
INNER JOIN staff s
```

✔ Always qualify column names

Avoid ambiguity when two tables have same column name.
```
SELECT p.service   -- clear and explicit
```

✔ No need to write INNER – JOIN defaults to INNER JOIN
```
JOIN staff ON p.service = s.service;
```

✔ Chain multiple JOINs when working with several tables
```
FROM table1 t1
JOIN table2 t2 ON t1.id = t2.id
JOIN table3 t3 ON t2.id = t3.id;
```

✔ Use WHERE for additional filtering
```
FROM patients p
JOIN staff s ON p.service = s.service
WHERE p.age > 65;
```
---
## Practice Questions:

1. Join patients and staff based on their common service field (show patient and staff who work in same service).
2. Join services_weekly with staff to show weekly service data with staff information.
3. Create a report showing patient information along with staff assigned to their service.

---

## Daily Challenge:

**Question:** Create a comprehensive report showing patient_id, patient name, age, service, and the total number of staff members available in their service. Only include patients from services that have more than 5 staff members. Order by number of staff descending, then by patient name.

**✅ Solution**
```
SELECT 
  p.patient_id,
  p.name AS patient_name,
  p.age,
  p.service,
  svc.total_staff
FROM patients p
JOIN (
  SELECT service, COUNT(staff_id) AS total_staff
  FROM staff
  GROUP BY service
  HAVING COUNT(staff_id) > 5
) svc
  ON p.service = svc.service
ORDER BY svc.total_staff DESC, p.name;
```
---
## 🔗 LinkedIn Post
Check out my LinkedIn post here 👉  
[Day 13 – SQL Challenge](https://www.linkedin.com/posts/mohammadrahil142_sql-dataanalytics-learninginpublic-activity-7396133351713234944-xRPj?utm_source=social_share_send&utm_medium=member_desktop_web&rcm=ACoAADocHhYBCyW3F2jiXG5MaOb0U1lc6mDQQJI)

