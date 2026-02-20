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

# 🔐 SQL Constraints

Constraints enforce data integrity and prevent invalid data entry.

---

## Types of Constraints

| Constraint | Purpose | Example |
|------------|----------|----------|
| NOT NULL | Prevents NULL values | name VARCHAR(50) NOT NULL |
| UNIQUE | Ensures distinct values | email VARCHAR(100) UNIQUE |
| PRIMARY KEY | Unique + Not Null | id INT PRIMARY KEY |
| FOREIGN KEY | Maintains relationships | dept_id INT REFERENCES departments(id) |
| CHECK | Validates condition | age INT CHECK (age >= 18) |
| DEFAULT | Sets default value | status VARCHAR(20) DEFAULT 'active' |

---

# 🛠 Creating Table with Constraints

```sql
CREATE TABLE students (
    id INT PRIMARY KEY,
    name VARCHAR(50) NOT NULL,
    score INT CHECK (score >= 0 AND score <= 100),
    status VARCHAR(20) DEFAULT 'active'
);
```

---

# 🔄 Adding Constraint Using ALTER

```sql
ALTER TABLE students
ADD CONSTRAINT chk_score
CHECK (score >= 0);
```

---

# 🔑 PRIMARY KEY

## Definition

- Uniquely identifies each row
- Cannot be NULL
- Must be unique
- Only one per table
- Can be composite

---

## Add Primary Key During Creation

```sql
CREATE TABLE departments (
    dept_id INT PRIMARY KEY,
    dept_name VARCHAR(50)
);
```

---

## Add Primary Key to Existing Table

```sql
ALTER TABLE employees
ADD CONSTRAINT pk_emp_id
PRIMARY KEY (emp_id);
```

---

# 🔗 FOREIGN KEY

## Definition

- Links one table to another
- References a Primary Key
- Prevents orphan records
- Maintains referential integrity

---

## Add Foreign Key During Creation

```sql
CREATE TABLE employees (
    emp_id INT PRIMARY KEY,
    name VARCHAR(50),
    dept_id INT,
    FOREIGN KEY (dept_id)
    REFERENCES departments(dept_id)
);
```

---

## Add Foreign Key to Existing Table

```sql
ALTER TABLE employees
ADD CONSTRAINT fk_dept_id
FOREIGN KEY (dept_id)
REFERENCES departments(dept_id);
```

---

# 🔄 Complete Workflow Example

```sql
-- Step 1: Create parent table
CREATE TABLE departments (
    dept_id INT PRIMARY KEY,
    name VARCHAR(50)
);

-- Step 2: Insert values
INSERT INTO departments VALUES (1, 'IT'), (2, 'HR');

-- Step 3: Create child table
CREATE TABLE employees (
    emp_id INT PRIMARY KEY,
    name VARCHAR(50),
    dept_id INT REFERENCES departments(dept_id)
);
```

---

# 📈 Index Example

```sql
CREATE INDEX idx_salary
ON employees(salary);
```

---

# ⚠ Common Mistakes

- Adding foreign key before parent table exists
- Inserting child record without parent
- Forgetting WHERE clause in UPDATE or DELETE
- Adding primary key on column with duplicates

---

# 🏁 Best Practices

✔ Always define Primary Keys  
✔ Use Foreign Keys in relational datasets  
✔ Add CHECK constraints for validation  
✔ Use DEFAULT values where appropriate  
✔ Avoid SELECT * in production  
✔ Name constraints clearly (pk_, fk_, chk_)

---

# 🎯 SQL in Data Science Workflow

1. Extract data
2. Clean & filter
3. Aggregate & transform
4. Export to Python / BI tools
5. Visualize & model

---
