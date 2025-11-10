# 🧠 Day 4 – LIMIT and OFFSET

 LIMIT, OFFSET, and Pagination Concepts

---

## 📘 Topics Covered
**Topics:** `LIMIT`, `OFFSET`, pagination concepts  

The `LIMIT` clause restricts the number of rows returned in a result set.  
`OFFSET` is used to skip a specific number of rows before starting to return results.  
Together, they help in implementing pagination — breaking large results into smaller, manageable chunks.

---

## 📚 Reading & Resources

LIMIT restricts the number of rows returned. OFFSET skips a specified number of rows before returning results.

### **Basic Syntax:**
**To limit the output to specific no of rows.**
```sql
SELECT column1, column2
FROM table_name
LIMIT number_of_rows;
```

**To skip a specific number of rows before returning results**
```sql
SELECT column1, column2
FROM table_name
LIMIT number_of_rows OFFSET skip_rows;
```
**Key Points:**

LIMIT controls how many rows are displayed.
OFFSET determines where the display should begin.

**Pagination Example:**

Page 1 → LIMIT 10 OFFSET 0

Page 2 → LIMIT 10 OFFSET 10

Page 3 → LIMIT 10 OFFSET 20

Useful for large datasets where showing all records at once isn’t practical.

---

## 🧩 Practice Questions
1. Display the first 5 patients from the patients table.
2. Show patients 11-20 using OFFSET.
3. Get the 10 most recent patient admissions based on arrival_date.

---
## 🚀 Daily Challenge

**Question:**
Find the 3rd to 7th highest patient satisfaction scores from the patients table, showing patient_id, name, service, and satisfaction. Display only these 5 records.

**✅ Solution:**
```sql
SELECT patient_id, name, service, satisfaction
FROM patients
ORDER BY satisfaction DESC
LIMIT 5 OFFSET 2;
```
---
## 🔗 LinkedIn Post

**Check out my detailed post and SQL challenge update here 👉**
[Day 4 – SQL Challenge](https://www.linkedin.com/posts/mohammadrahil142_idcwithsql-learnsql-sqlpractice-activity-7392629188492554240-rv6Q?utm_source=social_share_send&utm_medium=member_desktop_web&rcm=ACoAADocHhYBCyW3F2jiXG5MaOb0U1lc6mDQQJI)
