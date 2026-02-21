# 🚀 MySQL Data Import & Export Guide  

![MySQL](https://img.shields.io/badge/MySQL-8.0+-blue?logo=mysql)
![SQL](https://img.shields.io/badge/SQL-Command%20Line-green)
![Status](https://img.shields.io/badge/Status-Production%20Ready-brightgreen)
![License](https://img.shields.io/badge/License-MIT-yellow)

> A professional step-by-step guide to **importing CSV data into MySQL** and **exporting MySQL data** using the command line.  
> Designed for SQL learners, Data Science students, and Backend developers.

---

## 📌 Table of Contents

- [Prerequisites](#-prerequisites)
- [Data Import](#-data-import-using-command-line)
- [Data Export](#-data-export-from-mysql)
- [Common Errors](#-common-errors--solutions)
- [Summary](#-summary)
---

# 📥 Data Import Using Command Line

---

## 1️⃣ Create Database & Table

```sql
CREATE DATABASE FacilityServices;
USE FacilityServices;

CREATE TABLE employees (
    id INT,
    name VARCHAR(100),
    department VARCHAR(100),
    salary INT
);
```

---

## 2️⃣ Navigate to MySQL BIN Directory (Windows)

```bash
cd C:\Program Files\MySQL\MySQL Server 8.0\bin
```

---

## 3️⃣ Connect to MySQL

```bash
mysql -u root -p
```

Enter your password.

---

## 4️⃣ Enable Local File Import (Very Important)

```sql
SET GLOBAL local_infile = 1;
```

Exit MySQL:

```sql
quit;
```

---

## 5️⃣ Reconnect with Local Infile Enabled

```bash
mysql --local-infile=1 -u root -p
```

Select your database:

```sql
USE FacilityServices;
```

---

## 6️⃣ Import CSV File

```sql
LOAD DATA LOCAL INFILE 'C:\\full\\path\\file.csv'
INTO TABLE employees
FIELDS TERMINATED BY ','
ENCLOSED BY '"'
LINES TERMINATED BY '\r\n'
IGNORE 1 ROWS;
```

### 🔎 Explanation

- `FIELDS TERMINATED BY ','` → Defines column separator  
- `ENCLOSED BY '"'` → Handles quoted values  
- `LINES TERMINATED BY '\r\n'` → Windows line ending  
- `IGNORE 1 ROWS` → Skips header row  

⚠ **Important (Windows Users):**  
Always use double backslashes (`\\`) in file paths.

---

# 📤 Data Export from MySQL

---

## ✅ Method 1: Export to CSV Using SELECT INTO OUTFILE

```sql
SELECT *
FROM employees
INTO OUTFILE 'C:\\full\\path\\exported_file.csv'
FIELDS TERMINATED BY ','
ENCLOSED BY '"'
LINES TERMINATED BY '\r\n';
```

### ⚠ Notes:
- File must NOT already exist  
- MySQL must have write permission  
- Check export directory using:

```sql
SHOW VARIABLES LIKE "secure_file_priv";
```

---

## ✅ Method 2: Full Database Backup (Recommended)

```bash
mysqldump -u root -p FacilityServices > backup.sql
```

Export a specific table:

```bash
mysqldump -u root -p FacilityServices employees > employees_backup.sql
```

---

# ⚠ Common Errors & Solutions

### ❌ Error:  
> The used command is not allowed with this MySQL version

### ✅ Solution:
```sql
SET GLOBAL local_infile = 1;
```

---

### ❌ Error:  
> Access denied for outfile

### ✅ Solution:
- Check `secure_file_priv` variable  
- Export only inside allowed directory  

---

# 📊 Summary

| Operation        | Command Used                  |
|------------------|-------------------------------|
| Import CSV       | `LOAD DATA LOCAL INFILE`      |
| Export CSV       | `SELECT INTO OUTFILE`         |
| Full Backup      | `mysqldump`                   |

---

### 👩‍💻 Author
NITHYA G
