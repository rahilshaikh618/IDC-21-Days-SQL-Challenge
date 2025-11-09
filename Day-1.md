# 🧠 Day 1 – SQL Fundamentals: SELECT Statement

## 📘 Topics Covered
- Introduction to SQL  
- Basic `SELECT` statements  
- Retrieving specific columns  
- Viewing data structure  
- Using `LIMIT` to control output  

---

## 🧩 Practice Questions
1. Retrieve all columns from the `patients` table  
2. Select only `patient_id`, `name`, and `age` columns from the `patients` table  
3. Display the first 10 records from the `services_weekly` table  

---

## 💡 Key Learnings
- `SELECT` is used to extract data from a table  
- Always specify only the columns you need (avoid `SELECT *` in production)  
- Use aliases (`AS`) for readability  
- SQL keywords are case-insensitive but written in uppercase for clarity  

---

## 🚀 Daily Challenge
**Task:** List all unique hospital services available in the hospital.  

```sql
SELECT DISTINCT service
FROM patients;
