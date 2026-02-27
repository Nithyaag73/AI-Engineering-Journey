# 🚀 Complete SQL Concepts

![SQL](https://img.shields.io/badge/Language-SQL-blue?style=for-the-badge&logo=mysql)
![MySQL](https://img.shields.io/badge/Database-MySQL-orange?style=for-the-badge)
![Level](https://img.shields.io/badge/Level-Beginner_to_Advanced-green?style=for-the-badge)
![Status](https://img.shields.io/badge/Project-Active-success?style=for-the-badge)



---

# 📌 Project Overview

This repository contains structured SQL concepts with practical examples, including:

- Core SQL (DDL, DML, DQL)
- Joins
- Subqueries
- Views
- Stored Procedures
- Window Functions
- Indexing & Optimization
- Transactions & ACID
- Triggers

The goal of this project is to achieve **complete SQL proficiency for Data Analytics, Backend Development, and Database Engineering.**

---

# 📂 Module Structure

```
SQL-Mastery/
│
├── 01_DDL_DML/
├── 02_JOINS/
├── 03_SUBQUERIES/
├── 04_VIEWS/
├── 05_STORED_PROCEDURES/
├── 06_WINDOW_FUNCTIONS/
├── 07_INDEXING/
├── 08_TRANSACTIONS/
├── 09_TRIGGERS/
└── README.md
```

---

# 🧱 1️⃣ Core SQL Concepts

## DDL – Data Definition Language

```sql
CREATE TABLE players (
    player_id INT PRIMARY KEY,
    player_name VARCHAR(50),
    country VARCHAR(50),
    goals INT
);
```

## DML – Data Manipulation Language

```sql
INSERT INTO players VALUES (1, 'Ronaldo', 'Portugal', 15);

UPDATE players
SET goals = 20
WHERE player_name = 'Ronaldo';

DELETE FROM players WHERE player_id = 1;
```

---

# 🔗 2️⃣ JOINS

## INNER JOIN

```sql
SELECT a.productName, b.textDescription
FROM products a
JOIN productlines b
ON a.productLine = b.productLine;
```

## LEFT JOIN

```sql
SELECT c.customerName, o.orderNumber
FROM customers c
LEFT JOIN orders o
ON c.customerNumber = o.customerNumber;
```

---

# 🔍 3️⃣ Subqueries (Nested Queries)

## Salary Greater Than Average

```sql
SELECT *
FROM customers
WHERE salary > (
    SELECT AVG(salary)
    FROM customers
);
```

## 2nd Highest Salary

```sql
SELECT MAX(salary)
FROM customers
WHERE salary < (
    SELECT MAX(salary)
    FROM customers
);
```

---

# 👁️ 4️⃣ Views

## Create View

```sql
CREATE VIEW prod_com AS
SELECT 
    a.productCode,
    a.productName,
    a.MSRP,
    b.textDescription
FROM products a
JOIN productlines b
ON a.productLine = b.productLine;
```

## Use View

```sql
SELECT * FROM prod_com;
```

✔ Virtual table  
✔ No extra storage  
✔ Simplifies complex queries  

---

# ⚙️ 5️⃣ Stored Procedures

## Basic Procedure

```sql
DELIMITER //

CREATE PROCEDURE top_players()
BEGIN
    SELECT player_name, country, goals
    FROM players
    WHERE goals > 6;
END //

DELIMITER ;
```

## Procedure with IN Parameter

```sql
CREATE PROCEDURE top_players_limit(IN num INT)
BEGIN
    SELECT player_name, goals
    FROM players
    ORDER BY goals DESC
    LIMIT num;
END;
```

## Procedure with OUT Parameter

```sql
CREATE PROCEDURE player_count(OUT total_players INT)
BEGIN
    SELECT COUNT(*) INTO total_players FROM players;
END;
```

---

# 📊 6️⃣ Window Functions

## PARTITION BY

```sql
SELECT 
    player_name,
    country,
    goals,
    RANK() OVER (PARTITION BY country ORDER BY goals DESC) AS country_rank
FROM players;
```

## Running Total

```sql
SELECT 
    player_name,
    goals,
    SUM(goals) OVER (ORDER BY goals) AS running_total
FROM players;
```

---

# 🚀 7️⃣ Indexing

## Create Index

```sql
CREATE INDEX idx_player_name
ON players(player_name);
```

✔ Improves search performance  
✔ Speeds up WHERE and JOIN operations  

---

# 🔄 8️⃣ Transactions & ACID

## Transaction Example

```sql
START TRANSACTION;

UPDATE players
SET goals = goals + 1
WHERE player_name = 'Ronaldo';

COMMIT;
```

Or rollback:

```sql
ROLLBACK;
```

### ACID Properties

- Atomicity
- Consistency
- Isolation
- Durability

---

# 🔔 9️⃣ Triggers

## Example Trigger

```sql
DELIMITER //

CREATE TRIGGER before_player_update
BEFORE UPDATE ON players
FOR EACH ROW
BEGIN
    SET NEW.goals = IF(NEW.goals < 0, 0, NEW.goals);
END //

DELIMITER ;
```

---

# 🧠 Architecture Understanding

### Query Execution Flow

User Query  
→ Parser  
→ Optimizer  
→ Execution Engine  
→ Storage Engine  
→ Result

---

⭐ If you found this repository helpful, consider giving it a star!
