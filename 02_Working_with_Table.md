# Working with Tables in MySQL

This guide explains how to perform basic table operations in MySQL, such as selecting data, renaming tables, and altering table structures. Each SQL command is documented with in-line comments for clarity.

---

## Selecting Data from a Table

### Select All Columns

```sql
-- This query selects all columns and rows from the 'users' table
SELECT * FROM users;
```
### Select Specific Columns

``` sql
-- This query selects only the 'name' and 'email' columns from all rows in the 'users' table
SELECT name, email FROM users;
```
<hr>

## Renaming a Table

### Rename an Existing Table

```sql 
-- This renames the 'users' table to 'customers'
RENAME TABLE users TO customers;
```
### Rename it Back

```sql
-- This renames the 'customers' table back to 'users'
RENAME TABLE customers TO users;
```
<hr>

## Altering a Table

The ALTER TABLE statement allows modification of an existing table.

### Add a Column

```sql
-- Adds a new column 'is_active' with a BOOLEAN data type and a default value of TRUE
ALTER TABLE users ADD COLUMN is_active BOOLEAN DEFAULT TRUE;
```
### Drop a Column

```sql
-- Removes the 'is_active' column from the 'users' table
ALTER TABLE users DROP COLUMN is_active;
```

### Modify a Column Type

```sql
-- Changes the data type of the 'name' column to VARCHAR with a maximum length of 150 characters
ALTER TABLE users MODIFY COLUMN name VARCHAR(150);
```

### Move a Column to the First Position

```sql
-- Moves the 'email' column to the first position in the 'users' table
-- Also changes its data type to VARCHAR(100)
ALTER TABLE users MODIFY COLUMN email VARCHAR(100) FIRST;
```
### Move a Column After Another Column

```sql
-- Moves the 'gender' column to come immediately after the 'name' column
-- Also modifies it to be an ENUM type with three allowed values
ALTER TABLE users MODIFY COLUMN gender ENUM('Male', 'Female', 'Other') AFTER name;
```

<hr>

### Summary

<ul>
<h4> These commands are essential for managing MySQL tables:</h4>

<li> Use SELECT to retrieve data.

<li> Use RENAME TABLE to rename tables.

<li> Use ALTER TABLE to add, drop, or modify columns, and to rearrange column order.
</ul>

### Always back up your data before performing structural changes.
