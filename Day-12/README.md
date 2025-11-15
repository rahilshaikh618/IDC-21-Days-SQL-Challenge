# Day 11 – NULL Values and IS NULL / IS NOT NULL

## Topics Covered

**Topics:** NULL handling, IS NULL, IS NOT NULL, COALESCE

### Key Cincept - Understanding NULL in SQL

NULL represents missing or unknown data.

**It is not:**

1. Zero

2. An empty string

3. A default value

4. It simply means the value is absent.

**NULL Handling Examples**
```
-- Find records with NULL events
SELECT * 
FROM services_weekly 
WHERE event IS NULL;

-- Find records with non-NULL events
SELECT * 
FROM services_weekly 
WHERE event IS NOT NULL;

-- Replace NULL with a default value
SELECT
    service,
    week,
    COALESCE(event, 'No Event') AS event_status
FROM services_weekly;

-- Count NULL values
SELECT
    COUNT(*) AS total_rows,
    COUNT(event) AS non_null_events,
    COUNT(*) - COUNT(event) AS null_events
FROM services_weekly;

-- Filter excluding empty strings and NULLs
SELECT * 
FROM services_weekly
WHERE event IS NOT NULL 
  AND event != '';
```
---
## Tips & Tricks
```
-- Never use '=' or '!=' with NULL

-- Wrong:
WHERE event = NULL;
WHERE event != NULL;

-- Correct:
WHERE event IS NULL;
WHERE event IS NOT NULL;
```
```
-- NULL in arithmetic results in NULL
5 + NULL = NULL
NULL * 10 = NULL
```
```
-- COALESCE returns the first non-NULL value
COALESCE(column1, column2, 'default');
```
```
-- COUNT(*) includes NULLs,
COUNT(column) excludes NULLs
```
```
-- Handle NULL in ORDER BY (push NULLs last)
ORDER BY COALESCE(event, 'ZZZZ');

Note: Empty string '' is NOT NULL. Always check for both when necessary.
```
---

## Practice Questions

1. Find all weeks in services_weekly where no special event occurred.
2. Count how many records have null or empty event values.
3. List all services that had at least one week with a special event.
Find all weeks in services_weekly where no special event occurred.

---
## Daily Challenge:

**Question:** Analyze the event impact by comparing weeks with events vs weeks without events. Show: event status ('With Event' or 'No Event'), count of weeks, average patient satisfaction, and average staff morale. Order by average patient satisfaction descending.

Count how many records have NULL or empty event values.
### ✅ Solution:
```
SELECT
  CASE
    WHEN event IS NOT NULL AND event <> 'none' AND event <> '' THEN 'With Event'
    ELSE 'No Event'
  END AS event_status,
  COUNT(DISTINCT week) AS weeks_count,
  ROUND(AVG(patient_satisfaction), 2) AS avg_patient_satisfaction,
  ROUND(AVG(staff_morale), 2) AS avg_staff_morale
FROM services_weekly
GROUP BY event_status
ORDER BY avg_patient_satisfaction DESC;
```
## 🔗 LinkedIn Post
Check out my LinkedIn post here 👉  
[Day 1 – SQL Challenge]()
