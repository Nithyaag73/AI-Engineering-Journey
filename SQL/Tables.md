<div align="center">

# 📘 SQL Cheat Sheet  
### DDL • DML • DQL

</div>

<hr>

<h2>🔵 1️⃣ DDL – Data Definition Language</h2>
<p><b>Used to define or modify database structure.</b></p>

<b>Commands:</b> CREATE • ALTER • DROP

<h3>🔹 CREATE TABLE</h3>

<pre>
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
</pre>

<h3>🔹 ALTER TABLE</h3>

<b>Add Column</b>

<pre>
ALTER TABLE table_name
ADD column_name datatype;

Example:

ALTER TABLE employee
ADD department VARCHAR(30);
</pre>

<b>Drop Column</b>

<pre>
ALTER TABLE table_name
DROP COLUMN column_name;
</pre>

<h3>🔹 DROP TABLE</h3>

<pre>
DROP TABLE table_name;
</pre>

<b>Difference:</b><br>
DELETE → removes rows<br>
DROP → removes entire table

<hr>

<h2>🔵 2️⃣ DML – Data Manipulation Language</h2>
<p><b>Used to manipulate data inside tables.</b></p>

<b>Commands:</b> INSERT • UPDATE • DELETE

<h3>🔹 INSERT</h3>

<pre>
INSERT INTO table_name (column1, column2)
VALUES (value1, value2);

Example:

INSERT INTO employee (first, last, age, salary)
VALUES ('Jonnie', 'Weber', 28, 19500);
</pre>

<b>Rules:</b><br>
Strings → use single quotes 'text'<br>
Numbers → no quotes

<hr>

<h2>🔵 3️⃣ DQL – Data Query Language</h2>
<p><b>Used to retrieve data from tables.</b></p>

<b>Main Command:</b> SELECT

<h3>🔹 SELECT Examples</h3>

<pre>
SELECT first, last FROM empinfo;

SELECT last, city, age FROM empinfo
WHERE age > 30;

SELECT * FROM empinfo;
</pre>

<h3>🔹 WHERE Clause</h3>

<pre>
Operators:
=   >   <   >=   <=   <>   AND   OR

Example:

SELECT * FROM employee
WHERE salary > 30000;
</pre>

<h3>🔹 LIKE Operator (Pattern Matching)</h3>

<b>Wildcards:</b><br>
%  → any characters<br>
_  → single character

<pre>
Starts with:
SELECT * FROM empinfo
WHERE first LIKE 'Er%';

Ends with:
SELECT * FROM empinfo
WHERE last LIKE '%s';

Contains:
SELECT * FROM empinfo
WHERE last LIKE '%illia%';
</pre>

<hr>

<h2>🚀 Summary</h2>

<table>
<tr>
<th>Category</th>
<th>Purpose</th>
<th>Commands</th>
</tr>
<tr>
<td>DDL</td>
<td>Define structure</td>
<td>CREATE, ALTER, DROP</td>
</tr>
<tr>
<td>DML</td>
<td>Modify data</td>
<td>INSERT, UPDATE, DELETE</td>
</tr>
<tr>
<td>DQL</td>
<td>Retrieve data</td>
<td>SELECT</td>
</tr>
</table>
