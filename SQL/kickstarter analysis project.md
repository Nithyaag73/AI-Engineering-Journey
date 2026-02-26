# 📊 Kickstarter Campaign Success Analysis (SQL Project)

## 📌 Project Overview

This project performs Exploratory Data Analysis (EDA) on Kickstarter crowdfunding data using SQL.  
The goal is to analyze patterns behind successful and failed campaigns using structured queries.

The project covers:
- Data Cleaning
- Data Exploration
- Success Rate Analysis
- Funding Pattern Analysis
- Time-Based Trend Analysis
- Geographic Analysis
- Backer Behavior Insights

---

## 🛠 Tech Stack

- SQL (MySQL)
- Kaggle Kickstarter Dataset
- Relational Database Design
- Aggregation & Analytical Queries

---

## 🗂 Database Schema

```sql
CREATE TABLE kickstarter_projects (
    id INT PRIMARY KEY,
    name VARCHAR(255),
    category VARCHAR(100),
    main_category VARCHAR(100),
    currency VARCHAR(10),
    deadline DATE,
    goal DECIMAL(15,2),
    launched DATE,
    pledged DECIMAL(15,2),
    state VARCHAR(20),
    backers INT,
    country VARCHAR(10),
    usd_pledged DECIMAL(15,2),
    usd_goal DECIMAL(15,2)
);
```

---

# 🔍 Project Workflow

## 1️⃣ Data Exploration

- Count total projects
- Identify unique states
- Check goal & pledged statistics
- Inspect dataset structure

Example:

```sql
SELECT COUNT(*) AS total_projects 
FROM kickstarter_projects;

SELECT DISTINCT state 
FROM kickstarter_projects;

SELECT 
    MIN(goal) AS min_goal,
    MAX(goal) AS max_goal,
    AVG(goal) AS avg_goal
FROM kickstarter_projects;
```

---

## 2️⃣ Data Cleaning

### Handling NULL Values

```sql
SELECT 
    SUM(CASE WHEN name IS NULL THEN 1 ELSE 0 END) AS null_names,
    SUM(CASE WHEN goal IS NULL THEN 1 ELSE 0 END) AS null_goals
FROM kickstarter_projects;
```

### Removing Duplicates

```sql
DELETE p1 FROM kickstarter_projects p1
INNER JOIN kickstarter_projects p2
WHERE p1.id > p2.id
AND p1.name = p2.name
AND p1.launched = p2.launched;
```

### Standardizing State Column

```sql
UPDATE kickstarter_projects
SET state = LOWER(TRIM(state));
```

---

## 3️⃣ Success Rate Analysis

### Overall Success Rate

```sql
SELECT 
    state,
    COUNT(*) AS project_count,
    ROUND(COUNT(*) * 100.0 / SUM(COUNT(*)) OVER(), 2) AS percentage
FROM kickstarter_projects
WHERE state IN ('successful', 'failed', 'canceled')
GROUP BY state;
```

### Success Rate by Category

```sql
SELECT 
    main_category,
    COUNT(*) AS total_projects,
    SUM(CASE WHEN state = 'successful' THEN 1 ELSE 0 END) AS successful,
    ROUND(
        SUM(CASE WHEN state = 'successful' THEN 1 ELSE 0 END) * 100.0 
        / COUNT(*), 
    2) AS success_rate
FROM kickstarter_projects
WHERE state IN ('successful', 'failed')
GROUP BY main_category
ORDER BY success_rate DESC;
```

---

## 4️⃣ Funding Analysis

### Goal Range Success Rate

```sql
SELECT 
    CASE 
        WHEN usd_goal < 1000 THEN 'Under $1K'
        WHEN usd_goal BETWEEN 1000 AND 10000 THEN '$1K-$10K'
        WHEN usd_goal BETWEEN 10001 AND 50000 THEN '$10K-$50K'
        WHEN usd_goal BETWEEN 50001 AND 100000 THEN '$50K-$100K'
        ELSE 'Over $100K'
    END AS goal_range,
    COUNT(*) AS total_projects,
    ROUND(
        SUM(CASE WHEN state = 'successful' THEN 1 ELSE 0 END) 
        * 100.0 / COUNT(*), 
    2) AS success_rate
FROM kickstarter_projects
WHERE state IN ('successful', 'failed')
GROUP BY goal_range
ORDER BY success_rate DESC;
```

---

## 5️⃣ Time-Based Analysis

### Success Rate by Launch Year

```sql
SELECT 
    YEAR(launched) AS launch_year,
    COUNT(*) AS total_projects,
    ROUND(
        SUM(CASE WHEN state = 'successful' THEN 1 ELSE 0 END) 
        * 100.0 / COUNT(*), 
    2) AS success_rate
FROM kickstarter_projects
WHERE state IN ('successful', 'failed')
GROUP BY YEAR(launched)
ORDER BY launch_year;
```

---

## 6️⃣ Geographic Analysis

```sql
SELECT 
    country,
    COUNT(*) AS total_projects,
    ROUND(
        SUM(CASE WHEN state = 'successful' THEN 1 ELSE 0 END) 
        * 100.0 / COUNT(*), 
    2) AS success_rate
FROM kickstarter_projects
WHERE state IN ('successful', 'failed')
GROUP BY country
ORDER BY total_projects DESC;
```

---

## 7️⃣ Backer Analysis

```sql
SELECT 
    state,
    ROUND(AVG(backers), 0) AS avg_backers
FROM kickstarter_projects
WHERE state IN ('successful', 'failed')
GROUP BY state;
```

---

# 📊 Key Insights

- Moderate funding goals show higher success probability.
- Successful campaigns attract significantly more backers.
- Campaign duration influences outcomes.
- Certain categories outperform others.
- Geographic trends impact funding behavior.
