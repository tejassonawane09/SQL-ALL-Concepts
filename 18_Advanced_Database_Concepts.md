# Advanced Database Concepts

## 1️⃣ Normalization

Normalization is the process of organizing data in a database to: -
Reduce redundancy - Avoid duplication - Maintain data consistency -
Improve data integrity

### Normal Forms

-   **1NF**: Atomic values, no repeating groups
-   **2NF**: No partial dependency
-   **3NF**: No transitive dependency

**Interview Answer:**\
Normalization organizes tables to eliminate redundancy and ensure data
integrity.

------------------------------------------------------------------------

## 2️⃣ Denormalization

Denormalization intentionally adds redundancy to improve read
performance and reduce joins.

**Interview Answer:**\
Denormalization improves query performance by reducing joins at the cost
of controlled redundancy.

------------------------------------------------------------------------

## 3️⃣ Locks

Locks control concurrent access to data.

### Types of Locks

-   **Shared Lock (Read Lock)** -- Multiple reads allowed
-   **Exclusive Lock (Write Lock)** -- Only one write allowed
-   **Row-Level Lock** -- Locks specific row
-   **Table-Level Lock** -- Locks entire table

**Interview Answer:**\
Locks prevent data conflicts in multi-user environments.

------------------------------------------------------------------------

## 4️⃣ Deadlock

Deadlock occurs when two transactions wait for each other indefinitely
due to locked resources.

**Interview Answer:**\
A deadlock happens when transactions block each other in a circular wait
situation.

------------------------------------------------------------------------

## 5️⃣ Isolation Levels

Isolation levels control visibility of transaction changes.

  Level              Dirty Read   Non-Repeatable Read   Phantom Read
  ------------------ ------------ --------------------- --------------
  Read Uncommitted   Yes          Yes                   Yes
  Read Committed     No           Yes                   Yes
  Repeatable Read    No           No                    Yes
  Serializable       No           No                    No

------------------------------------------------------------------------

## 6️⃣ ACID vs BASE

### ACID (Relational Databases)

-   Atomicity
-   Consistency
-   Isolation
-   Durability

Used in banking and financial systems.

### BASE (NoSQL Systems)

-   Basically Available
-   Soft State
-   Eventual Consistency

Used in distributed and scalable systems.

  ACID                   BASE
  ---------------------- -----------------------
  Strong consistency     Eventual consistency
  Used in RDBMS          Used in NoSQL
  Focus on correctness   Focus on availability

------------------------------------------------------------------------

## Final Summary

Advanced database concepts include normalization for data integrity,
denormalization for performance, locking mechanisms for concurrency
control, deadlock handling, isolation levels to prevent anomalies, and
ACID vs BASE principles for system reliability models.
