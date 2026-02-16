# Transactions in SQL

## ✅ What is a Transaction?

A transaction is a group of SQL operations executed as a single logical
unit of work.\
Either all operations succeed or all fail. There is no partial
completion.

Example: Bank transfer (Debit + Credit must both succeed).

------------------------------------------------------------------------

# 🔹 Transaction Control Commands

## 1️⃣ START TRANSACTION

Begins a transaction block.

``` sql
START TRANSACTION;
```

Changes are temporary until committed.

------------------------------------------------------------------------

## 2️⃣ COMMIT

Permanently saves all changes made during the transaction.

``` sql
COMMIT;
```

After commit, changes cannot be undone.

------------------------------------------------------------------------

## 3️⃣ ROLLBACK

Undo all changes made since START TRANSACTION.

``` sql
ROLLBACK;
```

Restores database to previous consistent state.

------------------------------------------------------------------------

## 4️⃣ SAVEPOINT

Creates a checkpoint inside a transaction for partial rollback.

``` sql
SAVEPOINT sp1;
ROLLBACK TO sp1;
```

Allows undoing part of a transaction instead of entire transaction.

------------------------------------------------------------------------

# 🔹 ACID Properties

## A --- Atomicity

All operations succeed or none succeed.

## C --- Consistency

Database moves from one valid state to another valid state.

## I --- Isolation

Transactions do not interfere with each other.

## D --- Durability

Once committed, data remains permanent even after system failure.

------------------------------------------------------------------------

# 🔹 Transaction States

1.  Active -- Transaction running
2.  Partially Committed -- Last statement executed
3.  Committed -- Changes saved permanently
4.  Failed -- Error occurred
5.  Aborted -- Rolled back

------------------------------------------------------------------------

# 🔹 Isolation Levels

## 1️⃣ READ UNCOMMITTED

Allows dirty reads.

## 2️⃣ READ COMMITTED

Prevents dirty reads.

## 3️⃣ REPEATABLE READ

Prevents dirty reads and non-repeatable reads.

## 4️⃣ SERIALIZABLE

Highest isolation. Prevents dirty, non-repeatable, and phantom reads.

------------------------------------------------------------------------

# 🔹 Common Transaction Problems

Dirty Read -- Reading uncommitted data\
Non-Repeatable Read -- Same query gives different results\
Phantom Read -- New rows appear during transaction

------------------------------------------------------------------------

# 🔹 Interview Summary

A transaction ensures reliable data processing using ACID properties.\
START TRANSACTION begins it, COMMIT saves changes, ROLLBACK cancels
changes, and SAVEPOINT allows partial rollback.\
Isolation levels control how concurrent transactions interact.
