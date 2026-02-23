# SQL Date, Time & REGEX Functions Cheat Sheet

![SQL](https://img.shields.io/badge/Language-SQL-blue?style=flat-square&logo=mysql)
![MySQL](https://img.shields.io/badge/Database-MySQL-orange?style=flat-square&logo=mysql)
![Analytics](https://img.shields.io/badge/Use-Data_Analytics-green?style=flat-square)
![Status](https://img.shields.io/badge/Status-Active-brightgreen?style=flat-square)
![License](https://img.shields.io/badge/License-MIT-lightgrey?style=flat-square)

A practical and professional guide to Date & Time functions and Regular Expressions (REGEXP) in MySQL. Includes syntax and real query examples for Data Analytics and SQL practice.

---

## DATE & TIME FUNCTIONS

Date & Time functions are used to manipulate and extract information from date and time columns.

They help you to:
- Format dates
- Calculate differences between dates
- Extract specific parts (day, quarter, etc.)
- Add or subtract time intervals

---

### 1. DATEDIFF()

Returns the number of days between two dates.

Syntax:
```sql
DATEDIFF(date1, date2);
```

Example:
```sql
SELECT DATEDIFF('2025-01-10','2025-01-01') AS days_difference;
```

---

### 2. DATE_FORMAT()

Formats a date value into a specific format.

Syntax:
```sql
DATE_FORMAT(date, format);
```

Example:
```sql
SELECT DATE_FORMAT(NOW(), '%d-%m-%Y') AS formatted_date;
```

Common Format Specifiers:

| Format | Meaning |
|--------|---------|
| %d | Day (01-31) |
| %m | Month (01-12) |
| %Y | 4-digit year |
| %W | Weekday name |
| %M | Month name |

---

### 3. DAY()

Returns the day of the month.

```sql
SELECT DAY('2025-02-23') AS day_value;
```

---

### 4. QUARTER()

Returns the quarter of the year (1-4).

```sql
SELECT QUARTER('2025-02-23') AS quarter_value;
```

---

### 5. ADDDATE() / DATE_ADD()

Adds days or intervals to a date.

Syntax:
```sql
ADDDATE(date, INTERVAL value unit);
```

Example:
```sql
SELECT ADDDATE('2025-02-23', INTERVAL 10 DAY) AS new_date;
```

---

## REGEXP (Regular Expressions) in MySQL

When LIKE is not powerful enough, use REGEXP.

REGEXP helps to:
- Match specific patterns
- Search character ranges
- Find complex text patterns

Syntax:
```sql
SELECT column_name
FROM table_name
WHERE column_name REGEXP 'pattern';
```

---

### Example 1: Match values starting with 'w'

```sql
SELECT *
FROM customer
WHERE email REGEXP '^w';
```

^w matches values that start with the letter w.

---

### Example 2: Match specific characters (z, v, p)

```sql
SELECT *
FROM customer
WHERE email REGEXP '[zvp]';
```

[zvp] matches any value containing z OR v OR p.

---

### Example 3: Match character range (x to z)

```sql
SELECT *
FROM customer
WHERE email REGEXP '[x-z]';
```

[x-z] matches any character between x and z.

---

### Example 4: REGEXP instead of multiple LIKE

Instead of:

```sql
SELECT COUNT(*)
FROM telco_churna
WHERE customerID LIKE '%v%'
OR customerID LIKE '%w%'
OR customerID LIKE '%x%';
```

Use:

```sql
SELECT COUNT(*)
FROM telco_churna
WHERE customerID REGEXP '[vwx]';
```

This approach is cleaner, more readable, and scalable.

---

## LIKE vs REGEXP Comparison

| Feature | LIKE | REGEXP |
|----------|-------|---------|
| Simple wildcard search | Yes | Yes |
| Complex pattern matching | No | Yes |
| Character ranges | No | Yes |
| Multiple character match | Limited | Powerful |

---

## When to Use What?

- Use LIKE for simple wildcard searches (% and _).
- Use REGEXP for advanced pattern matching.

---

## Best Practices

- Avoid heavy REGEXP usage on very large datasets without indexing.
- Use DATE functions for reporting and analytics.
- Always validate REGEX patterns carefully.
- Prefer clean and readable queries.

---

## References

- MySQL Official Documentation
- W3Schools SQL Guide

---

