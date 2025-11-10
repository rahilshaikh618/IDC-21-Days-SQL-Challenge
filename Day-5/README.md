# 🧠 Day 5 – Aggregate Functions (COUNT, SUM, AVG, MIN, MAX)

Aggregate Functions in SQL

---

## 📘 Topics Covered
**Topics:** `COUNT`, `SUM`, `AVG`, `MIN`, `MAX` functions  

Aggregate functions in SQL are used to perform calculations on a set of values and return a single summarized result.  
They are especially useful for analyzing numerical data, generating reports, and deriving insights such as totals, averages, or extreme values.

---

## 📚 Reading & Resources

Aggregate functions work on groups of rows (or entire tables) and are often used with the `GROUP BY` clause to compute results for each group.  
For example, you can calculate the total number of patients per service or the average satisfaction score across departments.


### **Basic Syntax:**
```sql
-- COUNT(): Counts the number of rows
SELECT COUNT(column_name)
FROM table_name
WHERE condition;

-- SUM(): Adds up all values in a column
SELECT SUM(column_name)
FROM table_name
WHERE condition;

-- AVG(): Calculates the average value
SELECT AVG(column_name)
FROM table_name
WHERE condition;

-- MIN(): Finds the smallest value
SELECT MIN(column_name)
FROM table_name
WHERE condition;

-- MAX(): Finds the largest value
SELECT MAX(column_name)
FROM table_name
WHERE condition;
```
### Key Points: ###

Aggregate functions ignore NULL values (except COUNT(*) which counts all rows).

They can be combined with GROUP BY for category-based summaries.

Often used with HAVING to filter aggregated results.

Useful in data reporting and analysis (e.g., total patients, highest cost, average satisfaction).

---
## 🧩 Practice Questions

1. Count the total number of patients in the hospital.
2. Calculate the average satisfaction score of all patients.
3. Find the minimum and maximum age of patients.
---
## 🚀 Daily Challenge

**Question:**
Calculate the total number of patients admitted, total patients refused, and the average patient satisfaction across all services and weeks. 
Round the average satisfaction to 2 decimal places.

**✅ Solution:**
```sql
SELECT 
    SUM(patients_admitted) AS total_patients_admitted,
    SUM(patients_refused) AS total_patients_refused,
    ROUND(AVG(satisfaction), 2) AS avg_satisfaction
FROM services_weekly;
```
---
## 🔗 LinkedIn Post

**Check out my detailed post and SQL challenge update here 👉**
[Day 5 – SQL Challenge](https://www.linkedin.com/posts/mohammadrahil142_sqlwithidc-21daychallenge-dataanalytics-activity-7392658099658059776-s633?utm_source=social_share_send&utm_medium=member_desktop_web&rcm=ACoAADocHhYBCyW3F2jiXG5MaOb0U1lc6mDQQJI)
