🔐 SQL Constraints Cheat Sheet

Enforcing data integrity directly inside relational databases.
Essential for reliable analytics, reporting, and data science workflows.

📌 What Are SQL Constraints?

SQL constraints are rules applied to table columns to ensure data accuracy, consistency, and integrity during INSERT, UPDATE, and DELETE operations.

They prevent:

❌ Duplicate records

❌ Null values where not allowed

❌ Invalid ranges

❌ Broken relationships between tables

🏗 Types of SQL Constraints
Constraint	Purpose	Example Syntax
NOT NULL	Prevents NULL values	name VARCHAR(50) NOT NULL
UNIQUE	Ensures distinct values	email VARCHAR(100) UNIQUE
PRIMARY KEY	Unique + Not Null (row identifier)	id INT PRIMARY KEY
FOREIGN KEY	Maintains referential integrity	dept_id INT REFERENCES departments(id)
CHECK	Validates condition	age INT CHECK (age >= 18)
DEFAULT	Sets default value	status VARCHAR(20) DEFAULT 'active'
🛠 Defining Constraints During Table Creation
CREATE TABLE students (
    id INT PRIMARY KEY,
    name VARCHAR(50) NOT NULL,
    score INT CHECK (score >= 0 AND score <= 100),
    status VARCHAR(20) DEFAULT 'active'
);

✅ Constraints are enforced automatically by the database engine.

🔄 Adding Constraints to Existing Tables
ALTER TABLE students
ADD CONSTRAINT chk_score CHECK (score >= 0);

You can modify structure without recreating the table.

🔑 PRIMARY KEY
📌 Definition

A Primary Key uniquely identifies each row in a table.

Must be UNIQUE

Must be NOT NULL

Only one per table

Can be composite (multiple columns)

✅ Add Primary Key During Creation
CREATE TABLE departments (
    dept_id INT PRIMARY KEY,
    dept_name VARCHAR(50)
);
✅ Add Primary Key to Existing Table
ALTER TABLE employees
ADD CONSTRAINT pk_emp_id PRIMARY KEY (emp_id);
🔗 FOREIGN KEY
📌 Definition

A Foreign Key creates a relationship between two tables.

References a Primary Key in another table

Prevents orphan records

Enforces referential integrity

✅ Add Foreign Key During Creation
CREATE TABLE employees (
    emp_id INT PRIMARY KEY,
    name VARCHAR(50),
    dept_id INT,
    FOREIGN KEY (dept_id) REFERENCES departments(dept_id)
);
✅ Add Foreign Key to Existing Table
ALTER TABLE employees
ADD CONSTRAINT fk_dept_id
FOREIGN KEY (dept_id)
REFERENCES departments(dept_id);
🔄 Complete Example Workflow
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
✅ What This Achieves

Employees must belong to an existing department

No duplicate employee IDs

No NULL primary keys

Referential integrity maintained

🧠 Why Constraints Matter in Data Science

✔ Prevents dirty data at source
✔ Improves data reliability
✔ Avoids duplicates before analysis
✔ Maintains consistent relationships
✔ Reduces data cleaning effort

⚠ Common Errors to Avoid

Adding foreign key before parent table exists

Trying to insert child record without parent

Adding primary key on column with duplicates

Forgetting WHERE in updates

🏁 Best Practices

Always define Primary Keys

Use Foreign Keys for relational datasets

Add CHECK constraints for validation rules

Use DEFAULT values for predictable states

Name constraints explicitly (pk_, fk_, chk_)
