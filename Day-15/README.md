# Day 15 — Multiple Joins (SQL)

**Topics Covered:** Joining more than two tables, complex relationships, conditional aggregation, reporting

---

## 🔑 Key Concepts
Build confidence combining 3+ tables in a single query to produce meaningful reports. Focus on:

* Correct join order and join types (INNER, LEFT)
* Avoiding row multiplication or handling it with aggregation
* Conditional aggregation (COUNT/ SUM with `CASE WHEN`)

---

## 📚 Reading & Resources

Multiple joins combine data from three or more tables into one result set. Typical workflow:

1. Identify the *main table* (the table you want all rows from).
2. Decide which relationships must be preserved (use LEFT JOIN) and which must be strict (use INNER JOIN).
3. Add joins incrementally and test.

**Basic syntax**

```sql
SELECT columns
FROM table1
JOIN table2 ON table1.key = table2.key
JOIN table3 ON table2.key = table3.key
LEFT JOIN table4 ON table3.key = table4.key;
```

---

## ✅ Tips & Tricks

* **Start with the main table.** The first `FROM` table determines which rows are guaranteed to appear.
* **LEFT JOIN** to keep all rows from the left table.
* **INNER JOIN** to keep only rows with matches on both sides.
* **Join order matters** when mixing LEFT and INNER joins — different orders can produce different results.
* **Use `GROUP BY` or `DISTINCT`** if joins create duplicate logical rows.
* **Test step-by-step:** add one join at a time to verify intermediate results.

---

## ✍️ Examples (copy-paste ready)

### 1) Comprehensive service report (one row per service-week)

```sql
SELECT
    sw.service,
    sw.week,
    sw.patients_admitted,
    COUNT(DISTINCT s.staff_id) AS total_staff,
    SUM(CASE WHEN ss.present = 1 THEN 1 ELSE 0 END) AS staff_present
FROM services_weekly sw
LEFT JOIN staff s
    ON sw.service = s.service
LEFT JOIN staff_schedule ss
    ON s.staff_id = ss.staff_id
    AND sw.week = ss.week
WHERE sw.week = 10
GROUP BY sw.service, sw.week, sw.patients_admitted;
```

### 2) Patient admission with staff availability

```sql
SELECT
    p.patient_id,
    p.name,
    p.service,
    p.arrival_date,
    COUNT(DISTINCT s.staff_id) AS assigned_staff,
    AVG(CASE WHEN ss.present IN (1,'1','Y','y','yes') THEN 1 ELSE 0 END) AS avg_staff_presence
FROM patients p
JOIN staff s
    ON p.service = s.service
LEFT JOIN staff_schedule ss
    ON s.staff_id = ss.staff_id
GROUP BY p.patient_id, p.name, p.service, p.arrival_date;
```

---

## 🧩 Practice Questions

1. Join `patients`, `staff`, and `staff_schedule` to show patient service and staff availability.
2. Combine `services_weekly` with `staff` and `staff_schedule` for comprehensive service analysis.
3. Create a multi-table report showing patient admissions with staff information.

---

## 🚨 Daily Challenge (Day 15)

**Question:** Create a comprehensive service analysis report for **week 20** showing: `service` name, total patients admitted that week, total patients refused, average patient satisfaction, count of staff assigned to service, and count of staff present that week. Order by patients admitted descending.

### ✅ Solution

```sql
SELECT 
    sw.service,
    SUM(sw.patients_admitted) AS total_admitted,
    SUM(sw.patients_refused) AS total_refused,
    ROUND(AVG(sw.patient_satisfaction), 2) AS avg_patient_satisfaction,
    COUNT(DISTINCT s.staff_id) AS staff_count,
    SUM(CASE WHEN ss.present IN (1,'1','Y','y','yes','true') AND ss.week = 20 THEN 1 ELSE 0 END) AS staff_present_week20
FROM services_weekly sw
LEFT JOIN staff s
    ON sw.service = s.service
LEFT JOIN staff_schedule ss
    ON s.staff_id = ss.staff_id
WHERE sw.week = 20
GROUP BY sw.service
ORDER BY total_admitted DESC;
```
---
## 🔗 LinkedIn Post
Check out my LinkedIn post here 👉  
[Day 15 – SQL Challenge](https://www.linkedin.com/posts/mohammadrahil142_sql-dataanalytics-indiandataclub-activity-7396928655261667328-7bX1?utm_source=social_share_send&utm_medium=member_desktop_web&rcm=ACoAADocHhYBCyW3F2jiXG5MaOb0U1lc6mDQQJI)
