# 01_Creating a Table

This document explains the SQL code used to create a basic table called `users` in a relational database and how to query its contents.

## SQL Code Breakdown

```sql
-- Create a new table named 'users'
CREATE TABLE users (
    id INT AUTO_INCREMENT PRIMARY KEY,          -- 'id' is an integer that automatically increments for each new row and is set as the Primary Key (unique identifier)
    
    name VARCHAR(100) NOT NULL,                 -- 'name' is a variable-length string (up to 100 characters) and cannot be NULL (must have a value)
    
    email VARCHAR(100) UNIQUE NOT NULL,         -- 'email' is also a string up to 100 characters; it must be unique (no two users can have the same email), and cannot be NULL
    
    gender ENUM('Male','Female','Other'),       -- 'gender' is a predefined set of possible string values: 'Male', 'Female', or 'Other'
    
    date_of_birth DATE,                         -- 'date_of_birth' stores a date (format: YYYY-MM-DD)
    
    created_id TIMESTAMP DEFAULT CURRENT_TIMESTAMP -- 'created_id' automatically stores the current timestamp when a new row is inserted
);
-- This query creates the structure of the 'users' table with various columns and constraints.

# Viewing a Table

SELECT * FROM users;
-- This query retrieves all columns and all rows from the 'users' table.
-- It's useful for checking the current data stored in the table.

