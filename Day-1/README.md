# 🧠 Day 1 – Introduction to SQL & SELECT Statement

## 📘 Topics Covered
**Topics:** Basic `SELECT`, column selection, viewing data structure  

SQL (Structured Query Language) is the standard language for managing relational databases.  
The `SELECT` statement is your primary tool for retrieving data.

### 🔑 Key Concepts
- Tables store data in rows (records) and columns (fields)  
- `SELECT` defines which columns to retrieve  
- `FROM` specifies which table to query  
- Use a semicolon (`;`) to end SQL statements  

---

## 🧩 Practice Questions

1. Retrieve all columns from the `patients` table.  
2. Select only the `patient_id`, `name`, and `age` columns from the `patients` table.  
3. Display the first 10 records from the `services_weekly` table.  

---

## 🚀 Daily Challenge

**Question:** List all unique hospital services available in the hospital.  

### ✅ Solution:

```sql
SELECT DISTINCT service
FROM patients;
