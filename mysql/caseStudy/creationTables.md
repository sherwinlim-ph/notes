# ENUM

In MySQL, an ENUM (enumeration) is a string data type that lets you define a fixed list of permitted values when creating a table. MySQL restricts column inputs to only the values specified in that list.

1. Defining ENUM in a Table (CREATE TABLE)
You list the allowed values in parentheses after the ENUM keyword:

SQL
CREATE TABLE users (
    id INT AUTO_INCREMENT PRIMARY KEY,
    username VARCHAR(50) NOT NULL,
    role ENUM('admin', 'editor', 'viewer') DEFAULT 'viewer',
    status ENUM('active', 'inactive', 'suspended') NOT NULL
);
2. Inserting Data
When inserting data, you must provide one of the predefined string values.

SQL
-- Valid inserts
INSERT INTO users (username, role, status) 
VALUES ('alice', 'admin', 'active');

INSERT INTO users (username, status) 
VALUES ('bob', 'inactive'); -- 'role' defaults to 'viewer'
Index Insertion (Alternative): You can also insert values using their index position (starting at 1 for the first value). For example, role index 1 is 'admin', 2 is 'editor', etc.

SQL
INSERT INTO users (username, role, status) VALUES ('charlie', 1, 1);
3. Querying ENUM Columns
You query ENUM values just like normal strings:

SQL
-- Select all active admins
SELECT * FROM users 
WHERE role = 'admin' AND status = 'active';
4. Important Rules & Behaviors
Strict Validation: If you try to insert a value that is not in the allowed list (e.g., role = 'superviser'), MySQL will reject it and throw an error (or insert a blank string if strict mode is disabled).

Modifying Allowed Values: You can add or modify choices later using ALTER TABLE:

SQL
ALTER TABLE users MODIFY COLUMN role ENUM('admin', 'editor', 'viewer', 'moderator');
Storage Efficiency: Internally, MySQL stores ENUM values as integer numbers representing their index position, making them efficient for storage and sorting.