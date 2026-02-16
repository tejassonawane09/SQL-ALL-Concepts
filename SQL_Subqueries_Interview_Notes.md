
# 🔹 SQL Subqueries – Interview Ready Notes

## What is a Subquery?

A subquery is a query written inside another query.  
It executes first, and its result is used by the outer query.

Basic Structure:

```sql
SELECT column
FROM table
WHERE column operator (
    SELECT column
    FROM table
);
```

---

# 1️⃣ Single Row Subquery

### Definition:
A subquery that returns only one value.

### Used With:
=, >, <, >=, <=

### Example: Employees earning more than average salary

```sql
SELECT name, salary
FROM employee
WHERE salary > (
    SELECT AVG(salary)
    FROM employee
);
```

### Interview Answer:
A single row subquery returns one value and is typically used with comparison operators like =, >, or <.

---

# 2️⃣ Multi-row Subquery

### Definition:
Returns multiple values.

### Used With:
IN, ANY, ALL

### Example:

```sql
SELECT name
FROM employee
WHERE dept IN (
    SELECT dept
    FROM employee
    WHERE salary > 50000
);
```

### Interview Answer:
A multi-row subquery returns multiple values and is used with operators like IN, ANY, or ALL.

---

# 3️⃣ Correlated Subquery

### Definition:
A subquery that depends on the outer query and executes once per row.

### Example: Employees earning more than department average

```sql
SELECT e1.name, e1.salary, e1.dept
FROM employee e1
WHERE e1.salary > (
    SELECT AVG(e2.salary)
    FROM employee e2
    WHERE e1.dept = e2.dept
);
```

### Interview Answer:
A correlated subquery refers to a subquery that uses values from the outer query and executes once for each row.

---

# 4️⃣ EXISTS

### Definition:
Checks whether the subquery returns any row.

### Example:

```sql
SELECT dept_name
FROM department d
WHERE EXISTS (
    SELECT 1
    FROM employee e
    WHERE e.dept_id = d.dept_id
);
```

### Interview Answer:
EXISTS checks whether a subquery returns any row and stops execution after finding the first match.

---

# 5️⃣ IN

### Definition:
Checks if a value matches any value returned by the subquery.

### Example:

```sql
SELECT name
FROM employee
WHERE dept IN (
    SELECT dept
    FROM employee
    WHERE salary > 50000
);
```

---

# IN vs EXISTS

| IN | EXISTS |
|----|--------|
| Compares values | Checks existence |
| Slower for large data | Faster for large data |
| Returns all subquery values first | Stops after first match |

---

# Common Interview Question

### Find Second Highest Salary

```sql
SELECT MAX(salary)
FROM employee
WHERE salary < (
    SELECT MAX(salary)
    FROM employee
);
```

---

# Final Interview Summary

A subquery is a query written inside another query.  
It executes first and passes its result to the outer query.  
Subqueries can be single row, multi-row, or correlated.  
IN and EXISTS are commonly used to filter results efficiently.
