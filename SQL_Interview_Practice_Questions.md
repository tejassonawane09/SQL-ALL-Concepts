# SQL Interview Questions (Most Asked)

## Table Structure Used

employees( emp_id INT, emp_name VARCHAR(50), dept VARCHAR(20), salary
INT );

------------------------------------------------------------------------

## 1. Find Second Highest Salary

``` sql
SELECT MAX(salary) AS second_highest_salary
FROM employees
WHERE salary < (SELECT MAX(salary) FROM employees);
```

Explanation: First find highest salary. Then find maximum salary less
than highest.

------------------------------------------------------------------------

## 2. Find Second Highest Salary (Using LIMIT)

``` sql
SELECT salary
FROM employees
ORDER BY salary DESC
LIMIT 1 OFFSET 1;
```

Explanation: Sort salaries descending. Skip first row. Take second row.

------------------------------------------------------------------------

## 3. Find Nth Highest Salary

``` sql
SELECT DISTINCT salary
FROM employees e1
WHERE 2 = (
  SELECT COUNT(DISTINCT salary)
  FROM employees e2
  WHERE e2.salary >= e1.salary
);
```

------------------------------------------------------------------------

## 4. Department-wise Highest Salary

``` sql
SELECT dept, MAX(salary) AS max_salary
FROM employees
GROUP BY dept;
```

------------------------------------------------------------------------

## 5. Employee with Highest Salary in Each Department

``` sql
SELECT e.*
FROM employees e
JOIN (
  SELECT dept, MAX(salary) AS max_salary
  FROM employees
  GROUP BY dept
) m
ON e.dept = m.dept AND e.salary = m.max_salary;
```

------------------------------------------------------------------------

## 6. Find Duplicate Employees

``` sql
SELECT emp_name, COUNT(*)
FROM employees
GROUP BY emp_name
HAVING COUNT(*) > 1;
```

------------------------------------------------------------------------

## 7. Employees Earning More Than Average Salary

``` sql
SELECT *
FROM employees
WHERE salary > (SELECT AVG(salary) FROM employees);
```

------------------------------------------------------------------------

## 8. Department with Highest Average Salary

``` sql
SELECT dept
FROM employees
GROUP BY dept
ORDER BY AVG(salary) DESC
LIMIT 1;
```

------------------------------------------------------------------------

## 9. Top 3 Salaries

``` sql
SELECT DISTINCT salary
FROM employees
ORDER BY salary DESC
LIMIT 3;
```

------------------------------------------------------------------------

## 10. Rank Employees by Salary

``` sql
SELECT emp_name, salary,
DENSE_RANK() OVER (ORDER BY salary DESC) AS rank_no
FROM employees;
```

Explanation: Window function used to rank employees without collapsing
rows.

------------------------------------------------------------------------

## Final Interview Tip

Explain logic clearly before writing query. Interviewers check
understanding, not memorization.
