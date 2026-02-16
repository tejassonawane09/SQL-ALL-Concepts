# SQL Window Functions - Complete Interview Notes

## 1. Introduction to Window Functions

Window functions perform calculations across a set of rows related to
the current row without collapsing rows.

Difference: - GROUP BY reduces rows - Window Functions do NOT reduce
rows

Basic Syntax:

function_name() OVER ( PARTITION BY column ORDER BY column )

------------------------------------------------------------------------

## 2. OVER()

Defines the window in which the function operates.

Example:

SELECT salary, SUM(salary) OVER() FROM employee;

------------------------------------------------------------------------

## 3. PARTITION BY

Divides data into groups without collapsing rows.

Example:

SELECT name, dept, salary, SUM(salary) OVER(PARTITION BY dept) AS
dept_total FROM employee;

------------------------------------------------------------------------

## 4. ROW_NUMBER()

Assigns unique sequential number per row.

SELECT name, dept, salary, ROW_NUMBER() OVER(PARTITION BY dept ORDER BY
salary DESC) AS row_num FROM employee;

------------------------------------------------------------------------

## 5. RANK()

Handles ties but skips rank numbers.

Example ranking: 1, 2, 2, 4

------------------------------------------------------------------------

## 6. DENSE_RANK()

Handles ties but does NOT skip rank numbers.

Example ranking: 1, 2, 2, 3

------------------------------------------------------------------------

## 7. SUM() OVER()

Used for running total or partition total.

SELECT name, salary, SUM(salary) OVER(ORDER BY salary) AS running_total
FROM employee;

------------------------------------------------------------------------

## 8. AVG() OVER()

Calculates average without grouping.

SELECT name, salary, AVG(salary) OVER() AS overall_avg FROM employee;

------------------------------------------------------------------------

## 9. LAG()

Returns previous row value.

SELECT name, salary, LAG(salary) OVER(ORDER BY salary) AS
previous_salary FROM employee;

------------------------------------------------------------------------

## 10. LEAD()

Returns next row value.

SELECT name, salary, LEAD(salary) OVER(ORDER BY salary) AS next_salary
FROM employee;

------------------------------------------------------------------------

## 11. FIRST_VALUE()

Returns first value in window.

SELECT name, salary, FIRST_VALUE(salary) OVER(ORDER BY salary DESC) AS
highest_salary FROM employee;

------------------------------------------------------------------------

## 12. LAST_VALUE()

Returns last value in window (often requires frame specification).

------------------------------------------------------------------------

## 13. NTH_VALUE()

Returns nth value from the window.

------------------------------------------------------------------------

## 14. CUME_DIST()

Returns cumulative distribution value between 0 and 1.

------------------------------------------------------------------------

## 15. PERCENT_RANK()

Returns percentage rank using formula: (rank - 1) / (total_rows - 1)

------------------------------------------------------------------------

## Important Interview Points

-   Window functions do not reduce rows.
-   They require OVER() clause.
-   PARTITION BY divides data logically.
-   ORDER BY defines ranking or sequence.
-   Commonly used for ranking, running totals, and comparison analysis.
