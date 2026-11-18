# basic guide
1. Database & Table Management (DDL)Create a database:SQLCREATE DATABASE my_database;

USE my_database;

Create a table:SQLCREATE TABLE users (
    id INT AUTO_INCREMENT PRIMARY KEY,
    username VARCHAR(50) NOT NULL UNIQUE,
    email VARCHAR(100),
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

Modify a table (ALTER):SQLALTER TABLE users ADD COLUMN age INT;

ALTER TABLE users DROP COLUMN age;

Delete a table or database:SQLDROP TABLE users;

DROP DATABASE my_database;

2. Data Manipulation (DML - CRUD)Insert data:SQLINSERT INTO users (username, email) VALUES ('johndoe', 'john@example.com');

Select (Read) data:SQLSELECT username, email FROM users WHERE id = 1;
Update data:SQLUPDATE users SET email = 'newemail@example.com' WHERE username = 'johndoe';
Delete data:SQLDELETE FROM users WHERE id = 1;

3. Querying & FilteringFiltering (WHERE, AND, OR, LIKE):SQLSELECT * FROM users 
WHERE age > 21 AND (status = 'active' OR role = 'admin');

-- Wildcard matching
SELECT * FROM users WHERE email LIKE '%@gmail.com';
Sorting (ORDER BY) & Limiting:SQLSELECT * FROM products 
ORDER BY price DESC 
LIMIT 10 OFFSET 0;
Grouping & Aggregation (GROUP BY, HAVING):SQLSELECT department, COUNT(*) AS employee_count 
FROM employees 
GROUP BY department 
HAVING employee_count > 5;

4. Joins (Combining Tables)INNER JOIN (Matches records in both tables):SQLSELECT users.username, orders.order_date 
FROM users
INNER JOIN orders ON users.id = orders.user_id;
LEFT JOIN (All records from left table, matched from right):SQLSELECT users.username, orders.order_date 
FROM users
LEFT JOIN orders ON users.id = orders.user_id;

5. Useful MySQL Functions & ClausesString functions: CONCAT(first, ' ', last), UPPER(str), LOWER(str), LENGTH(str)Date functions: NOW(), CURDATE(), DATE_FORMAT(date, '%Y-%m-%d')Handling NULLs (COALESCE):SQLSELECT COALESCE(phone_number, 'No Phone Provided') FROM users;

# list of commands

Core Query Structure Order
SELECT

FROM

WHERE

GROUP BY

HAVING

ORDER BY

LIMIT

SELECT Commands & Modifiers
SELECT *

SELECT column_name

SELECT DISTINCT

AS (Column aliases)

FROM Commands
FROM table_name

JOIN / INNER JOIN

LEFT JOIN

RIGHT JOIN

WHERE Operators & Conditions
= (Equals)

!= or <> (Not equals)

> (Greater than)

< (Less than)

>= (Greater than or equal to)

<= (Less than or equal to)

AND

OR

NOT

IN (...)

BETWEEN ... AND ...

LIKE '%pattern%'

IS NULL

IS NOT NULL