# 🧠 21 Days SQL Challenge – Indian Data Club (Full Curriculum)

Welcome to the **21 Days SQL Challenge** repository — a structured, hands-on journey through SQL fundamentals to advanced analytics, designed for developers, analysts, and learners who want practical experience using real-world datasets.

> **How to use this repo**
>
> * Each day contains reading material, tips, practice questions, and a daily challenge.
> * Use the `services_weekly`, `patients`, `staff`, and `staff_schedule` tables (or equivalent) for practice.
> * For doubts, join the Challenges Doubt Discord: [https://discord.gg/6gUG8KfPgx](https://discord.gg/6gUG8KfPgx)

---

## 📚 Quick Links

* Submission form: [https://forms.office.com/r/CsF3zaz0jL](https://forms.office.com/r/CsF3zaz0jL)
* Discord (Doubt channel): [https://discord.gg/6gUG8KfPgx](https://discord.gg/6gUG8KfPgx)

---

## **Days 1-4**: SQL Fundamentals (SELECT, WHERE, ORDER BY, LIMIT)

### Day 1 (03/11): Introduction to SQL & SELECT

**Topics:** Basic SELECT, column selection, viewing data structure

**Practice:**

1. Retrieve all columns from `patients`.
2. Select `patient_id, name, age` from `patients`.
3. Display first 10 records from `services_weekly`.

**Daily Challenge:**

* List all unique hospital services available in the hospital.

---

### Day 2 (04/11): WHERE Clause

**Topics:** WHERE, comparison, logical operators, IN, BETWEEN, NULL checks

**Practice:**

1. Patients older than 60.
2. Staff in 'Emergency' service.
3. Weeks with >100 patient requests.

**Daily Challenge:**

* Patients admitted to 'Surgery' with satisfaction < 70 (show id, name, age, satisfaction).

---

### Day 3 (05/11): ORDER BY

**Topics:** ORDER BY, ASC/DESC, multi-column sorting

**Practice:**

1. Patients sorted by age DESC.
2. `services_weekly` sorted by week asc and patients_request desc.
3. Staff sorted by name.

**Daily Challenge:**

* Top 5 weeks with highest patient refusals (show week, service, patients_refused, patients_request).

---

### Day 4 (06/11): LIMIT & OFFSET

**Topics:** LIMIT, OFFSET, pagination

**Practice:**

1. First 5 patients.
2. Patients 11–20 using OFFSET.
3. 10 most recent admissions (by arrival_date).

**Daily Challenge:**

* 3rd to 7th highest patient satisfaction scores (show patient_id, name, service, satisfaction).

---

## **Days 5-7**: Aggregation & Grouping (COUNT, SUM, AVG, GROUP BY, HAVING)

### Day 5 (07/11): Aggregate Functions

**Topics:** COUNT, SUM, AVG, MIN, MAX

**Practice:**

1. Total patients.
2. Average satisfaction.
3. Min & max age.

**Daily Challenge:**

* Total admitted, total refused, average patient satisfaction across services & weeks (round avg to 2 decimals).

---

### Day 6 (09/11): GROUP BY

**Topics:** GROUP BY, aggregations per category

**Practice:**

1. Count patients by service.
2. Average age by service.
3. Staff count by role.

**Daily Challenge:**

* For each service: total patients admitted, total refused, admission rate (%) — order by admission rate DESC.

---

### Day 7 (10/11): HAVING

**Topics:** HAVING to filter aggregated groups

**Practice:**

1. Services with total admitted > 500.
2. Services where avg satisfaction < 75.
3. Weeks where total staff presence < 50.

**Daily Challenge:**

* Services that refused > 100 patients total AND avg satisfaction < 80. Show service name, total_refused, avg_satisfaction.

---

## **Days 8-9**: Data Manipulation (String & Date Functions)

### Day 8 (11/11): String Functions

**Topics:** UPPER, LOWER, LENGTH, CONCAT, SUBSTRING, TRIM, REPLACE

**Daily Challenge:**

* Patient summary with uppercase full name, lowercase service, age category, name length; filter name_length > 10.

---

### Day 9 (12/11): Date Functions

**Topics:** DATE functions, date arithmetic, EXTRACT

**Daily Challenge:**

* Average length of stay per service; show only services where avg stay > 7 days. Include patient count and order by avg stay desc.

---

## **Days 10-12**: Conditional Logic (CASE, DISTINCT, NULL Handling)

### Day 10 (13/11): CASE Statements

**Daily Challenge:**

* Service performance report with performance category based on avg satisfaction thresholds.

---

### Day 11 (14/11): DISTINCT & duplicates

**Daily Challenge:**

* Unique combinations of service and event_type (non-null), with counts ordered by count desc.

---

### Day 12 (15/11): NULL handling

**Daily Challenge:**

* Compare weeks with events vs without events: show status, count of weeks, avg patient satisfaction, avg staff morale; order by avg patient satisfaction desc.

---

## **Days 13-15**: Combining Tables (JOINs)

### Day 13 (17/11): INNER JOIN

**Daily Challenge:**

* Patient report with total staff in their service; include only patients from services with >5 staff. Order by staff_count desc, patient name.

---

### Day 14 (18/11): LEFT/RIGHT JOIN

**Daily Challenge:**

* Staff utilization report showing staff and count of weeks present (include staff with no schedule). Order by weeks_present desc.

---

### Day 15 (19/11): Multiple Joins

**Daily Challenge:**

* Week 20 service analysis: service, admitted, refused, avg satisfaction, staff assigned, staff present that week. Order by patients_admitted desc.

---

## Mini Project (20/11): The Great Pizza (SQL Mini Project)

* Apply SQL concepts to analyse pizza sales, customer behaviour, and performance metrics. Submit via the form.

---

## **Days 16-18**: Advanced Queries (Subqueries, UNION)

### Day 16 (21/11): Subqueries (WHERE)

**Daily Challenge:**

* Find patients admitted to services that had at least one week with refusals AND the service avg satisfaction < overall hospital avg.

---

### Day 17 (22/11): Subqueries (SELECT/FROM)

**Daily Challenge:**

* Service report showing total admitted, difference from avg admissions, and rank indicator (Above/Average/Below). Order by total admitted desc.

---

### Day 18 (23/11): UNION / UNION ALL

**Daily Challenge:**

* Personnel & patient list for 'surgery' or 'emergency' services with id, full name, type, and service.

---

## **Days 19-20**: Analytical (Window) Functions

### Day 19 (25/11): ROW_NUMBER(), RANK(), DENSE_RANK()

**Daily Challenge:**

* For each service, rank weeks by patient satisfaction (top 3 weeks per service).

---

### Day 20 (26/11): Aggregate Window Functions

**Daily Challenge:**

* Trend analysis for weeks 10–20: patients_admitted, cumulative admissions, 3-week moving avg satisfaction, and diff from service avg.

---

## Day 21 (27/11): CTEs (WITH clause)

**Daily Challenge:**

* Build a comprehensive hospital performance dashboard using CTEs: service metrics, staff metrics, patient demographics, and an overall performance score. Order by performance score desc.

---

## Capstone Project

* A mystery investigation using multiple datasets (keycard logs, phone records, evidence). Use full SQL skillset to identify the culprit and submit queries and final "Case Solved" output.

---

## 🎯 Learning Outcomes

* Strong SQL fundamentals and advanced query skills
* Ability to explore, clean, aggregate, join, and analyze real datasets
* Practical experience suitable for portfolios and interviews

---

## 🙏 Acknowledgements

Thanks to **Indian Data Club (IDC)** and **DPDzero** for organizing the challenge.

---

## 🔗 Connect

* LinkedIn: [https://www.linkedin.com/in/rahilshaikh618](www.linkedin.com/in/mohammadrahil142)
* GitHub: [https://github.com/rahilshaikh618](https://github.com/rahilshaikh618)

---

*If you want this README exported as `README.md` file within the repo or need a shorter version for GitHub summary, tell me and I will add it.*
