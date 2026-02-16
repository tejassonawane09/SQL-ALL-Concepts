# 🔹 14. User Defined Functions (UDF) in SQL

## ✅ What is a User Defined Function (UDF)?

A User Defined Function is a custom function created by the user inside
the database.

It: - Accepts input parameters - Returns a single value - Can be used
inside SELECT statements - Helps reuse business logic

Think of it like a reusable calculation block inside the database.

------------------------------------------------------------------------

## 🔹 Difference Between Function and Stored Procedure

  Function                          Stored Procedure
  --------------------------------- -----------------------
  Must return a value               May or may not return
  Used inside SELECT                Called using CALL
  Cannot modify table (generally)   Can modify tables
  Used for calculations             Used for operations

------------------------------------------------------------------------

# 1️⃣ CREATE FUNCTION

## ✅ Basic Syntax

``` sql
DELIMITER //

CREATE FUNCTION function_name(parameters)
RETURNS return_type
BEGIN
    SQL logic;
    RETURN value;
END //

DELIMITER ;
```

------------------------------------------------------------------------

## 🔹 Example 1: Calculate Bonus (10%)

``` sql
DELIMITER //

CREATE FUNCTION calculate_bonus(salary DECIMAL(10,2))
RETURNS DECIMAL(10,2)
BEGIN
    RETURN salary * 0.10;
END //

DELIMITER ;
```

### Usage:

``` sql
SELECT name, salary, calculate_bonus(salary)
FROM employee;
```

------------------------------------------------------------------------

## 🔹 Example 2: Calculate Age

``` sql
DELIMITER //

CREATE FUNCTION calculate_age(dob DATE)
RETURNS INT
BEGIN
    RETURN TIMESTAMPDIFF(YEAR, dob, CURDATE());
END //

DELIMITER ;
```

------------------------------------------------------------------------

# 2️⃣ Deterministic Functions

## ✅ What is Deterministic Function?

A deterministic function always returns the same output for the same
input.

Example:

``` sql
calculate_bonus(50000)
```

Always returns the same result.

------------------------------------------------------------------------

## 🔹 Non-Deterministic Function

Returns different output for same input.

Examples: - NOW() - RAND() - CURDATE()

------------------------------------------------------------------------

## 🔹 Declaring Deterministic Function

``` sql
CREATE FUNCTION calculate_bonus(salary DECIMAL(10,2))
RETURNS DECIMAL(10,2)
DETERMINISTIC
BEGIN
    RETURN salary * 0.10;
END;
```

------------------------------------------------------------------------

# 🔹 Business Logic Example

``` sql
DELIMITER //

CREATE FUNCTION calculate_bonus(salary DECIMAL(10,2))
RETURNS DECIMAL(10,2)
DETERMINISTIC
BEGIN
    DECLARE bonus DECIMAL(10,2);

    IF salary > 60000 THEN
        SET bonus = salary * 0.20;
    ELSE
        SET bonus = salary * 0.10;
    END IF;

    RETURN bonus;
END //

DELIMITER ;
```

------------------------------------------------------------------------

# 🔹 Advantages

-   Reusable logic
-   Cleaner queries
-   Centralized business rules
-   Modular design

------------------------------------------------------------------------

# 🔹 Interview Summary Answer

A user-defined function is a reusable SQL block that returns a single
value. It accepts parameters and is used inside queries for
calculations. Deterministic functions always return the same result for
the same input, while non-deterministic functions may return different
outputs.
