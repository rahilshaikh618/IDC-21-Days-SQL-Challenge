# 🕵️‍♂️ SQL Murder Mystery: “Who Killed the CEO?”
A Data Investigation Capstone Project by Mohd Rahil

---
## 📌 Project Overview

**This capstone project is part of the 21 Days SQL Challenge by Indian Data Club (IDC) and DPDzero.
The goal of the challenge was to solve a fictional corporate murder mystery using SQL as the only tool.

A CEO is found dead at 9:00 PM on 15th October 2025 in their office.
As a Data Analyst Detective, your mission is to analyze multiple datasets to determine:**

Who committed the murder?

When and where did it actually happen?

What evidence supports the conclusion?

This project demonstrates analytical reasoning, multi-table SQL operations, time-based filtering, and storytelling through data.

---
## 🗂️ Datasets Used

The project uses five tables, all created through the provided SQL_Murder_Mystery.sql file:

**1. employees**

| Column       | Type     | Description               |
|--------------|----------|---------------------------|
| employee_id  | INT      | Unique employee ID        |
| name         | VARCHAR  | Full name of the employee |
| department   | VARCHAR  | Department name           |
| role         | VARCHAR  | Job position / title      |


**2. keycard_logs**

| Column      | Type      | Description                        |
|-------------|-----------|------------------------------------|
| log_id      | INT       | Keycard log entry ID               |
| employee_id | INT       | Employee who accessed the room     |
| room        | VARCHAR   | Room name                          |
| entry_time  | TIMESTAMP | Time at which the employee entered |
| exit_time   | TIMESTAMP | Time at which the employee exited  |


**3. calls**

| Column       | Type      | Description                         |
|--------------|-----------|-------------------------------------|
| call_id      | INT       | Unique call ID                      |
| caller_id    | INT       | Employee who initiated the call     |
| receiver_id  | INT       | Employee receiving the call         |
| call_time    | TIMESTAMP | When the call occurred              |
| duration_sec | INT       | Duration of the call (seconds)      |


**4. alibis**

| Column           | Type      | Description                             |
|------------------|-----------|-----------------------------------------|
| alibi_id         | INT       | Alibi record ID                         |
| employee_id      | INT       | Employee providing the alibi            |
| claimed_location | VARCHAR   | Where the employee claims they were     |
| claim_time       | TIMESTAMP | When the employee states they were there |


**5. evidence**

| Column       | Type      | Description                            |
|--------------|-----------|-----------------------------------------|
| evidence_id  | INT       | Unique evidence ID                      |
| room         | VARCHAR   | Room where evidence was found           |
| description  | VARCHAR   | Description of the evidence recovered   |
| found_time   | TIMESTAMP | Timestamp when the evidence was discovered |

---
## 🧠 Objective

**Using only SQL, the goal of this project was to uncover the murderer by:**

🔍 Identifying the crime location and time

🚪 Analyzing movement patterns using keycard logs

🤥 Matching or contradicting alibis

📞 Investigating suspicious phone calls

🧤 Mapping evidence to employee presence

🧩 Combining all findings into a final “Case Solved” output

### ⭐ Step-by-Step Investigation Process

**1️⃣ Confirm the Crime Location & Time (Evidence Table)**

Using the evidence table, the crime was pinned down to:

Room: CEO Office

Time: Around 9:00 PM


**2️⃣ Identify Who Was Near the CEO Office**

Queried keycard_logs to find all employees who entered the CEO Office between 20:50–21:00, forming the initial suspect list.


**3️⃣ Cross-Check Alibis**

Compared:

claimed_location from alibis
vs.

actual room from keycard_logs

to expose false alibis.


**4️⃣ Analyze Suspicious Phone Calls**

Filtered calls made within 10 minutes before the murder, identifying unusual communication patterns.


**5️⃣ Link Evidence to Employee Movements**

Connected physical evidence from the evidence table with employee presence using keycard_logs to see:

Who was in the room

When the evidence was found


**6️⃣ Combine All Clues Using CTEs**

Merged all investigation layers using:

🧩 JOINs

🧠 CTEs

🔗 INTERSECT

⏱️ Time filtering


to produce the final answer.

🎯 Final SQL Output
| killer      |
|-------------|
| David Kumar |


**🔎 Why David Kumar?**

David Kumar was the only employee who:

Was inside the CEO Office during the crime window

Had a false alibi

Made a suspicious phone call minutes before the incident

Matched evidence timestamps with room presence

---
## 📝 Skills Demonstrated

✔ Multi-table JOINs

✔ Subqueries & CTEs

✔ Time-window filtering (BETWEEN)

✔ Contradiction analysis

✔ Logical pattern identification

✔ Storytelling through data

✔ End-to-end SQL-based problem solving

---
## 🔗 LinkedIn Post
Check out my LinkedIn post here 👉  
[Capstone Project – 21 Days SQL Challenge](https://www.linkedin.com/posts/mohammadrahil142_sql-21dayssqlchallenge-capstoneproject-activity-7400326195059462144-eq_r?utm_source=social_share_send&utm_medium=member_desktop_web&rcm=ACoAADocHhYBCyW3F2jiXG5MaOb0U1lc6mDQQJI)

---
## 🙋‍♂️ About Me (Creator)

Name: Mohd Rahil

Role: Data Analyst | SQL Enthusiast | Problem Solver

Interested in: Data Analytics, Business Intelligence, SQL, DBMS, Data Storytelling

[LinkedIn](www.linkedin.com/in/mohammadrahil142)
