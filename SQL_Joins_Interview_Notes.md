# SQL Joins -- Interview Notes

## Why Joins Are Important

In real-world databases, data is stored in multiple tables. Joins are
used to combine related data from different tables using a common
column.

------------------------------------------------------------------------

## 1. INNER JOIN

Returns only matching records from both tables.

### Syntax:

``` sql
SELECT columns
FROM table1
INNER JOIN table2
ON table1.column = table2.column;
```

### Interview Answer:

INNER JOIN returns only rows where matching values exist in both tables.

------------------------------------------------------------------------

## 2. LEFT JOIN (LEFT OUTER JOIN)

Returns all records from the left table and matching records from the
right table. If no match exists, NULL values are returned.

### Syntax:

``` sql
SELECT columns
FROM table1
LEFT JOIN table2
ON table1.column = table2.column;
```

### Interview Answer:

LEFT JOIN returns all records from the left table and matched records
from the right table.

------------------------------------------------------------------------

## 3. RIGHT JOIN (RIGHT OUTER JOIN)

Returns all records from the right table and matching records from the
left table. If no match exists, NULL values are returned.

### Syntax:

``` sql
SELECT columns
FROM table1
RIGHT JOIN table2
ON table1.column = table2.column;
```

### Interview Answer:

RIGHT JOIN returns all records from the right table and matched records
from the left table.

------------------------------------------------------------------------

## 4. FULL JOIN (FULL OUTER JOIN)

Returns all records from both tables, matched where possible. Unmatched
rows contain NULL values.

### Syntax:

``` sql
SELECT columns
FROM table1
FULL JOIN table2
ON table1.column = table2.column;
```

### Interview Answer:

FULL JOIN returns all records from both tables including unmatched ones.

------------------------------------------------------------------------

## 5. SELF JOIN

A table joined with itself. Used for hierarchical data like
employee-manager relationships.

### Syntax:

``` sql
SELECT e.name AS Employee,
       m.name AS Manager
FROM employee e
LEFT JOIN employee m
ON e.manager_id = m.emp_id;
```

### Interview Answer:

SELF JOIN is used when a table needs to be joined with itself.

------------------------------------------------------------------------

## 6. CROSS JOIN

Returns all possible combinations of rows from both tables (Cartesian
product).

### Syntax:

``` sql
SELECT columns
FROM table1
CROSS JOIN table2;
```

### Interview Answer:

CROSS JOIN returns all possible combinations of rows from both tables.

------------------------------------------------------------------------

## Quick Comparison Table

  Join Type   Result
  ----------- ---------------------------
  INNER       Only matching rows
  LEFT        All left + matching right
  RIGHT       All right + matching left
  FULL        All rows from both
  SELF        Table joined with itself
  CROSS       Cartesian product

------------------------------------------------------------------------

## Final Interview Summary

Joins are used to combine data from multiple tables based on related
columns. INNER JOIN returns matched records, LEFT and RIGHT JOIN include
unmatched records from one side, FULL JOIN includes all records from
both tables, SELF JOIN joins a table with itself, and CROSS JOIN returns
all possible combinations.
