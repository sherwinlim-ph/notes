# creating tables

To create a table in MySQL, you use the CREATE TABLE statement. This defines the table's name, its columns, the data type for each column, and any rules or constraints (such as primary keys).

Basic Syntax
SQL
CREATE TABLE table_name (
    column1 datatype constraints,
    column2 datatype constraints,
    column3 datatype constraints,
    ...
);
Step-by-Step Example
Here is a practical example for creating a table named users to store customer information:

SQL
CREATE TABLE users (
    user_id INT AUTO_INCREMENT PRIMARY KEY,
    username VARCHAR(50) NOT NULL UNIQUE,
    email VARCHAR(100) NOT NULL,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
What each part means:
user_id INT AUTO_INCREMENT PRIMARY KEY: Creates an integer column that automatically increments by 1 for every new row, serving as the unique identifier (Primary Key) for each user.

username VARCHAR(50) NOT NULL UNIQUE: Stores text up to 50 characters long. NOT NULL means it cannot be left blank, and UNIQUE ensures no two users can have the same username.

email VARCHAR(100) NOT NULL: Stores the user's email address and requires it to be provided.

created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP: Automatically records the exact date and time when the row is created if no custom timestamp is supplied.

Helpful Best Practices
Check if the table exists: To avoid errors if a table with the same name already exists, you can add IF NOT EXISTS:

SQL
CREATE TABLE IF NOT EXISTS users (
    ...
);
Choose the right data types: Use INT for whole numbers, VARCHAR(n) for variable-length text, DECIMAL for currency/prices, and DATETIME or TIMESTAMP for dates and times.

Always define a Primary Key: Every table should typically have a primary key column to uniquely identify each record.

# if-not exists

For databases, it is CREATE DATABASE IF NOT EXISTS (not IF DATABASE NOT EXISTS).

For tables, it is CREATE TABLE IF NOT EXISTS (putting IF NOT EXISTS right after CREATE TABLE).

Here is the corrected version:

SQL
CREATE DATABASE IF NOT EXISTS products;

USE products;

CREATE TABLE IF NOT EXISTS products (
    product_id INT AUTO_INCREMENT PRIMARY KEY,
    product_name VARCHAR(100) NOT NULL,
    product_category VARCHAR(50) NOT NULL,
    product_price DECIMAL(5, 2) NOT NULL,
    added_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);


# 