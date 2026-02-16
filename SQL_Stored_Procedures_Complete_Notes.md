# SQL Stored Procedures -- Complete Interview Notes

## 1. What is a Stored Procedure?

A Stored Procedure is a pre-written SQL block stored inside the
database.\
It can accept parameters, execute multiple SQL statements, and return
results.

### Advantages:

-   Reusability
-   Better performance (precompiled)
-   Centralized business logic
-   Improved security

------------------------------------------------------------------------

## 2. CREATE PROCEDURE

### Syntax:

DELIMITER //

CREATE PROCEDURE procedure_name() BEGIN SQL statements; END //

DELIMITER ;

### Example:

CREATE PROCEDURE get_all_employees() BEGIN SELECT \* FROM employee; END;

Call using: CALL get_all_employees();

------------------------------------------------------------------------

## 3. Parameters

### IN (Default)

Used to pass input values.

CREATE PROCEDURE get_employee_by_id(IN empid INT) BEGIN SELECT \* FROM
employee WHERE id = empid; END;

### OUT

Used to return value from procedure.

CREATE PROCEDURE get_employee_count(OUT total INT) BEGIN SELECT
COUNT(\*) INTO total FROM employee; END;

### INOUT

Acts as both input and output.

CREATE PROCEDURE increase_salary(INOUT sal DECIMAL(10,2)) BEGIN SET sal
= sal + 5000; END;

------------------------------------------------------------------------

## 4. IF / ELSE

CREATE PROCEDURE check_salary(IN sal INT) BEGIN IF sal \> 60000 THEN
SELECT 'High Salary'; ELSE SELECT 'Normal Salary'; END IF; END;

------------------------------------------------------------------------

## 5. LOOP

DECLARE i INT DEFAULT 1;

loop_label: LOOP IF i \> 5 THEN LEAVE loop_label; END IF; SET i = i + 1;
END LOOP;

------------------------------------------------------------------------

## 6. WHILE

WHILE i \<= 5 DO SET i = i + 1; END WHILE;

------------------------------------------------------------------------

## 7. REPEAT

REPEAT SET i = i + 1; UNTIL i \> 5 END REPEAT;

------------------------------------------------------------------------

## 8. LEAVE

Used to exit a loop (similar to break statement).

------------------------------------------------------------------------

## 9. CURSOR

Used for row-by-row processing.

DECLARE cursor_name CURSOR FOR SELECT column FROM table; OPEN
cursor_name; FETCH cursor_name INTO variable; CLOSE cursor_name;

------------------------------------------------------------------------

## 10. HANDLER

Used for error handling.

DECLARE CONTINUE HANDLER FOR NOT FOUND SET done = TRUE;

Types: - CONTINUE (continue execution) - EXIT (terminate execution)

------------------------------------------------------------------------

## Interview Summary

A Stored Procedure is a precompiled set of SQL statements stored in the
database. It supports parameters (IN, OUT, INOUT), control flow logic
(IF-ELSE, loops), cursors for row-by-row processing, and handlers for
error management. It improves performance, security, and reusability.
