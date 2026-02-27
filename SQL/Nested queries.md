# 📘 SQL Subqueries (Nested Queries) – Complete Guide

![SQL](https://img.shields.io/badge/Language-SQL-blue?style=for-the-badge&logo=mysql)
![Level](https://img.shields.io/badge/Topic-Subqueries-green?style=for-the-badge)

> A complete practical guide to mastering SQL Subqueries with real-world examples.

---

# 📌 What is a Subquery?

A **Subquery** (Nested Query) is a query written inside another SQL query.

It executes first, and its result is used by the outer query.

Subqueries are commonly used inside:

- WHERE
- SELECT
- FROM
- HAVING

---

# 🧠 Execution Flow

Example:

SELECT * 
FROM customers
WHERE salary > (SELECT AVG(salary) FROM customers);

Execution Order:

1️⃣ Execute inner query  
2️⃣ Get result (average salary)  
3️⃣ Outer query compares each row  
4️⃣ Return filtered result  

---

# 📂 Example 1: Salary Greater Than Average

```sql
SELECT *
FROM customers
WHERE salary > (
    SELECT AVG(salary)
    FROM customers
);
```

---

# 📂 Example 2: Salary Greater Than Specific Person

```sql
SELECT *
FROM customers
WHERE salary > (
    SELECT salary
    FROM customers
    WHERE name = 'Mr. X'
);
```

---

# 📂 Example 3: 2nd Highest Salary

```sql
SELECT MAX(salary)
FROM customers
WHERE salary < (
    SELECT MAX(salary)
    FROM customers
);
```

---

# 🔄 Types of Subqueries

## 1️⃣ Single Row Subquery
Returns one value.

## 2️⃣ Multiple Row Subquery
Returns multiple values (use IN, ANY, ALL).

## 3️⃣ Correlated Subquery
Depends on outer query row.

Example:

```sql
SELECT c1.name, c1.salary
FROM customers c1
WHERE salary > (
    SELECT AVG(c2.salary)
    FROM customers c2
    WHERE c2.department = c1.department
);
```

---

# 🧬 Logical Diagram

Outer Query
   ↓
Subquery Executes
   ↓
Returns Value(s)
   ↓
Outer Query Uses Result
   ↓
Final Output

---

