# 🧠 Day 6 – GROUP BY Clause

 GROUP BY Clause and Aggregating by Categories

---

## 📘 Topics Covered
**Topics:** `GROUP BY`, aggregating by categories  

The `GROUP BY` clause divides rows into groups based on column values, allowing you to apply aggregate functions (`COUNT`, `SUM`, `AVG`, etc.) to each group individually.  
It is a powerful way to summarize and categorize data in SQL.

---

## 📚 Reading & Resources

### **Basic Syntax:**
```sql
SELECT column1, aggregate_function(column2)
FROM table_name
GROUP BY column1;
```
### **Key Rules:**

Every non-aggregated column in the SELECT clause must appear in the GROUP BY clause.

Each group produces one result row.

Use aggregate functions (COUNT, SUM, AVG, etc.) on other columns.

You can group by multiple columns for detailed segmentation.

### **💡 Tips & Tricks**

✅ Think “one row per group” — if you GROUP BY service, you’ll get one row per service.
✅ Execution order in SQL:
FROM → WHERE → GROUP BY → SELECT → ORDER BY → LIMIT
✅ Use WHERE before GROUP BY to filter rows.
✅ Use HAVING after GROUP BY to filter aggregated results.
✅ Grouping multiple columns increases granularity for deeper insights.

---
## 🧩 Practice Questions & Solutions
1. Count the number of patients by each service.
2. Calculate the average age of patients grouped by service.
3. Find the total number of staff members per role.

---
## 🚀 Daily Challenge

**Question:**
For each hospital service, calculate the total number of patients admitted, total patients refused, and the admission rate
(percentage of requests that were admitted).
Order the results by admission rate in descending order.

**✅ Solution:**
```
SELECT 
    service,
    SUM(patients_admitted) AS total_admitted,
    SUM(patients_refused) AS total_refused,
    ROUND((SUM(patients_admitted) * 100.0 / SUM(patients_requested)), 2) AS admission_rate
FROM services_weekly
GROUP BY service
ORDER BY admission_rate DESC;
```
## 🔗 LinkedIn Post

Check out my detailed post and SQL challenge update here 👉
[Day 6 – SQL with IDC](https://www.linkedin.com/posts/mohammadrahil142_sqlwithidc-sqlchallenge-dataanalytics-activity-7393328296001851392-ETor?utm_source=social_share_send&utm_medium=member_desktop_web&rcm=ACoAADocHhYBCyW3F2jiXG5MaOb0U1lc6mDQQJI)
