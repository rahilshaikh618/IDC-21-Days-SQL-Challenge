# Day 11 – DISTINCT and Handling Duplicates (SQL)

## Overview

Using DISTINCT to remove duplicate rows and extract unique values from datasets. Helps in data cleaning, reporting, and identifying unique combinations.

**Syntax**
```
SELECT DISTINCT column1, column2
FROM table_name;
```
---
## 🔑 Key Concepts

DISTINCT compares all selected columns together.

Returns unique combinations, not unique individual columns.

Can have performance impact on large datasets.

---
## Tips and Best Practices

```
-- DISTINCT vs GROUP BY (similar for simple queries)
SELECT DISTINCT service FROM patients;
SELECT service FROM patients GROUP BY service;
-- Use GROUP BY when applying aggregates

-- DISTINCT applies to entire row
SELECT DISTINCT service, name FROM patients;

-- Count unique values
SELECT COUNT(DISTINCT service) FROM patients;

-- DISTINCT treats NULL values as equal (only one NULL returned)
```

### Additional Notes:

DISTINCT can be expensive; avoid overuse.

Remove duplicates early for cleaner downstream processing.

---
### Practice Questions:

1. List all unique services in the patients table.
2. Find all unique staff roles in the hospital.
3. Get distinct months from the services_weekly table.

---
## Daily Challenge:

**Question:** Find all unique combinations of service and event type from the services_weekly table where events are not null or none, along with the count of occurrences for each combination. Order by count descending.

**✅ Solution:**
```
select service, event, count(*) as occurence
 from services_weekly
 where event is not null
 and event <> 'none'
 group by service, event
 order by occurence desc;
```
---
## 🔗 LinkedIn Post
Check out my LinkedIn post here 👉  
[Day 11 – SQL Challenge](https://www.linkedin.com/posts/mohammadrahil142_sql-learningjourney-sqlchallenge-activity-7395172472045723648-qkFL?utm_source=social_share_send&utm_medium=member_desktop_web&rcm=ACoAADocHhYBCyW3F2jiXG5MaOb0U1lc6mDQQJI)
