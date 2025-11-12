# 📘 Day 8: String Functions in SQL

### 🧠 Topics Covered:
`UPPER`, `LOWER`, `LENGTH`, `CONCAT`, `SUBSTRING`

---

## 📖 Concept Overview
String functions help you **manipulate and format text data** directly within SQL queries — ideal for transforming names, labels, and other text-based fields.

---

## 🔧 Common String Functions

| Function | Description | Example |
|-----------|--------------|----------|
| `UPPER(column)` | Convert text to uppercase | `UPPER(name)` → **RAHIL** |
| `LOWER(column)` | Convert text to lowercase | `LOWER(service)` → **general ward** |
| `LENGTH(column)` | Get string length | `LENGTH(name)` → **5** |
| `CONCAT(str1, str2)` | Combine multiple strings | `CONCAT(first_name, ' ', last_name)` |
| `SUBSTRING(str, pos, len)` | Extract part of a string | `SUBSTRING(name, 1, 4)` → **Rahi** |
| `TRIM(column)` | Remove extra spaces | `TRIM(name)` |
| `REPLACE(str, old, new)` | Replace text | `REPLACE(service, 'old', 'new')` |

---

## 💡 Tips & Tricks

✅ **String Concatenation:**
```MySQL
CONCAT(name, ' - ', service);
```
✅ **Trim Variants:**

LTRIM() → removes spaces from the left

RTRIM() → removes spaces from the right

TRIM() → removes spaces from both sides

✅ **Case-Insensitive Comparison:**
```sql
WHERE LOWER(name) = LOWER('john smith');
```
✅ **Performance Note:**
Avoid using string functions inside WHERE clauses as they prevent index usage and may slow queries.

✅ **Combine with CASE for complex logic:**
```sql
SELECT
    name,
    CASE
        WHEN LENGTH(name) > 20 THEN CONCAT(SUBSTRING(name, 1, 20), '...')
        ELSE name
    END AS display_name
FROM patients;
```
---
## 🧩 Practice Questions

1️⃣ Convert all patient names to uppercase

2️⃣ Find the length of each staff member’s name

3️⃣ Concatenate staff_id and staff_name with a hyphen separator

---
## 🏆 Daily Challenge
Create a patient summary that shows patient_id, full name in uppercase, service in lowercase, age category (if age >= 65 then 'Senior', if age >= 18 then 'Adult', else 'Minor'), and name length. Only show patients whose name length is greater than 10 characters.

✅**Solution**
```sql
SELECT 
    patient_id,
    UPPER(name) AS full_name,
    LOWER(service) AS service_availed,
    CASE 
        WHEN age >= 65 THEN 'Senior'
        WHEN age >= 18 THEN 'Adult'
        ELSE 'Minor'
    END AS age_category,
    CHAR_LENGTH(name) AS name_length
FROM patients
WHERE CHAR_LENGTH(name) > 10;
```
## 🔗 LinkedIn Post

**Check out my detailed post and SQL challenge update here 👉**
[Day 8 – SQL Challenge](https://www.linkedin.com/posts/mohammadrahil142_sqlwithidc-21dayssqlchallenge-sql-activity-7394259751070576641-AWIa?utm_source=social_share_send&utm_medium=member_desktop_web&rcm=ACoAADocHhYBCyW3F2jiXG5MaOb0U1lc6mDQQJI)
