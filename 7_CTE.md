# SQL - CTE (Common Table Expressions)

## What is a CTE?

CTE stands for Common Table Expression. It is a temporary result set
defined using the WITH keyword. It exists only during the execution of a
single query.

Basic Syntax:

WITH cte_name AS ( SELECT column FROM table ) SELECT \* FROM cte_name;

Why we use CTE: - Improves readability - Breaks complex queries into
parts - Reusable within same query - Handles hierarchical data

------------------------------------------------------------------------

# 1. Simple CTE

Example: Employees earning above average salary

WITH avg_salary_cte AS ( SELECT AVG(salary) AS avg_sal FROM employee )
SELECT name, salary FROM employee WHERE salary \> (SELECT avg_sal FROM
avg_salary_cte);

Interview Explanation: A simple CTE is a temporary named result set
defined using WITH clause and used inside a single query for better
readability.

------------------------------------------------------------------------

# 2. Multiple CTE

You can define multiple CTEs separated by commas.

Example:

WITH total_salary AS ( SELECT dept, SUM(salary) AS total_sal FROM
employee GROUP BY dept ), average_salary AS ( SELECT dept, AVG(salary)
AS avg_sal FROM employee GROUP BY dept ) SELECT t.dept, t.total_sal,
a.avg_sal FROM total_salary t JOIN average_salary a ON t.dept = a.dept;

Interview Explanation: Multiple CTEs allow breaking large queries into
smaller logical parts, improving clarity and maintenance.

------------------------------------------------------------------------

# 3. Recursive CTE

Used for hierarchical data like employee-manager structure.

Structure:

WITH RECURSIVE cte_name AS (

    -- Anchor Query
    SELECT columns
    FROM table
    WHERE condition

    UNION ALL

    -- Recursive Query
    SELECT columns
    FROM table
    JOIN cte_name ON condition

) SELECT \* FROM cte_name;

Example: Employee Hierarchy

WITH RECURSIVE emp_hierarchy AS (

    SELECT emp_id, name, manager_id
    FROM employee
    WHERE manager_id IS NULL

    UNION ALL

    SELECT e.emp_id, e.name, e.manager_id
    FROM employee e
    JOIN emp_hierarchy h
    ON e.manager_id = h.emp_id

) SELECT \* FROM emp_hierarchy;

Interview Explanation: Recursive CTE is used to query hierarchical or
tree-structured data. It contains an anchor query and a recursive query
combined using UNION ALL.

------------------------------------------------------------------------

# Important Notes

-   CTE exists only during execution of single query.
-   Cannot create indexes on CTE.
-   Not stored permanently.
-   Improves readability but not always performance.
