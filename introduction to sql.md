SQL provides a foundational way to interact with relational databases, making it essential for data science tasks like querying datasets. It's a standard language you'll use in tools like Jupyter Notebook or Power BI for analysis.

What is SQL?
SQL stands for Structured Query Language, a domain-specific language designed for managing and manipulating relational databases. It became an ANSI standard in 1986 and ISO standard in 1987, enabling consistent use across systems like MySQL, PostgreSQL, and SQL Server. Unlike general-purpose languages such as Python, SQL focuses solely on data operations within tables organized by rows and columns.

Key Capabilities
SQL handles core database tasks through simple commands.

Execute queries to retrieve specific data from tables.

Insert, update, or delete records to modify datasets.

Create databases, tables, views, stored procedures, and set permissions.

How SQL Works
A SQL query follows a process: parsing for syntax, optimization for efficiency, execution on the database engine, and output of results. Components include databases (data collections), tables (structured storage), indexes (for fast lookups), and constraints (to enforce data integrity like unique values or non-null fields).

Basic Commands
SQL divides into categories for practical use.

Category	Purpose	Examples
DDL (Data Definition)	Define structure	CREATE TABLE, ALTER TABLE, DROP TABLE 
​
DML (Data Manipulation)	Modify data	INSERT, UPDATE, DELETE 
​
DQL (Data Query)	Retrieve data	SELECT 
​
DCL (Data Control)	Manage access	GRANT, REVOKE 
​
Getting Started Example
To create a simple table for a data science project:

text
CREATE TABLE employees (
    id INT PRIMARY KEY,
    name VARCHAR(50),
    salary DECIMAL(10,2)
);
This sets up a table with constraints; insert data next with INSERT INTO employees VALUES (1, 'Alice', 50000);
