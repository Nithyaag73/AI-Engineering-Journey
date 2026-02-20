# 📘 Complete SQL Cheat Sheet for Data Science

> A comprehensive SQL reference covering fundamentals, commands, constraints, primary keys, and foreign keys.  
> Perfect for Data Science, Analytics, Backend Development, and Database Management.

---

# 📌 What is SQL?

**SQL (Structured Query Language)** is a domain-specific language used to manage and manipulate relational databases.

- ANSI Standard: 1986  
- ISO Standard: 1987  
- Used in: MySQL, PostgreSQL, SQL Server, Oracle  
- Common in: Jupyter Notebook, Power BI, Tableau  

SQL works with **tables (rows & columns)** inside relational databases.

---

# 🚀 Why SQL is Important for Data Science

- Query large datasets efficiently
- Filter and clean data
- Aggregate and summarize information
- Join multiple tables
- Prepare datasets for ML models
- Connect to BI tools

---

# 🏗 How SQL Works

When a SQL query runs:

1. Parsing – Checks syntax
2. Optimization – Chooses best execution plan
3. Execution – Runs the query
4. Output – Returns results

### Core Components

| Component | Description |
|------------|-------------|
| Database | Collection of structured data |
| Table | Organized storage (rows & columns) |
| Index | Speeds up searches |
| Constraints | Enforce rules and data integrity |

---

# 📂 SQL Command Categories

| Category | Purpose | Examples |
|----------|----------|----------|
| DDL | Define structure | CREATE, ALTER, DROP |
| DML | Modify data | INSERT, UPDATE, DELETE |
| DQL | Retrieve data | SELECT |
| DCL | Manage permissions | GRANT, REVOKE |

---

# 🛠 Basic SQL Commands

## 1️⃣ Create Table

```sql
CREATE TABLE employees (
    id INT PRIMARY KEY,
    name VARCHAR(50),
    salary DECIMAL(10,2)
);
```

---

## 2️⃣ Insert Data

```sql
INSERT INTO employees VALUES (1, 'Alice', 50000);
```

---

## 3️⃣ Retrieve Data

```sql
SELECT * FROM employees;
```

Select specific columns:

```sql
SELECT name, salary FROM employees;
```

---

## 4️⃣ Filter Data

```sql
SELECT * FROM employees
WHERE salary > 40000;
```

---

## 5️⃣ Update Data

```sql
UPDATE employees
SET salary = 55000
WHERE id = 1;
```

---

## 6️⃣ Delete Data

```sql
DELETE FROM employees
WHERE id = 1;
```

---

# 🔗 Joins

```sql
SELECT e.name, d.department_name
FROM employees e
JOIN departments d
ON e.department_id = d.id;
```

Types of joins:
- INNER JOIN
- LEFT JOIN
- RIGHT JOIN
- FULL JOIN

---

# 📊 Aggregation Functions

| Function | Purpose |
|----------|----------|
| COUNT() | Count rows |
| SUM() | Total |
| AVG() | Average |
| MIN() | Minimum |
| MAX() | Maximum |

Example:

```sql
SELECT AVG(salary) FROM employees;
```

---

# 🧮 GROUP BY & HAVING

```sql
SELECT department_id, AVG(salary)
FROM employees
GROUP BY department_id
HAVING AVG(salary) > 50000;
```

---
