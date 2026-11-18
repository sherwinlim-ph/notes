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

Data Definition Language (DDL) — Table & Database Structure
CREATE DATABASE

DROP DATABASE

CREATE TABLE

ALTER TABLE

DROP TABLE

TRUNCATE TABLE

Data Manipulation Language (DML) — Managing Data
INSERT INTO

UPDATE

DELETE FROM

Aggregate Functions (Used with SELECT or GROUP BY)
COUNT()

SUM()

AVG()

MAX()

MIN()

Advanced Keywords & Operators
UNION / UNION ALL

EXISTS / NOT EXISTS

CASE WHEN ... THEN ... ELSE ... END

AS (Table or column aliases)

DISTINCT

# list of commands when creating a tables

Common Data Types
INT / BIGINT (Whole numbers)

VARCHAR(n) (Variable-length text)

TEXT (Long text)

DECIMAL(p, s) (Exact decimals/currency)

DATE / DATETIME / TIMESTAMP (Dates and times)

BOOLEAN / ENUM('val1', 'val2') (Booleans and choices)

Column Constraints
PRIMARY KEY (Uniquely identifies rows)

AUTO_INCREMENT (Auto-increments integers)

NOT NULL (Disallows empty values)

UNIQUE (Ensures all values are distinct)

DEFAULT value (Fallback value if none specified)

CHECK (condition) (Validates input data)

FOREIGN KEY (column_name) REFERENCES parent_table(parent_column)
    ON DELETE CASCADE / SET NULL / RESTRICT
    ON UPDATE CASCADE / RESTRICT

INDEX idx_name (column_name)
UNIQUE INDEX idx_name (column_name)

ENGINE=InnoDB
DEFAULT CHARSET=utf8mb4
COLLATE=utf8mb4_unicode_ci