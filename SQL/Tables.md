# 📘 SQL Cheat Sheet – DDL, DML & DQL

A quick reference guide for basic SQL commands used in relational databases like MySQL, PostgreSQL, and SQL Server.

------------------------------------------------------------

🔵 1️⃣ DDL – Data Definition Language
Used to define or modify database structure.

Includes:
CREATE
ALTER
DROP

------------------------------------------------------------

🔹 CREATE TABLE
Creates a new table.

CREATE TABLE table_name (
    column1 datatype,
    column2 datatype,
    column3 datatype
);

Example:

CREATE TABLE employee (
    id INT,
    first VARCHAR(20),
    last VARCHAR(20),
    age INT,
    salary FLOAT
);

------------------------------------------------------------

🔹 ALTER TABLE
Used to modify an existing table.

➤ Add Column

ALTER TABLE table_name
ADD column_name datatype;

Example:

ALTER TABLE employee
ADD department VARCHAR(30);

➤ Drop Column

ALTER TABLE table_name
DROP COLUMN column_name;

------------------------------------------------------------

🔹 DROP TABLE
Deletes entire table structure including data.

DROP TABLE table_name;

⚠ Difference:
DELETE → removes rows
DROP → removes entire table

------------------------------------------------------------

🔵 2️⃣ DML – Data Manipulation Language
Used to manipulate data inside tables.

Includes:
INSERT
UPDATE
DELETE

------------------------------------------------------------

🔹 INSERT
Adds rows to a table.

INSERT INTO table_name (column1, column2)
VALUES (value1, value2);

Example:

INSERT INTO employee (first, last, age, salary)
VALUES ('Jonnie', 'Weber', 28, 19500);

📌 Rules:
Strings → use single quotes 'text'
Numbers → no quotes

------------------------------------------------------------

🔵 3️⃣ DQL – Data Query Language
Used to retrieve data from tables.

Main Command:
SELECT

------------------------------------------------------------

🔹 SELECT Examples

SELECT first, last FROM empinfo;

SELECT last, city, age FROM empinfo
WHERE age > 30;

SELECT * FROM empinfo;

------------------------------------------------------------

🔹 WHERE Clause
Filters records.

Operators:
=
>
<
>=
<=
<>
AND
OR

Example:

SELECT * FROM employee
WHERE salary > 30000;

------------------------------------------------------------

🔹 LIKE Operator (Pattern Matching)

Wildcards:
%  → any characters
_  → single character

Examples:

Starts with:
SELECT * FROM empinfo
WHERE first LIKE 'Er%';

Ends with:
SELECT * FROM empinfo
WHERE last LIKE '%s';

Contains:
SELECT * FROM empinfo
WHERE last LIKE '%illia%';

------------------------------------------------------------

🚀 Summary

DDL → CREATE, ALTER, DROP
DML → INSERT, UPDATE, DELETE
DQL → SELECT

------------------------------------------------------------
