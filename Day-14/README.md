# Day 14 – LEFT JOIN and RIGHT JOIN

## 📘 Topics

**LEFT JOIN**, **RIGHT JOIN**, and handling **unmatched records** in SQL.

---

## 📚 Reading & Resources

**LEFT JOIN** returns all rows from the left table and matching rows from the right. If no match is found, NULLs appear for right table columns.

**RIGHT JOIN** returns all rows from the right table with matching rows from the left.

---

## 🔧 Basic Syntax

```sql
-- LEFT JOIN (most common)
SELECT columns
FROM table1
LEFT JOIN table2 ON table1.column = table2.column;

-- RIGHT JOIN (less common)
SELECT columns
FROM table1
RIGHT JOIN table2 ON table1.column = table2.column;
```

---

## 🔍 Key Differences

* **INNER JOIN** → Only matching rows from both tables.
* **LEFT JOIN** → All rows from left + matches from right (NULL if no match).
* **RIGHT JOIN** → All rows from right + matches from left (NULL if no match).

---

## 📝 Examples

### 1. All staff with their schedule (including those without schedules)

```sql
SELECT
    s.staff_id,
    s.staff_name,
    s.role,
    s.service,
    COUNT(ss.week) AS weeks_scheduled,
    SUM(COALESCE(ss.present, 0)) AS weeks_present
FROM staff s
LEFT JOIN staff_schedule ss ON s.staff_id = ss.staff_id
GROUP BY s.staff_id, s.staff_name, s.role, s.service;
```

### 2. Find staff with NO schedule records

```sql
SELECT s.*
FROM staff s
LEFT JOIN staff_schedule ss ON s.staff_id = ss.staff_id
WHERE ss.staff_id IS NULL;
```

### 3. All services with their patient stats (even if no patients)

```sql
SELECT
    sw.service,
    sw.week,
    COUNT(p.patient_id) AS patient_count
FROM services_weekly sw
LEFT JOIN patients p ON sw.service = p.service
GROUP BY sw.service, sw.week;
```

---

## 💡 Tips & Tricks

### ✔️ Rewrite RIGHT JOIN using LEFT JOIN

```sql
-- Equivalent forms:
FROM table1 RIGHT JOIN table2 ON ...
FROM table2 LEFT JOIN table1 ON ...
```

### ✔️ Use COALESCE() to replace NULL values

```sql
SELECT
    s.staff_name,
    COALESCE(SUM(ss.present), 0) AS weeks_present
FROM staff s
LEFT JOIN staff_schedule ss ON s.staff_id = ss.staff_id;
```

### ✔️ Find non-matching rows

```sql
SELECT s.*
FROM staff s
LEFT JOIN staff_schedule ss ON s.staff_id = ss.staff_id
WHERE ss.staff_id IS NULL;
```

### ✔️ WHERE vs ON with LEFT JOIN

```sql
-- ON: filters before join, keeps all left rows
LEFT JOIN table2 ON condition AND table2.column = 'value'

-- WHERE: filters after join, may remove left rows
LEFT JOIN table2 ON condition
WHERE table2.column = 'value';
```

### ✔️ LEFT JOIN preserves row count from left table

It may increase when right table has multiple matching rows.

---

## ✅ Summary

Mastering LEFT and RIGHT JOINs helps handle real-world relational data, analyze missing information, and build cleaner, more accurate reports.

---
## 🧩 Practice Questions:

1. Show all staff members and their schedule information (including those with no schedule entries).
2. List all services from services_weekly and their corresponding staff (show services even if no staff assigned).
3. Display all patients and their service's weekly statistics (if available).

---

### 🚀 Daily Challenge:

**Question:** Create a staff utilisation report showing all staff members (staff_id, staff_name, role, service) and the count of weeks they were present (from staff_schedule). Include staff members even if they have no schedule records. Order by weeks present descending.

### ✅ Solution:
```
SELECT 
    s.staff_id,
    s.staff_name,
    s.role,
    s.service,
    COALESCE(
        COUNT(DISTINCT CASE WHEN ss.present = 1 THEN ss.week END),
        0
    ) AS total_week_present
FROM staff s
LEFT JOIN staff_schedule ss
    ON s.staff_id = ss.staff_id
GROUP BY 
    s.staff_id,
    s.staff_name,
    s.role,
    s.service
ORDER BY 
    total_week_present DESC;
```
---
## 🔗 LinkedIn Post
Check out my LinkedIn post here 👉  
[Day 14 – SQL Challenge](https://www.linkedin.com/posts/mohammadrahil142_sqlwithidc-sqlchallenge-dataanalytics-activity-7396584748531380224-Ev6z?utm_source=social_share_send&utm_medium=member_desktop_web&rcm=ACoAADocHhYBCyW3F2jiXG5MaOb0U1lc6mDQQJI)
