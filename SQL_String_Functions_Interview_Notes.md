
# SQL String Functions – Interview Ready Notes

## 1. CONCAT()
Used to combine two or more strings.

Example:
SELECT CONCAT(name, ' - ', city) FROM users;

Interview Explanation:
CONCAT joins multiple strings into one single string.

---

## 2. SUBSTRING()
Extracts part of a string.

Syntax:
SUBSTRING(column, start_position, length)

Example:
SELECT SUBSTRING(name, 1, 5) FROM users;

Interview Explanation:
SUBSTRING extracts specific portion of a string.

---

## 3. SUBSTRING_INDEX() (MySQL)
Extracts substring based on delimiter.

Example:
SELECT SUBSTRING_INDEX(email, '@', -1) FROM users;

Interview Explanation:
Used to extract part of string before or after delimiter.

---

## 4. LEFT() / RIGHT()
Extract characters from beginning or end.

Example:
SELECT LEFT(name, 3) FROM users;
SELECT RIGHT(email, 4) FROM users;

Interview Explanation:
LEFT and RIGHT extract characters from start or end of string.

---

## 5. TRIM() / LTRIM() / RTRIM()
Remove extra spaces.

Example:
SELECT TRIM('   Tejas   ');

Interview Explanation:
Used to clean unnecessary spaces from text data.

---

## 6. REPLACE()
Replace substring with another substring.

Example:
SELECT REPLACE(email, 'gmail.com', 'outlook.com') FROM users;

Interview Explanation:
Replaces all occurrences of a substring.

---

## 7. LOWER() / UPPER()
Convert text case.

Example:
SELECT LOWER(name), UPPER(city) FROM users;

Interview Explanation:
Used for text standardization.

---

## 8. LENGTH()
Returns number of characters in string.

Example:
SELECT LENGTH(name) FROM users;

Interview Explanation:
Returns total number of characters in text.

---

## 9. LOCATE()
Finds position of substring.

Example:
SELECT LOCATE('@', email) FROM users;

Interview Explanation:
Returns position of substring within string.

---

## 10. FORMAT()
Formats numeric value.

Example:
SELECT FORMAT(1234567.89, 2);

Interview Explanation:
Used to format numbers with decimal and comma separator.

---

## 11. LPAD() / RPAD()
Pads string to specific length.

Example:
SELECT LPAD(name, 10, '*') FROM users;
SELECT RPAD(name, 10, '*') FROM users;

Interview Explanation:
Adds characters to left or right side of string.

---

## 12. REGEXP
Advanced pattern matching.

Example:
SELECT * FROM users WHERE email REGEXP '\\.com$';

Interview Explanation:
REGEXP allows advanced pattern matching using regular expressions.
