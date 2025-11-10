# 🧠 Day 7 – HAVING Clause

Filtering Aggregated Results Using HAVING Clause

---

## 📘 Topics Covered
**Topics:** `HAVING` clause, filtering aggregated results  

The `HAVING` clause is used to filter the results of groups created by `GROUP BY`.  
While the `WHERE` clause filters individual rows **before grouping**, `HAVING` filters **after aggregation** — making it ideal for conditions involving aggregate functions such as `SUM()`, `AVG()`, `COUNT()`, etc.

---

## 📚 Reading & Resources

### **Basic Syntax:**
```sql
SELECT column1, aggregate_function(column2)
FROM table_name
GROUP BY column1
HAVING aggregate_condition;
```
### 💡 **Tips & Tricks**

✅ Execution Order: WHERE → GROUP BY → HAVING → ORDER BY
✅ Use WHERE for row filtering, HAVING for group filtering
✅ HAVING requires GROUP BY (in most databases)
✅ You can reference column aliases in HAVING (depends on SQL engine)
---
## 🧩 Practice Questions
1. Find services that have admitted more than 500 patients in total.
2. Show services where average patient satisfaction is below 75.
3. List weeks where total staff presence across all services was less than 50.

---
## 🚀 Daily Challenge

**Question:**
Identify services that refused more than 100 patients in total and had an average patient satisfaction below 80.
Show service name, total refused, and average satisfaction.

**✅ Solution:**
```
SELECT 
    service,
    SUM(patients_refused) AS total_patients_refused,
    AVG(patient_satisfaction) AS average_patient_satisfaction
FROM 
    services_weekly
GROUP BY 
    service
HAVING 
    SUM(patients_refused) > 100 
    AND AVG(patient_satisfaction) < 80
ORDER BY 
    total_patients_refused DESC;
```
## 🔗 LinkedIn Post

**Check out my detailed post and SQL challenge update here 👉**
[Day 7 – SQL Challenge]([httpe](https://www.linkedin.com/posts/mohammadrahil142_idcwithsql-dpdzero-indiandataclub-activity-7393650653862141952-Y-GQ?utm_source=social_share_send&utm_medium=member_desktop_web&rcm=ACoAADocHhYBCyW3F2jiXG5MaOb0U1lc6mDQQJI))
