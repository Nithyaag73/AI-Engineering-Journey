 🔐 SQL Constraints

Constraints enforce data integrity and prevent invalid data entry.

---

## Types of Constraints

| Constraint | Purpose | Example |
|------------|----------|----------|
| NOT NULL | Prevents NULL values | name VARCHAR(50) NOT NULL |
| UNIQUE | Ensures distinct values | email VARCHAR(100) UNIQUE |
| PRIMARY KEY | Unique + Not Null | id INT PRIMARY KEY |
| FOREIGN KEY | Maintains relationships | dept_id INT REFERENCES departments(id) |
| CHECK | Validates condition | age INT CHECK (age >= 18) |
| DEFAULT | Sets default value | status VARCHAR(20) DEFAULT 'active' |

---

# 🛠 Creating Table with Constraints

```sql
CREATE TABLE students (
    id INT PRIMARY KEY,
    name VARCHAR(50) NOT NULL,
    score INT CHECK (score >= 0 AND score <= 100),
    status VARCHAR(20) DEFAULT 'active'
);
```

---

# 🔄 Adding Constraint Using ALTER

```sql
ALTER TABLE students
ADD CONSTRAINT chk_score
CHECK (score >= 0);
```

---

# 🔑 PRIMARY KEY

## Definition

- Uniquely identifies each row
- Cannot be NULL
- Must be unique
- Only one per table
- Can be composite

---

## Add Primary Key During Creation

```sql
CREATE TABLE departments (
    dept_id INT PRIMARY KEY,
    dept_name VARCHAR(50)
);
```

---

## Add Primary Key to Existing Table

```sql
ALTER TABLE employees
ADD CONSTRAINT pk_emp_id
PRIMARY KEY (emp_id);
```

---

# 🔗 FOREIGN KEY

## Definition

- Links one table to another
- References a Primary Key
- Prevents orphan records
- Maintains referential integrity

---

## Add Foreign Key During Creation

```sql
CREATE TABLE employees (
    emp_id INT PRIMARY KEY,
    name VARCHAR(50),
    dept_id INT,
    FOREIGN KEY (dept_id)
    REFERENCES departments(dept_id)
);
```

---

## Add Foreign Key to Existing Table

```sql
ALTER TABLE employees
ADD CONSTRAINT fk_dept_id
FOREIGN KEY (dept_id)
REFERENCES departments(dept_id);
```

---

# 🔄 Complete Workflow Example

```sql
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
```

---

# 📈 Index Example

```sql
CREATE INDEX idx_salary
ON employees(salary);
```

---

# ⚠ Common Mistakes

- Adding foreign key before parent table exists
- Inserting child record without parent
- Forgetting WHERE clause in UPDATE or DELETE
- Adding primary key on column with duplicates

---

# 🏁 Best Practices

✔ Always define Primary Keys  
✔ Use Foreign Keys in relational datasets  
✔ Add CHECK constraints for validation  
✔ Use DEFAULT values where appropriate  
✔ Avoid SELECT * in production  
✔ Name constraints clearly (pk_, fk_, chk_)

---

# 🎯 SQL in Data Science Workflow

1. Extract data
2. Clean & filter
3. Aggregate & transform
4. Export to Python / BI tools
5. Visualize & model

---
