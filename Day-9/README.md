# 📘 Day 9: Date Functions in SQL

### 🧠 Topics Covered:
`DATE` Functions | Date Arithmetic | `EXTRACT`

---

## 📖 Concept Overview

Date functions help you **analyze, manipulate, and filter** data based on dates and times in SQL.  
They are essential for working with time-based datasets like hospital records, sales data, or attendance logs.

### 🔧 **Common Date Functions**


| Function / Syntax | Description | Example |
|--------------------|-------------|----------|
| `DATE('now')` | Current date | `2024-11-12` |
| `JULIANDAY(date)` | Converts to Julian day number | `JULIANDAY('2024-11-12')` |
| `DATE(date, '+1 day')` | Adds 1 day to a date | `DATE('2024-11-12', '+1 day')` |
| `strftime('%Y', date)` | Extract year | `2024` |
| `strftime('%m', date)` | Extract month | `11` |
| `strftime('%d', date)` | Extract day | `12` |


### 🧩 **Examples**

### 🏥 1️⃣ Calculate length of stay (in days)
```sql
SELECT
    patient_id,
    name,
    arrival_date,
    departure_date,
    CAST(JULIANDAY(departure_date) - JULIANDAY(arrival_date) AS INTEGER) AS stay_days
FROM patients;
```
### 📅 2️⃣ Extract year and month from date
```sql
SELECT
    patient_id,
    strftime('%Y', arrival_date) AS arrival_year,
    strftime('%m', arrival_date) AS arrival_month
FROM patients;
```
### 📆 3️⃣ Filter by date range
```sql
SELECT *
FROM patients
WHERE arrival_date BETWEEN '2024-01-01' AND '2024-12-31';
```

### 🌤️ 4️⃣ Find patients admitted in a specific month (e.g., June)
```sql
SELECT *
FROM patients
WHERE strftime('%m', arrival_date) = '06';  -- June
```

## 💡 Tips & Tricks

✅ Use ISO format: Always store and query dates as 'YYYY-MM-DD' for consistency.

✅ Calculate date differences (varies by database):
```
-- MySQL
DATEDIFF(date2, date1)
```

✅ A Avoid date functions in WHERE for large datasets — they disable index usage.

✅ Cast date calculations to INTEGER or REAL to ensure consistency across systems.

---
## 🧠 Practice Questions

1️⃣ Extract the year from all patient arrival dates.
2️⃣ Calculate the length of stay for each patient (departure_date - arrival_date).
3️⃣ Find all patients who arrived in a specific month (e.g., June).

---
## 🏆 Daily Challenge
Question: Calculate the average length of stay (in days) for each service, showing only services where the average stay is more than 7 days.
Also display the count of patients and order results by average stay (descending).

**✅ Solution:**
```sql
SELECT
    service,
    COUNT(*) AS patient_count,
    ROUND(AVG(DATEDIFF(departure_date, arrival_date)), 2) AS avg_stay_days
FROM patients
WHERE arrival_date IS NOT NULL
  AND departure_date IS NOT NULL
  AND DATEDIFF(departure_date, arrival_date) >= 0
GROUP BY service
HAVING AVG(DATEDIFF(departure_date, arrival_date)) > 7
ORDER BY avg_stay_days DESC;
```
## 🔗 LinkedIn Post

**Check out my detailed post and SQL challenge update here 👉**
[Day 9 – SQL Challenge](https://www.linkedin.com/posts/mohammadrahil142_sqlwithidc-indiandataclub-dpdzero-activity-7394282220305244160-u5xK?utm_source=social_share_send&utm_medium=member_desktop_web&rcm=ACoAADocHhYBCyW3F2jiXG5MaOb0U1lc6mDQQJI)
