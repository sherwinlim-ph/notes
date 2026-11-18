# basic queries

When we talk about "queries" in SQL, we are talking about asking the database for information. The most common tool for this is the SELECT statement.

Think of a query like asking a librarian to fetch specific books for you.

1. The Most Basic Query: Getting Everything
If you want to look at every single column and every single row inside your products table, you use the asterisk (*), which means "all":

SQL
SELECT * FROM products;
SELECT: "I want to retrieve data."

*: "Give me all columns."

FROM products: "Look inside the products table."

2. Picking Specific Columns
Usually, you don't need every piece of information. If you only want to see the names and prices of your items, you list the column names instead of using *:

SQL
SELECT product_name, product_price FROM products;
3. Filtering Data with WHERE
What if you only want to see items that belong to a specific category, like just the coffees? You use the WHERE clause to filter your results:

SQL
SELECT * FROM products 
WHERE product_category = 'Coffee';
You can also filter by numbers. For example, if you want to find items that cost less than $5.00:

SQL
SELECT product_name, product_price 
FROM products 
WHERE product_price < 5.00;
Putting Data In First (INSERT)
Before you can query data, the table needs to have some rows in it. Here is how you add a row using INSERT INTO:

SQL
INSERT INTO products (product_name, product_category, product_price) 
VALUES ('Caramel Macchiato', 'Coffee', 4.75);