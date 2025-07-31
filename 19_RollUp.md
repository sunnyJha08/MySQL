# ROLLUP

To get subtotals and grand totals, you can use ROLLUP:

```sql
SELECT gender, COUNT(*) AS total_users
FROM users
GROUP BY gender WITH ROLLUP;
```

<ul>
  <h3>Explanation:</h3>
  <li> This will give you a count of users by gender, along with a grand total for all users.
</ul>

## Stored Procedures in MySQL

A stored procedure is a saved SQL block that can be executed later. It's useful when you want to encapsulate logic that can be reused multiple times — like queries, updates, or conditional operations.

<hr>

## Why Change the Delimiter?

By default, MySQL uses ; to end SQL statements.

But when defining stored procedures, we use ; inside the procedure as well. This can confuse MySQL. To avoid this, we temporarily change the delimiter (e.g. to $$ or //) while creating the procedure.

<hr>

## Syntax for Creating a Stored Procedure

```sql
DELIMITER $$
 
CREATE PROCEDURE procedure_name()
BEGIN
    -- SQL statements go here
END$$
 
DELIMITER ;
```

After the procedure is created, we reset the delimiter back to ;.

<hr>

## Creating a Procedure with Input Parameters

Let’s say you want to create a stored procedure that inserts a new user into the users table.

<h3>Example:</h3>

```sql
DELIMITER $$
 
CREATE PROCEDURE AddUser(
    IN p_name VARCHAR(100),
    IN p_email VARCHAR(100),
    IN p_gender ENUM('Male', 'Female', 'Other'),
    IN p_dob DATE,
    IN p_salary INT
)
BEGIN
    INSERT INTO users (name, email, gender, date_of_birth, salary)
    VALUES (p_name, p_email, p_gender, p_dob, p_salary);
END$$
 
DELIMITER ;
```

This creates a procedure named AddUser that accepts five input parameters.

<hr>

## Calling the Procedure

You can call the procedure using:

```sql
CALL AddUser('Kiran Sharma', 'kiran@example.com', 'Female', '1994-06-15', 72000);
```

This will insert the new user into the users table.

<hr>

<ul>
<h3> Notes </h3>
<li> Input parameters are declared using the IN keyword.
<li> Stored procedures are stored in the database and can be reused.
</ul>

<hr>

## Viewing Stored Procedures

```sql
SHOW PROCEDURE STATUS WHERE Db = 'startersql';
```

<hr>

## Dropping a Stored Procedure

```sql
DROP PROCEDURE IF EXISTS AddUser;
```

## Summary

<pre>
<h4>Command 	          Purpose</h4>
DELIMITER $$ 	          Temporarily change statement delimiter
CREATE PROCEDURE 	  Defines a new stored procedure
CALL procedure_name(...)  Executes a stored procedure
DROP PROCEDURE 	          Removes an existing procedure
</pre>
