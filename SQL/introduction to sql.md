📌 What is SQL?

SQL (Structured Query Language) is a domain-specific language used to manage and manipulate relational databases.

📅 ANSI Standard: 1986

📅 ISO Standard: 1987

🗄 Used in: MySQL, PostgreSQL, SQL Server, Oracle

📊 Common in: Jupyter Notebook, Power BI, Tableau, backend systems

Unlike general-purpose languages (e.g., Python), SQL focuses exclusively on structured data stored in tables (rows & columns).

🚀 Why SQL is Important for Data Science

Query large datasets efficiently

Clean and transform raw data

Perform aggregations and summaries

Join multiple tables

Prepare datasets for ML models

Connect directly with BI tools

🏗 How SQL Works

When you run a SQL query, the database engine follows this process:

Parsing – Checks syntax correctness

Optimization – Finds the most efficient execution plan

Execution – Runs the query

Output – Returns results

🔹 Core Components
Component	Description
Database	Collection of structured data
Table	Organized storage (rows & columns)
Index	Improves search speed
Constraints	Enforce rules (PRIMARY KEY, UNIQUE, NOT NULL)
📂 SQL Command Categories
Category	Purpose	Examples
DDL (Data Definition Language)	Define database structure	CREATE, ALTER, DROP
DML (Data Manipulation Language)	Modify data	INSERT, UPDATE, DELETE
DQL (Data Query Language)	Retrieve data	SELECT
DCL (Data Control Language)	Manage permissions	GRANT, REVOKE
🛠 Basic SQL Commands
1️⃣ Create Table (DDL)
CREATE TABLE employees (
    id INT PRIMARY KEY,
    name VARCHAR(50),
    salary DECIMAL(10,2)
);
2️⃣ Insert Data (DML)
INSERT INTO employees VALUES (1, 'Alice', 50000);
3️⃣ Retrieve Data (DQL)
SELECT * FROM employees;

Select specific columns:

SELECT name, salary FROM employees;
4️⃣ Filter Data
SELECT * FROM employees
WHERE salary > 40000;
5️⃣ Update Data
UPDATE employees
SET salary = 55000
WHERE id = 1;
6️⃣ Delete Data
DELETE FROM employees
WHERE id = 1;
🔗 Joins (Combining Tables)
SELECT e.name, d.department_name
FROM employees e
JOIN departments d
ON e.department_id = d.id;

Types of Joins:

INNER JOIN

LEFT JOIN

RIGHT JOIN

FULL JOIN

📊 Aggregation Functions
Function	Purpose
COUNT()	Count rows
SUM()	Total value
AVG()	Average value
MIN()	Minimum
MAX()	Maximum

Example:

SELECT AVG(salary) FROM employees;
🧮 GROUP BY & HAVING
SELECT department_id, AVG(salary)
FROM employees
GROUP BY department_id
HAVING AVG(salary) > 50000;
🔐 Constraints
Constraint	Purpose
PRIMARY KEY	Unique identifier
FOREIGN KEY	Links tables
NOT NULL	Prevents empty values
UNIQUE	No duplicate values
CHECK	Validates condition

Example:

CREATE TABLE employees (
    id INT PRIMARY KEY,
    name VARCHAR(50) NOT NULL,
    salary DECIMAL(10,2) CHECK (salary > 0)
);
📈 Index Example
CREATE INDEX idx_salary
ON employees(salary);

Improves search performance on frequently queried columns.

🧠 SQL Best Practices

✔ Use meaningful table & column names
✔ Always use WHERE in UPDATE & DELETE
✔ Use indexes for large datasets
✔ Normalize database design
✔ Use aliases for readability
✔ Avoid SELECT * in production

🧩 SQL in Data Science Workflow

Extract data from database

Clean & filter using SQL

Aggregate & transform

Export to Python / Power BI

Visualize & model

📚 Recommended Practice Platforms

LeetCode (Database section)

HackerRank SQL

Mode Analytics SQL Tutorial

Kaggle datasets with SQL

🏁 Final Notes

SQL is a must-have skill for:

Data Analysts

Data Scientists

Backend Developers

Business Intelligence Engineers

Mastering SQL enables you to efficiently handle structured data at scale.
