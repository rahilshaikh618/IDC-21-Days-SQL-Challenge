# 🧀 **The Great Pizza Analytics Challenge**
### _A SQL Mini-Project Using the IDC Pizza Database_

Welcome to **The Great Pizza Analytics Challenge!**  
This project simulates a real-world scenario where you work as a **Data Analyst at IDC Pizza**, exploring and analyzing sales data to extract meaningful insights using SQL.

This work is part of my **21 Days SQL Challenge**, aimed at mastering real-world SQL techniques including filtering, joins, aggregations, pattern matching, and sales analytics.

---

## 📂 **Project Overview**
This project focuses on practical SQL capabilities used in industry:

🔹 Database inspection & schema understanding  
🔹 Data cleaning & NULL handling  
🔹 Filtering, pattern matching, and logical operators  
🔹 Joins (INNER, LEFT, RIGHT, SELF)  
🔹 Aggregation (SUM, COUNT, AVG)  
🔹 Grouping & HAVING filters  
🔹 Time-based queries  
🔹 Sales performance insights  

---

## 🗃️ **Dataset Structure**
The IDC Pizza database consists of **four relational tables** that together depict a complete sales ecosystem:

### **1️⃣ `pizza_types`**  
Contains pizza metadata:  
- `pizza_type_id`  
- `name`  
- `category`  
- `ingredients`  

### **2️⃣ `pizzas`**  
Contains size and pricing details:  
- `pizza_id`  
- `pizza_type_id`  
- `size`  
- `price`  

### **3️⃣ `orders`**  
Contains order timestamps:  
- `order_id`  
- `date`  
- `time`  

### **4️⃣ `order_details`**  
Contains detailed order item information:  
- `order_details_id`  
- `order_id`  
- `pizza_id`  
- `quantity`  

---

## 🎯 **Ad Hoc Requests (Questions Solved)**

### 🟦 **PHASE 1 — Foundation & Inspection (4 Queries)**
1️⃣ List all unique pizza categories (`DISTINCT`)  
2️⃣ Display pizza_type_id, name, and ingredients with NULLs replaced  
3️⃣ Identify pizzas with missing prices (`IS NULL`)  
4️⃣ Retrieve orders placed on `'2015-01-01'`  

---

### 🟧 **PHASE 2 — Filtering & Exploration (6 Queries)**
5️⃣ List pizzas sorted by price (descending)  
6️⃣ Retrieve pizzas available in size `'L'` or `'XL'`  
7️⃣ Find pizzas priced between `$15.00–$17.00`  
8️⃣ Fetch pizzas containing `"Chicken"` in their name  
9️⃣ Get orders placed on `'2015-02-15'` or after **8 PM**  
🔟 Calculate the total quantity of pizzas sold (`SUM`)  

---

### 🟩 **PHASE 3 — Sales Performance & Insights (7 Queries)**
1️⃣1️⃣ Compute average pizza price (`AVG`)  
1️⃣2️⃣ Determine total revenue per order (JOIN + SUM + GROUP BY)  
1️⃣3️⃣ Quantity sold per pizza category  
1️⃣4️⃣ Categories selling more than **5000** units (`HAVING`)  
1️⃣5️⃣ Identify pizzas never ordered (LEFT/RIGHT JOIN)  
1️⃣6️⃣ Analyze price differences between pizza sizes (SELF JOIN)  
1️⃣7️⃣ Applied logical improvements where required  

---

## ⭐ **Key Insights (Based on Attempted Queries)**

👉 **49,000+ pizzas sold** across the dataset  
👉 **Classic & Chicken** categories dominate sales & revenue  
👉 **L & XL sizes** are the most preferred  
👉 Majority of orders placed between **6 PM – 9 PM** (peak dinner time)  
👉 Some pizzas were **never ordered**, signaling low demand  
👉 Missing or NULL data required cleaning for reliability  
👉 Price variations across sizes support strong **value-based pricing**  
👉 Ingredient patterns show strong preference for **cheese & chicken pizzas**

---

## 🛠️ **Tech Stack Used**
✔ SQL (MySQL)  
✔ Aggregations & Joins  
✔ Data Cleaning & NULL Handling  
✔ Query Optimization Basics  
✔ Schema Design Understanding  
✔ Analytical Query Writing  

---

## 📁 **Project Files Included**
📄 SQL Submission File (CSV)  
📊 Project Presentation (PPTX)  
📘 Project Report (PDF)  
📑 README.md (this file)  

---

## 🙌 **Acknowledgment**
This project is part of the **#SQLWithIDC** Challenge by **Indian Data Club**, supported by **DPDzero**.  
It helped strengthen skills in SQL analytics and data-driven problem solving.

---

## 🔗 **LinkedIn Post**
Check out my LinkedIn post here:  
👉 [Mini Project – SQL Challenge](https://www.linkedin.com/posts/mohammadrahil142_the-great-pizza-analytics-challenge-activity-7397359283643908096-5Th6?utm_source=social_share_send&utm_medium=member_desktop_web&rcm=ACoAADocHhYBCyW3F2jiXG5MaOb0U1lc6mDQQJI)

---
