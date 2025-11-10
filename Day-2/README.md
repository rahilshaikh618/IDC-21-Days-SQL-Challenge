# 🧠 Day 2 – Filtering Data with WHERE Clause

## 📅 Date
**Day 2 (04/11):** Filtering Data with WHERE Clause

---

## 📘 Topics Covered ##
**Topics:** `WHERE` clause, comparison operators, basic filtering  
---
## 📚 Reading & Resources ##

The `WHERE` clause filters records based on conditions, returning only rows that meet your criteria.  
It’s one of the most important SQL clauses for extracting meaningful insights from data.


Operators:

Comparison: =, !=, <>, >, <, >=, <=
Logical: AND, OR, NOT
Pattern Matching: LIKE, IN, BETWEEN

### **Basic Syntax:**
```sql
SELECT column1, column2, ...
FROM table_name
WHERE condition;
```
---
## 🧩 Practice Questions

1. Find all patients who are older than 60 years.
2. Retrieve all staff members who work in the 'Emergency' service.
3. List all weeks where more than 100 patients requested admission in any service.
---
## 🚀 Daily Challenge

Question:
Find all patients admitted to the 'Surgery' service with a satisfaction score below 70, showing their patient_id, name, age, and satisfaction_score.

✅ Solution:
```
SELECT patient_id, name, age, satisfaction_score
FROM patients
WHERE service = 'Surgery'
  AND satisfaction_score < 70;
```
---
## 🔗 LinkedIn Post

**Check out my detailed post and daily progress here 👉**
[Day 2 – SQL Challenge](https://www.linkedin.com/posts/mohammadrahil142_21dayssqlchallenge-21dayssqlchallenge-sqlwithidc-activity-7392495028599844864-vutS?utm_source=social_share_send&utm_medium=member_desktop_web&rcm=ACoAADocHhYBCyW3F2jiXG5MaOb0U1lc6mDQQJI)

