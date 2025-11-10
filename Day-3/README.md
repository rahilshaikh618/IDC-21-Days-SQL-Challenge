# 🧠 Day 3 – Sorting Data with ORDER BY

---

## 📘 Topics Covered
**Topics:** `ORDER BY`, `ASC/DESC`, multiple column sorting  

The `ORDER BY` clause allows you to sort query results based on one or more columns.  
Sorting helps you organize your data in a meaningful order — such as highest score, alphabetical order, or chronological order.

---

## 📚 Reading & Resources
### **Basic Syntax:**
```sql
SELECT column1, column2
FROM table_name
ORDER BY column1 [ASC|DESC];
 ```
### **Key Points:**
ASC → Ascending order (default) – A → Z, 0 → 9, oldest → newest

DESC → Descending order – Z → A, 9 → 0, newest → oldest

You can sort by multiple columns (e.g., first by department, then by age)

NULL values usually appear first with ASC and last with DESC

---
## 🧩 Practice Questions
1. List all patients sorted by age in descending order.
2. Show all services_weekly data sorted by week number ascending and patients_request descending.
3. Display staff members sorted alphabetically by their names.
---
## 🚀 Daily Challenge

**Question:**
Retrieve the top 5 weeks with the highest patient refusals across all services, showing week_number, service, patients_refused, and patients_requested.
Sort the results by patients_refused in descending order.

**✅ Solution:**
```
SELECT week_number, service, patients_refused, patients_requested
FROM services_weekly
ORDER BY patients_refused DESC
LIMIT 5;
```
## 🔗 LinkedIn Post

Check out my detailed post and SQL journey update here 👉
[Day 3 – SQL with IDC](https://www.linkedin.com/posts/mohammadrahil142_idcwithsql-sqlchallenge-learnsql-activity-7392520114690121729-72n0?utm_source=social_share_send&utm_medium=member_desktop_web&rcm=ACoAADocHhYBCyW3F2jiXG5MaOb0U1lc6mDQQJI)
