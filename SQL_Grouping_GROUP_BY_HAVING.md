# SQL Fundamentals -- Grouping (GROUP BY & HAVING)

## 1. GROUP BY

### What is GROUP BY?

GROUP BY is used to group rows that have the same values in a specified
column. It is mainly used with aggregate functions like COUNT, SUM, AVG,
MIN, and MAX.

------------------------------------------------------------------------

### Example Table

  id   name    salary   dept
  ---- ------- -------- -------
  1    Amit    50000    IT
  2    Neha    60000    HR
  3    Raj     45000    IT
  4    Sneha   70000    Sales

------------------------------------------------------------------------

### Example 1: Total Salary Department-wise

``` sql
SELECT dept, SUM(salary)
FROM employee
GROUP BY dept;
```

Output:

IT → 95000\
HR → 60000\
Sales → 70000

------------------------------------------------------------------------

### Important Rule

When using GROUP BY: - Every selected column must either be inside GROUP
BY\
OR\
- Used inside an aggregate function

------------------------------------------------------------------------

## 2. HAVING

### What is HAVING?

HAVING is used to filter grouped data.

Important: - WHERE filters rows\
- HAVING filters groups

------------------------------------------------------------------------

### Example: Departments with Total Salary \> 80000

``` sql
SELECT dept, SUM(salary) AS total_salary
FROM employee
GROUP BY dept
HAVING SUM(salary) > 80000;
```

Output:

IT → 95000

------------------------------------------------------------------------

## Difference Between WHERE and HAVING

  WHERE                            HAVING
  -------------------------------- -----------------------------
  Filters rows                     Filters groups
  Used before GROUP BY             Used after GROUP BY
  Cannot use aggregate functions   Can use aggregate functions

------------------------------------------------------------------------

## Execution Order in SQL

1.  FROM\
2.  WHERE\
3.  GROUP BY\
4.  HAVING\
5.  SELECT\
6.  ORDER BY

------------------------------------------------------------------------

## Interview Answer

GROUP BY is used to group rows based on one or more columns so that
aggregate functions like SUM, COUNT, and AVG can be applied to each
group separately.

HAVING is used to filter the grouped results based on aggregate
conditions, whereas WHERE filters rows before grouping.
