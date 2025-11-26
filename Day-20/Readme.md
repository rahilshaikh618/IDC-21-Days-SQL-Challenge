# 📘 Day 20 – Aggregate Window Functions

Topics: Running Totals, Moving Averages, Window Frames

---
## 🔍 Overview

Day 20 focused on Aggregate Window Functions, which allow powerful analytical calculations such as running totals, moving averages, cumulative statistics, and rolling comparisons — all without collapsing rows, unlike GROUP BY.

These techniques are essential for time-series analysis and performance tracking.

### 🧠 What I Learned

**1️⃣ Aggregate Window Functions**

These include:

SUM() OVER → Running totals, cumulative sums

AVG() OVER → Moving averages

COUNT() OVER → Running counts

MIN() / MAX() OVER → Running min or max values

They allow calculations that look backward or forward across rows.

**2️⃣ Window Frame Clause**

The window frame controls how many rows a calculation should consider:

ROWS BETWEEN start AND end


**Common frame options:**

UNBOUNDED PRECEDING – from the start of the partition

N PRECEDING – last N rows

CURRENT ROW – only the current row

N FOLLOWING – next N rows

UNBOUNDED FOLLOWING – until the end

**Examples:**

Running total → UNBOUNDED PRECEDING to CURRENT ROW

3-week moving average → 2 PRECEDING to CURRENT ROW

Centered window → 2 PRECEDING to 2 FOLLOWING

---
## 💡 Key Concepts & Tips

With ORDER BY inside OVER, the default frame is:
ROWS BETWEEN UNBOUNDED PRECEDING AND CURRENT ROW

Without ORDER BY, the window applies to the entire partition

Moving averages require explicit window frames

**Window aggregates allow:**

Trend analysis

Rolling comparisons

Highlighting performance deviations

Window functions can reference other window functions (but cannot be nested)

---
## 🏋️ Practice Questions

1. Calculate running total of patients admitted by week for each service.
2. Find the moving average of patient satisfaction over 4-week periods.
3. Show cumulative patient refusals by week across all services.

---
## 🏆 Daily Challenge
**Question:** Create a trend analysis showing for each service and week: week number, patients_admitted, running total of patients admitted (cumulative), 3-week moving average of patient satisfaction (current week and 2 prior weeks), and the difference between current week admissions and the service average. Filter for weeks 10-20 only.

**✅ Solution**
```
WITH service_stats AS (
    SELECT 
        service,
        AVG(patients_admitted) AS avg_admissions
    FROM services_weekly
    GROUP BY service
)
SELECT
    sw.service,
    sw.week,
    sw.patients_admitted,
    
    -- Running total of patients admitted (cumulative)
    SUM(sw.patients_admitted) OVER (
        PARTITION BY sw.service
        ORDER BY sw.week
    ) AS running_total,
    
    -- 3-week moving average of patient satisfaction (current week + previous 2)
    AVG(sw.patient_satisfaction) OVER (
        PARTITION BY sw.service
        ORDER BY sw.week
        ROWS BETWEEN 2 PRECEDING AND CURRENT ROW
    ) AS moving_avg_3week,
    
    -- Difference from service's average admissions
    (sw.patients_admitted - ss.avg_admissions) AS diff_from_service_avg

FROM services_weekly sw
JOIN service_stats ss 
    ON sw.service = ss.service
WHERE sw.week BETWEEN 10 AND 20
ORDER BY sw.service, sw.week;
```
---
## 🔗 LinkedIn Post
Check out my LinkedIn post here 👉  
[Day 13 – SQL Challenge](https://www.linkedin.com/posts/mohammadrahil142_sqlwithidc-sql-dataanalytics-activity-7399538850718736384-YS7m?utm_source=social_share_send&utm_medium=member_desktop_web&rcm=ACoAADocHhYBCyW3F2jiXG5MaOb0U1lc6mDQQJI)
