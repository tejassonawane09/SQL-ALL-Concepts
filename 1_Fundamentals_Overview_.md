# SQL Fundamentals

## 1. SQL Overview

SQL (Structured Query Language) is used to communicate with relational
databases.

It is used to: - Store data - Retrieve data - Update data - Delete
data - Control access to data

### Interview Answer:

SQL is a structured query language used to store, manage, and retrieve
data from relational databases. It allows operations like selecting
data, inserting records, updating values, deleting records, and managing
database structure.

------------------------------------------------------------------------

## 2. Database vs DBMS vs RDBMS

### Database

An organized collection of data.

### DBMS

Software used to manage databases. Examples: MySQL, Oracle, SQL Server.

### RDBMS

Advanced version of DBMS. - Stores data in tables (rows and columns) -
Maintains relationships using primary and foreign keys - Ensures data
integrity

### Difference Table

  Feature         DBMS            RDBMS
  --------------- --------------- -----------------------------
  Structure       File-based      Table-based
  Relationships   Not mandatory   Enforced
  Keys            Not required    Uses Primary & Foreign keys
  Normalization   No              Yes

------------------------------------------------------------------------

## 3. Data Types in SQL

### Numeric

-   INT
-   BIGINT
-   DECIMAL(p,s)
-   FLOAT

### String

-   CHAR(n)
-   VARCHAR(n)
-   TEXT

### Date & Time

-   DATE
-   TIME
-   DATETIME
-   TIMESTAMP

### Boolean

-   TRUE / FALSE

------------------------------------------------------------------------

## 4. Constraints

Constraints maintain data integrity.

### NOT NULL

Ensures column cannot store NULL.

### UNIQUE

Ensures all values are different.

### PRIMARY KEY

-   Uniquely identifies each row
-   Cannot be NULL
-   Only one per table

### FOREIGN KEY

-   Creates relationship between tables
-   References primary key of another table

### CHECK

Applies condition on column values.

### DEFAULT

Sets default value if no value is provided.

------------------------------------------------------------------------

## 5. DDL Commands (Data Definition Language)

### CREATE

Creates table or database.

### ALTER

Modifies existing table structure.

### DROP

Deletes table permanently.

### TRUNCATE

Deletes all rows but keeps structure.

------------------------------------------------------------------------

## 6. DML Commands (Data Manipulation Language)

### INSERT

Adds new records.

### SELECT

Retrieves data.

### UPDATE

Modifies existing records.

### DELETE

Removes records.

------------------------------------------------------------------------

## 7. DCL Commands (Data Control Language)

### GRANT

Gives access permissions.

### REVOKE

Removes access permissions.

------------------------------------------------------------------------

## 8. TCL Commands (Transaction Control Language)

### COMMIT

Saves changes permanently.

### ROLLBACK

Undoes changes before commit.

### SAVEPOINT

Creates temporary rollback point.

------------------------------------------------------------------------

# Final Interview Summary

SQL is a language used to interact with relational databases.\
It includes: - DDL for defining structure - DML for manipulating data -
DCL for controlling access - TCL for managing transactions

Constraints and proper data types ensure data integrity and performance.
