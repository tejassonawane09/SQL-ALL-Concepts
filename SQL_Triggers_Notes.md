# 🔹 15. TRIGGERS IN SQL

## ✅ What is a Trigger?

A Trigger is a database object that automatically executes when a
specific event (INSERT, UPDATE, DELETE) occurs on a table.

It runs automatically --- no manual call required.

------------------------------------------------------------------------

## 🔹 Basic Syntax

``` sql
DELIMITER //

CREATE TRIGGER trigger_name
BEFORE/AFTER INSERT/UPDATE/DELETE
ON table_name
FOR EACH ROW
BEGIN
    SQL logic;
END //

DELIMITER ;
```

------------------------------------------------------------------------

# 1️⃣ BEFORE INSERT

### Purpose:

-   Validation
-   Modify values before insertion

### Example:

``` sql
CREATE TRIGGER before_insert_employee
BEFORE INSERT ON employee
FOR EACH ROW
BEGIN
    IF NEW.salary < 0 THEN
        SET NEW.salary = 0;
    END IF;
END;
```

👉 `NEW` refers to the new row being inserted.

------------------------------------------------------------------------

# 2️⃣ AFTER INSERT

### Purpose:

-   Logging
-   Audit tracking

### Example:

``` sql
CREATE TRIGGER after_insert_employee
AFTER INSERT ON employee
FOR EACH ROW
BEGIN
    INSERT INTO employee_log(message)
    VALUES(CONCAT('New employee added: ', NEW.name));
END;
```

------------------------------------------------------------------------

# 3️⃣ BEFORE UPDATE

### Purpose:

-   Validate updates
-   Restrict changes

### Example:

``` sql
CREATE TRIGGER before_update_salary
BEFORE UPDATE ON employee
FOR EACH ROW
BEGIN
    IF NEW.salary < OLD.salary THEN
        SET NEW.salary = OLD.salary;
    END IF;
END;
```

👉 `OLD` = Previous value\
👉 `NEW` = Updated value

------------------------------------------------------------------------

# 4️⃣ AFTER UPDATE

### Purpose:

-   Maintain history
-   Track changes

### Example:

``` sql
CREATE TRIGGER after_update_salary
AFTER UPDATE ON employee
FOR EACH ROW
BEGIN
    INSERT INTO salary_history(emp_id, old_salary, new_salary)
    VALUES(OLD.id, OLD.salary, NEW.salary);
END;
```

------------------------------------------------------------------------

# 5️⃣ BEFORE DELETE

### Purpose:

-   Prevent unauthorized deletion

### Example:

``` sql
CREATE TRIGGER before_delete_employee
BEFORE DELETE ON employee
FOR EACH ROW
BEGIN
    IF OLD.salary > 100000 THEN
        SIGNAL SQLSTATE '45000'
        SET MESSAGE_TEXT = 'Cannot delete high salary employee';
    END IF;
END;
```

------------------------------------------------------------------------

# 6️⃣ AFTER DELETE

### Purpose:

-   Archive deleted records

### Example:

``` sql
CREATE TRIGGER after_delete_employee
AFTER DELETE ON employee
FOR EACH ROW
BEGIN
    INSERT INTO deleted_employees(emp_id, name)
    VALUES(OLD.id, OLD.name);
END;
```

------------------------------------------------------------------------

# 🔹 OLD vs NEW Keywords

  Keyword   Meaning
  --------- ----------------------------------------
  NEW       New inserted or updated value
  OLD       Previous value before update or delete

------------------------------------------------------------------------

# 🔹 Interview Summary

A trigger is a database object that automatically executes in response
to INSERT, UPDATE, or DELETE operations on a table.\
Triggers can run BEFORE or AFTER an event and are mainly used for
validation, logging, enforcing business rules, and maintaining data
integrity.
