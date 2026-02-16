# SQL Fundamentals — Basic Querying

> Topics covered: SELECT, WHERE, ORDER BY, LIMIT/OFFSET, DISTINCT, Alias, BETWEEN, IN/NOT IN, LIKE, IS NULL  
> Examples are based on the `employee` table shown below.

---

## Sample Table Used in Examples

```sql
employee
----------------------------------
id | name   | salary | dept  | join_date
----------------------------------
1  | Amit   | 50000  | IT    | 2023-01-10
2  | Neha   | 60000  | HR    | 2022-05-12
3  | Raj    | 45000  | IT    | 2021-03-15
4  | Sneha  | 70000  | Sales | 2020-07-01
```

---

## 1) SELECT

### What it does
`SELECT` is used to **retrieve data** from a table. It does not change the data — it only reads it.

### Syntax
```sql
SELECT column_name
FROM table_name;
```

### Examples
Select all columns:
```sql
SELECT * FROM employee;
```

Select specific columns:
```sql
SELECT name, salary
FROM employee;
```

### Interview answer
`SELECT` is used to retrieve data from one or more tables. We can fetch all columns using `*` or specific columns by name.

---

## 2) WHERE

### What it does
`WHERE` filters rows based on a condition.  
Without `WHERE`, SQL returns all rows. With `WHERE`, it returns only matching rows.

### Syntax
```sql
SELECT columns
FROM table
WHERE condition;
```

### Examples
Employees from IT department:
```sql
SELECT *
FROM employee
WHERE dept = 'IT';
```

Salary greater than 50000:
```sql
SELECT name, salary
FROM employee
WHERE salary > 50000;
```

### Interview answer
`WHERE` is used to filter records based on conditions so that we retrieve only required rows instead of the entire table.

---

## 3) ORDER BY

### What it does
`ORDER BY` sorts the result set.

- Default is **ascending** order
- Use `DESC` for **descending** order

### Syntax
```sql
SELECT columns
FROM table
ORDER BY column_name ASC;  -- or DESC
```

### Examples
Sort by salary ascending:
```sql
SELECT *
FROM employee
ORDER BY salary;
```

Sort by salary descending:
```sql
SELECT *
FROM employee
ORDER BY salary DESC;
```

### Interview answer
`ORDER BY` sorts query results in ascending or descending order based on one or more columns.

---

## 4) LIMIT / OFFSET

### What it does
- `LIMIT` restricts how many rows are returned  
- `OFFSET` skips a number of rows before returning results  
This is commonly used in **pagination**.

> Note: Some databases use different syntax (for example, SQL Server uses `TOP` and `OFFSET...FETCH`). The concept is the same.

### Syntax
```sql
SELECT columns
FROM table
LIMIT n OFFSET m;
```

### Examples
Return first 2 rows:
```sql
SELECT *
FROM employee
LIMIT 2;
```

Skip first row and return next 2 rows:
```sql
SELECT *
FROM employee
LIMIT 2 OFFSET 1;
```

### Interview answer
`LIMIT` controls the number of rows returned and `OFFSET` skips rows. This is used in pagination (page-wise data loading).

---

## 5) DISTINCT

### What it does
`DISTINCT` removes duplicate values from the result.

### Syntax
```sql
SELECT DISTINCT column_name
FROM table;
```

### Example
Unique departments:
```sql
SELECT DISTINCT dept
FROM employee;
```

### Interview answer
`DISTINCT` is used to return unique values by removing duplicates from the result set.

---

## 6) Alias

### What it does
Alias gives a **temporary name** to a column or table to make output more readable.

### Syntax
```sql
SELECT column_name AS alias_name
FROM table;
```

### Example
```sql
SELECT
  name AS Employee_Name,
  salary AS Monthly_Salary
FROM employee;
```

### Interview answer
Alias helps improve readability, especially in reports, joins, and complex calculations.

---

## 7) BETWEEN

### What it does
`BETWEEN` filters values within a range and **includes both ends** (start and end values).

### Syntax
```sql
SELECT columns
FROM table
WHERE column BETWEEN value1 AND value2;
```

### Example
Salary between 45000 and 60000:
```sql
SELECT *
FROM employee
WHERE salary BETWEEN 45000 AND 60000;
```

### Interview answer
`BETWEEN` checks whether a value falls within an inclusive range (both boundary values are included).

---

## 8) IN / NOT IN

### What it does
`IN` checks if a value matches **any value** in a list.  
`NOT IN` excludes values in a list.

### Syntax
```sql
WHERE column IN (value1, value2, ...)

WHERE column NOT IN (value1, value2, ...)
```

### Examples
Employees in IT or HR:
```sql
SELECT *
FROM employee
WHERE dept IN ('IT', 'HR');
```

Employees not in IT or HR:
```sql
SELECT *
FROM employee
WHERE dept NOT IN ('IT', 'HR');
```

### Interview answer
`IN` filters rows matching a list of values, and `NOT IN` excludes rows matching those values.

---

## 9) LIKE

### What it does
`LIKE` is used for **pattern matching** on text.

Wildcards:
- `%` = any number of characters
- `_` = exactly one character

### Syntax
```sql
WHERE column LIKE 'pattern';
```

### Examples
Names starting with S:
```sql
SELECT *
FROM employee
WHERE name LIKE 'S%';
```

Names ending with a:
```sql
SELECT *
FROM employee
WHERE name LIKE '%a';
```

### Interview answer
`LIKE` is used for pattern matching in strings using wildcards such as `%` and `_`.

---

## 10) IS NULL

### What it does
Used to check NULL values.

Important rule:
- You **cannot** use `= NULL`
- You must use `IS NULL` (or `IS NOT NULL`)

### Syntax
```sql
WHERE column IS NULL;

WHERE column IS NOT NULL;
```

### Examples
Find rows where salary is missing:
```sql
SELECT *
FROM employee
WHERE salary IS NULL;
```

### Interview answer
`IS NULL` is used to check NULL values because NULL represents missing/unknown data and cannot be compared with `=`.

---

## Quick Interview Summary 

Basic querying in SQL includes retrieving data using `SELECT`, filtering using `WHERE`, sorting using `ORDER BY`, controlling output size using `LIMIT/OFFSET`, removing duplicates with `DISTINCT`, improving readability with `Alias`, range filtering using `BETWEEN`, multi-value filtering using `IN/NOT IN`, pattern matching using `LIKE`, and handling missing values using `IS NULL`.
