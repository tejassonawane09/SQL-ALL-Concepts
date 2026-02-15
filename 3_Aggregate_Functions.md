# 🔹 3. Aggregate Functions 

## ✅ What Are Aggregate Functions?
Aggregate functions perform calculations on multiple rows and return **a single value** (a summary).

Common uses:
- Total salary of employees
- Average sales
- Maximum revenue
- Number of customers

They are often used with:
- `WHERE` (filter rows first)
- `GROUP BY` (summarize by category)
- `HAVING` (filter groups)

---

## Example Table (for understanding)

```sql
employee
----------------------------------
id | name   | salary | dept
----------------------------------
1  | Amit   | 50000  | IT
2  | Neha   | 60000  | HR
3  | Raj    | 45000  | IT
4  | Sneha  | 70000  | Sales
```

---

## 1️⃣ `COUNT()`

### ✅ What it does
Returns the **number of rows**.

### ✅ Syntax
```sql
SELECT COUNT(column_name)
FROM table;
```

### ✅ Types of `COUNT`

**1) `COUNT(*)` → counts all rows**
```sql
SELECT COUNT(*)
FROM employee;
```
**Output:** `4`

**2) `COUNT(column)` → counts non-NULL values only**
```sql
SELECT COUNT(salary)
FROM employee;
```
If one `salary` is `NULL`, it will not be counted.

**3) `COUNT(DISTINCT column)` → counts unique values**
```sql
SELECT COUNT(DISTINCT dept)
FROM employee;
```
**Output:** `3` (`IT`, `HR`, `Sales`)

### ✅ Interview answer
`COUNT()` returns total number of rows. `COUNT(*)` counts all rows, while `COUNT(column)` ignores `NULL` values.

---

## 2️⃣ `SUM()`

### ✅ What it does
Calculates the **total** of a numeric column.

### ✅ Syntax
```sql
SELECT SUM(column)
FROM table;
```

### ✅ Example
```sql
SELECT SUM(salary)
FROM employee;
```
**Output:** `50000 + 60000 + 45000 + 70000 = 225000`

### ✅ Interview answer
`SUM()` calculates the total value of a numeric column and ignores `NULL` values.

---

## 3️⃣ `AVG()`

### ✅ What it does
Calculates the **average (mean)** of a numeric column.

### ✅ Syntax
```sql
SELECT AVG(column)
FROM table;
```

### ✅ Example
```sql
SELECT AVG(salary)
FROM employee;
```
**Output:** `225000 / 4 = 56250`

> Note: `AVG()` ignores `NULL` values.

### ✅ Interview answer
`AVG()` returns the mean value of a numeric column and ignores `NULL` values.

---

## 4️⃣ `MIN()`

### ✅ What it does
Returns the **smallest** value in a column.

Works with:
- Numbers
- Dates
- Strings (alphabetical)

### ✅ Example (Number)
```sql
SELECT MIN(salary)
FROM employee;
```
**Output:** `45000`

### ✅ Example (Date)
```sql
SELECT MIN(join_date)
FROM employee;
```
Returns the **earliest** date.

### ✅ Interview answer
`MIN()` returns the lowest value from a column and works with numeric, date, and text columns.

---

## 5️⃣ `MAX()`

### ✅ What it does
Returns the **largest** value in a column.

### ✅ Example (Number)
```sql
SELECT MAX(salary)
FROM employee;
```
**Output:** `70000`

### ✅ Example (Date)
```sql
SELECT MAX(join_date)
FROM employee;
```
Returns the **latest** date.

### ✅ Interview answer
`MAX()` returns the highest value from a column and works with numeric, date, and text columns.

---

## 🔹 Aggregates with `WHERE`
Filter rows first, then aggregate:

```sql
SELECT SUM(salary)
FROM employee
WHERE dept = 'IT';
```

---

## 🔹 Aggregates with `GROUP BY` (Very important)
Summarize by category:

```sql
SELECT dept, SUM(salary) AS total_salary
FROM employee
GROUP BY dept;
```

**Example output:**
- `IT` → `95000`
- `HR` → `60000`
- `Sales` → `70000`

---

## 🔹 Important Rules / Behavior
1. Aggregate functions **ignore NULL values**.
2. Without `GROUP BY`, they return **one single value**.
3. If you select a normal column with an aggregate, you must use `GROUP BY`.

**Wrong example (will error):**
```sql
SELECT dept, SUM(salary)
FROM employee;
```

---

## 🎯 Final Summary
Aggregate functions summarize data across multiple rows and return a single value. Common aggregates are `COUNT`, `SUM`, `AVG`, `MIN`, and `MAX`. They are often combined with `GROUP BY` for grouped summaries and ignore `NULL` values.
