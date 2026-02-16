# SQL Date Functions 

## 1. NOW()

Returns current date and time.

Example: SELECT NOW();

Interview Point: NOW() returns the current system date and time.

------------------------------------------------------------------------

## 2. CURDATE()

Returns current date only (without time).

Example: SELECT CURDATE();

Difference: NOW() → Date + Time\
CURDATE() → Date only

------------------------------------------------------------------------

## 3. DATE_ADD()

Adds interval to a date.

Syntax: DATE_ADD(date, INTERVAL value unit)

Example: SELECT DATE_ADD(order_date, INTERVAL 7 DAY) FROM orders;

Business Use: Used to calculate expiry dates, renewal dates, delivery
deadlines.

------------------------------------------------------------------------

## 4. DATE_SUB()

Subtracts interval from a date.

Example: SELECT DATE_SUB(order_date, INTERVAL 30 DAY);

Used for: Finding records from last 30 days.

------------------------------------------------------------------------

## 5. DATEDIFF()

Returns difference in days between two dates.

Syntax: DATEDIFF(date1, date2)

Example: SELECT DATEDIFF(delivery_date, order_date) FROM orders;

Interview Point: DATEDIFF always returns difference in DAYS.

------------------------------------------------------------------------

## 6. TIMESTAMPDIFF()

Returns difference between two dates in specified unit.

Syntax: TIMESTAMPDIFF(unit, date1, date2)

Example: SELECT TIMESTAMPDIFF(YEAR, '1998-05-10', CURDATE());

Units: YEAR, MONTH, DAY, HOUR, MINUTE

Interview Point: More flexible than DATEDIFF.

------------------------------------------------------------------------

## 7. YEAR()

Extracts year from date.

Example: SELECT YEAR(order_date) FROM orders;

Used in: Year-wise sales reports.

------------------------------------------------------------------------

## 8. MONTH()

Extracts month from date.

Example: SELECT MONTH(order_date) FROM orders;

Used in: Monthly analysis.

------------------------------------------------------------------------

## 9. DAY()

Extracts day from date.

Example: SELECT DAY(order_date) FROM orders;

------------------------------------------------------------------------

# Common Interview Questions

1.  Difference between DATEDIFF and TIMESTAMPDIFF?

    -   DATEDIFF → Only days
    -   TIMESTAMPDIFF → Multiple units

2.  How to get last 7 days data? SELECT \* FROM orders WHERE order_date
    \>= DATE_SUB(CURDATE(), INTERVAL 7 DAY);

3.  How to calculate delivery time? SELECT DATEDIFF(delivery_date,
    order_date) FROM orders;

------------------------------------------------------------------------

# Final Summary

Date functions are used to manipulate and analyze time-based data. They
help in filtering recent records, calculating durations, extracting date
parts, and building time-based reports.
