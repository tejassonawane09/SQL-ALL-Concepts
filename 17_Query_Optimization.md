#  Query Optimization

## ✅ What is Query Optimization?

Query Optimization is the process of improving SQL query performance so
that it: - Runs faster - Uses fewer resources - Scans fewer rows - Uses
proper indexes

------------------------------------------------------------------------

# 1️⃣ Query Execution Plan

## What is Execution Plan?

Execution Plan shows how the database executes your query.

It tells: - Which index is used - Join type - Scan type - Estimated
rows - Query cost

### Example:

``` sql
EXPLAIN
SELECT * FROM employee WHERE id = 10;
```

Important execution plan columns: - type → Scan type - key → Index
used - rows → Estimated rows scanned - Extra → Additional info

------------------------------------------------------------------------

# 2️⃣ Full Table Scan

## What is Full Table Scan?

When database reads every row of a table to find matching results.

### When It Happens:

-   No index on filter column
-   Using functions on indexed column
-   Small tables

### Example:

``` sql
SELECT * FROM employee WHERE name = 'Amit';
```

Without index on `name`, database scans entire table.

------------------------------------------------------------------------

# 3️⃣ Index Scan

## What is Index Scan?

Database uses index structure to quickly locate rows instead of scanning
entire table.

### Example:

``` sql
CREATE INDEX idx_emp_id ON employee(id);

SELECT * FROM employee WHERE id = 10;
```

Types: - Index Seek (Fastest) - Index Range Scan - Index Full Scan

------------------------------------------------------------------------

# 4️⃣ Optimization Techniques

## 1. Create Proper Indexes

-   Index frequently filtered columns
-   Index join columns
-   Index ORDER BY columns

Avoid indexing: - Low uniqueness columns - Frequently updated columns

## 2. Avoid SELECT \*

Select only required columns.

## 3. Filter Early Using WHERE

Reduce dataset before joins.

## 4. Avoid Functions on Indexed Columns

Bad:

``` sql
WHERE YEAR(join_date) = 2024;
```

Better:

``` sql
WHERE join_date BETWEEN '2024-01-01' AND '2024-12-31';
```

## 5. Use EXISTS Instead of IN (for large data)

## 6. Use LIMIT for large result sets

## 7. Use Covering Index

Index contains all columns needed for query.

------------------------------------------------------------------------

# 5️⃣ Performance Tuning

Performance tuning includes: 1. Identify slow queries 2. Run EXPLAIN 3.
Check scan type 4. Add proper index 5. Rewrite inefficient queries 6.
Retest performance

------------------------------------------------------------------------

# 🔹 Common Performance Problems

-   Missing index
-   Full table scan
-   Too many joins
-   Poor filtering
-   Large dataset
-   Subqueries instead of joins

------------------------------------------------------------------------

# 🔹 Full Table Scan vs Index Scan

  Full Table Scan         Index Scan
  ----------------------- --------------------------
  1] Reads all rows,          Reads matching rows only
  2] Slow on large tables,    Faster
  3] Happens without index,   Requires index

------------------------------------------------------------------------

# 🔹 Final Summary

Query optimization improves performance by reducing unnecessary data
scans. Execution plans help analyze query behavior. Proper indexing,
filtering early, avoiding SELECT \*, and rewriting inefficient queries
are key techniques for performance tuning.
