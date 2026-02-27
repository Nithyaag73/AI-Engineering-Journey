# 📘 SQL Stored Procedures & Window Functions – Complete Guide

![SQL](https://img.shields.io/badge/Language-SQL-blue?style=for-the-badge&logo=mysql)
![MySQL](https://img.shields.io/badge/Database-MySQL-orange?style=for-the-badge)
![Level](https://img.shields.io/badge/Level-Advanced-green?style=for-the-badge)

---

# 📌 What is a Stored Procedure?

A **Stored Procedure** is a precompiled SQL block stored inside the database that can be executed multiple times.

✔ Reusable  
✔ Improves performance  
✔ Reduces redundancy  
✔ Supports parameters (IN, OUT, INOUT)

---

# 🧠 Why Use Stored Procedures?

- Avoid rewriting repetitive queries
- Improve maintainability
- Control access to database logic
- Perform complex operations
- Accept dynamic inputs

---

# 🔹 Basic Stored Procedure Example

### Create Procedure

```sql
DELIMITER //

CREATE PROCEDURE SelectAllCustomers()
BEGIN
    SELECT * FROM customers;
END //

DELIMITER ;
```

### Call Procedure

```sql
CALL SelectAllCustomers();
```

---

# 🔹 Stored Procedure with IN Parameter

Example: Get Top N Players by Goals

```sql
DELIMITER //

CREATE PROCEDURE top_players_sort_by_goals(IN num INT)
BEGIN
    SELECT player_name, country, goals
    FROM players
    ORDER BY goals DESC
    LIMIT num;
END //

DELIMITER ;
```

### Call Procedure

```sql
CALL top_players_sort_by_goals(3);
```

✔ `IN` parameter receives input  
✔ Dynamic limit based on user input  

---

# 🔹 Stored Procedure with OUT Parameter

Example: Count Total Players

```sql
DELIMITER //

CREATE PROCEDURE player_count(OUT total_players INT)
BEGIN
    SELECT COUNT(*) 
    FROM players 
    INTO total_players;
END //

DELIMITER ;
```

### Call Procedure

```sql
CALL player_count(@total_count);
SELECT @total_count;
```

✔ `OUT` parameter returns value  
✔ Value stored in session variable  

---

# 🔹 Stored Procedure for UPDATE Operation

Example: Update Player Goals

```sql
DELIMITER //

CREATE PROCEDURE update_players(IN new_goals INT, IN player_name_input VARCHAR(50))
BEGIN
    UPDATE players
    SET goals = new_goals
    WHERE player_name = player_name_input;
END //

DELIMITER ;
```

### Call Procedure

```sql
CALL update_players(20, 'Ronaldo');
```

✔ Performs data modification  
✔ Uses input parameters  

---

# 🔹 Simple Procedure Example

```sql
DELIMITER &&

CREATE PROCEDURE top_players()
BEGIN
    SELECT player_name, country, goals
    FROM players
    WHERE goals > 6;
END &&

DELIMITER ;
```

---

# ⚠ Why Do We Use DELIMITER?

MySQL normally ends statements with `;`

But stored procedures contain multiple `;` inside.

So we temporarily change delimiter:

```
DELIMITER //
```

Then revert:

```
DELIMITER ;
```

---

# 📊 Window Functions in MySQL

A **Window Function** performs calculations across a set of rows related to the current row.

Unlike GROUP BY:
- It does NOT collapse rows
- It keeps individual row visibility

---

# 🔹 Basic Window Function Example

```sql
USE classicmodels;

SELECT 
    productLine,
    productName,
    SUM(MSRP) OVER (PARTITION BY productLine) AS total_msrp
FROM products;
```

---

# 🔎 Understanding OVER Clause

The `OVER()` clause defines the window.

It can:

1️⃣ Partition rows  
2️⃣ Order rows  

---

# 🔹 PARTITION BY Example

```sql
SELECT 
    player_name,
    country,
    goals,
    RANK() OVER (PARTITION BY country ORDER BY goals DESC) AS country_rank
FROM players;
```

✔ Partitions data by country  
✔ Ranks players inside each country  

---

# 🔹 Running Total Example

```sql
SELECT 
    player_name,
    goals,
    SUM(goals) OVER (ORDER BY goals) AS running_total
FROM players;
```

---

# 🧬 Execution Architecture

Stored Procedure Flow:

User → CALL procedure → Execute SQL block → Return Result

Window Function Flow:

Query → Define Window (OVER) → Apply Function → Return Enhanced Rows

---

# 🔄 Difference: GROUP BY vs Window Function

| GROUP BY | Window Function |
|----------|-----------------|
| Collapses rows | Keeps all rows |
| One row per group | One row per original row |
| Aggregated output | Analytical output |

---

# 🚀 Advantages of Stored Procedures

✔ Faster execution (precompiled)  
✔ Secure logic handling  
✔ Reduces network traffic  
✔ Modular programming  
✔ Centralized business logic  

---

# ❌ Disadvantages

✖ Harder debugging  
✖ Version control challenges  
✖ Vendor specific (MySQL, SQL Server differences)  

---

# 🎯 When to Use What?

Use Stored Procedures When:
- Business logic inside DB
- Repeated queries
- Controlled access needed

Use Window Functions When:
- Ranking
- Running totals
- Analytical queries
- Partitioned calculations

---

You are now moving into **Advanced SQL Engineering Level 🚀**
