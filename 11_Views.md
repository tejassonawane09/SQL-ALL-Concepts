# 🔹 11. Views in SQL 

------------------------------------------------------------------------

## ✅ What is a View?

A View is a virtual table created using a SELECT query.

Important: - A view does NOT store data physically. - It stores only the
query. - When you query a view, it runs the underlying SELECT statement.

------------------------------------------------------------------------

## 🔹 View vs Table

  View                      Table
  ------------------------- ----------------------
  Virtual                   Physical
  Stores query only         Stores data
  No storage                Uses storage
  Reflects real-time data   Data stored directly

------------------------------------------------------------------------

# 1️⃣ CREATE VIEW

## Syntax

``` sql
CREATE VIEW view_name AS
SELECT column1, column2
FROM table
WHERE condition;
```

## Example

``` sql
CREATE VIEW it_employees AS
SELECT id, name, salary
FROM employee
WHERE dept = 'IT';
```

Now use:

``` sql
SELECT * FROM it_employees;
```

### Why Use It?

-   Simplifies repeated queries
-   Improves readability
-   Used in reporting layer

------------------------------------------------------------------------

# 2️⃣ Updatable Views

## What is an Updatable View?

An updatable view allows: - INSERT - UPDATE - DELETE

operations through the view.

## Conditions for Updatable View

✔ Based on single table\
✔ No GROUP BY\
✔ No aggregate functions\
✔ No DISTINCT\
✔ No JOIN\
✔ No UNION

## Example

``` sql
CREATE VIEW hr_employees AS
SELECT id, name, salary, dept
FROM employee
WHERE dept = 'HR';
```

Update through view:

``` sql
UPDATE hr_employees
SET salary = 65000
WHERE id = 2;
```

This updates the original employee table.

------------------------------------------------------------------------

# 3️⃣ WITH CHECK OPTION

## What is WITH CHECK OPTION?

Ensures that inserted or updated rows satisfy the view condition.

## Without CHECK OPTION

``` sql
CREATE VIEW it_employees AS
SELECT *
FROM employee
WHERE dept = 'IT';
```

You can insert non-IT data, but it won't appear in the view.

## With CHECK OPTION

``` sql
CREATE VIEW it_employees AS
SELECT *
FROM employee
WHERE dept = 'IT'
WITH CHECK OPTION;
```

Now inserting non-IT data will give an error.

------------------------------------------------------------------------

# 🔹 Advantages of Views

1.  Improve security
2.  Simplify complex queries
3.  Hide sensitive columns
4.  Provide abstraction layer

------------------------------------------------------------------------

# 🔹 Disadvantages of Views

1.  Can reduce performance in complex cases
2.  Cannot index normal views (except materialized views)
3.  Not ideal for heavy aggregations

------------------------------------------------------------------------

# 🎯 Summary Answer

A view is a virtual table created using a SELECT statement. It does not
store data physically but retrieves data dynamically from underlying
tables. A view is updatable if it is based on a single table without
joins or aggregates. WITH CHECK OPTION ensures that modifications
through the view satisfy its filtering condition.
