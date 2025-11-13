# 🧠 Day 10 – Conditional Logic (CASE Statements)

## 📘 Topics Covered
**Topics:** CASE WHEN, conditional logic, derived columns  

---
## 🔑 Key Concepts

CASE statements allow you to add conditional logic to SQL queries, similar to **if–else** statements in programming.  
They help create **custom labels, categories, and derived columns** directly within query results.

**For Example:**
```sql
CASE column_name
    WHEN value1 THEN result1
    WHEN value2 THEN result2
    ELSE default_result
END
```
**✔️ Searched CASE (More Flexible)**
```
CASE
    WHEN condition1 THEN result1
    WHEN condition2 THEN result2
    ELSE default_result
END
```
---
## 💡 Tips & Tricks

✅ Always include ELSE – prevents NULL output

✅ CASE is an expression – can be used anywhere (SELECT, ORDER BY, GROUP BY)

✅ Use CASE for custom sorting:
```
ORDER BY CASE
    WHEN service = 'Emergency' THEN 1
    WHEN service = 'ICU' THEN 2
    ELSE 3
END
```

✅ Conditional Aggregation Pattern:
```
SUM(CASE WHEN condition THEN 1 ELSE 0 END)          -- Conditional count
AVG(CASE WHEN condition THEN value ELSE NULL END)   -- Conditional average
```

✅ You can nest CASE statements, but maintain readability

✅ CASE is evaluated top-to-bottom — first match wins

---
## 🧠 Practice Questions:

1. Categorise patients as 'High', 'Medium', or 'Low' satisfaction based on their scores.
2. Label staff roles as 'Medical' or 'Support' based on role type.
3. Create age groups for patients (0-18, 19-40, 41-65, 65+).

---
## 🏆 Daily Challenge:

**Question:** Create a service performance report showing service name, total patients admitted, and a performance category based on the following: 'Excellent' if avg satisfaction >= 85, 
'Good' if >= 75, 'Fair' if >= 65, otherwise 'Needs Improvement'. Order by average satisfaction descending.

**✅ Solution:**
```
SELECT
    service,
    COUNT(*) AS total_patients_admitted,
    AVG(satisfaction) AS avg_satisfaction,
    CASE
        WHEN AVG(satisfaction) >= 85 THEN 'Excellent'
        WHEN AVG(satisfaction) >= 75 THEN 'Good'
        WHEN AVG(satisfaction) >= 65 THEN 'Fair'
        ELSE 'Needs Improvement'
    END AS performance_category
FROM patients
GROUP BY service
ORDER BY avg_satisfaction DESC;
```
## 🔗 LinkedIn Post

**Check out my detailed post and SQL challenge update here 👉**
[Day 9 – SQL Challenge](https://ww)
