# 🔹 12. Indexing in SQL

## 📌 What is an Index?

An Index is a data structure that improves the speed of data retrieval
operations on a table.\
It works like a book index --- instead of scanning the entire table, the
database can directly locate required rows.

------------------------------------------------------------------------

## 🔹 Types of Indexes

### 1️⃣ Clustered Index

-   Determines the physical order of data in a table.
-   Only ONE clustered index per table.
-   Usually created automatically on Primary Key.

**Interview Point:**\
A clustered index defines the physical storage order of data in a table.

------------------------------------------------------------------------

### 2️⃣ Non-Clustered Index

-   Does NOT change physical data order.
-   Creates a separate lookup structure with pointers to actual rows.
-   Multiple non-clustered indexes allowed.

**Interview Point:**\
A non-clustered index creates a separate structure for fast lookup
without changing table order.

------------------------------------------------------------------------

### 3️⃣ Composite Index

-   Index on multiple columns.
-   Follows the left-most prefix rule.

Example: If index is on (dept, salary): - Query using dept → Uses index\
- Query using dept and salary → Uses index\
- Query using salary only → May not use index

------------------------------------------------------------------------

### 4️⃣ Unique Index

-   Ensures all values are unique.
-   Prevents duplicate entries.
-   Primary Key automatically creates unique index.

------------------------------------------------------------------------

### 5️⃣ Covering Index

-   Index contains all columns required by a query.
-   No need to access base table.
-   Improves performance significantly.

------------------------------------------------------------------------

## 🔹 Index Optimization

### ✅ When to Create Index

-   Frequently searched columns
-   WHERE clause columns
-   JOIN columns
-   ORDER BY columns

### ❌ When Not to Create Index

-   Small tables
-   Frequently updated columns
-   Low selectivity columns (e.g., Gender)

------------------------------------------------------------------------

## 🔹 EXPLAIN

Displays query execution plan.

Helps identify: - Whether index is used - Scan type - Estimated rows
scanned

------------------------------------------------------------------------

## 🔹 EXPLAIN ANALYZE

-   Executes the query
-   Shows actual runtime statistics
-   More accurate than EXPLAIN

------------------------------------------------------------------------

## 🔹 EXPLAIN FORMAT=JSON

-   Shows execution plan in JSON format
-   Used for detailed performance debugging

------------------------------------------------------------------------

## 🎯 Final Summary

Indexing improves query performance by reducing data scan time.\
Clustered index controls physical order of data, while non-clustered
index creates a separate lookup structure.\
Composite, unique, and covering indexes help optimize complex queries.\
EXPLAIN and EXPLAIN ANALYZE are used to evaluate query performance.
