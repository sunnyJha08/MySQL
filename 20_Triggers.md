# Triggers in MySQL

### A trigger is a special kind of stored program that is automatically executed (triggered) when a specific event occurs in a table — such as INSERT, UPDATE, or DELETE.

<ul>
Triggers are commonly used for:
<li> Logging changes
<li> Enforcing additional business rules
<li> Automatically updating related data
</ul>

<hr>

## Basic Trigger Structure

```sql
CREATE TRIGGER trigger_name
AFTER INSERT ON table_name
FOR EACH ROW
BEGIN
    -- statements to execute
END;
```

<ul>
<h3>Triggers can be fired:</h3>
<li> BEFORE or AFTER an event
<li> On INSERT, UPDATE, or DELETE
</ul>

<hr>

## Scenario: Log Every New User Insertion

Suppose we want to log every time a new user is inserted into the users table. We'll create a separate table called user_log to store log entries.

<hr>

## Step 1: Create the Log Table

```sql
CREATE TABLE user_log (
    id INT AUTO_INCREMENT PRIMARY KEY,
    user_id INT,
    name VARCHAR(100),
    created_on TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
```

## Step 2: Create the Trigger

We now define a trigger that runs after a new user is added.

```sql
DELIMITER $$
 
CREATE TRIGGER after_user_insert
AFTER INSERT ON users
FOR EACH ROW
BEGIN
    INSERT INTO user_log (user_id, name)
    VALUES (NEW.id, NEW.name);
END$$
 
DELIMITER ;
```

<ul>
<h3>Explanation:</h3>
<li> AFTER INSERT means the trigger fires after the user is inserted.
<li> NEW refers to the new row being added to the users table.
<li> We insert the new user's ID and name into the user_log table.
</ul>

## Step 3: Test the Trigger

```sql
CALL AddUser('Ritika Jain', 'ritika@example.com', 'Female', '1996-03-12', 74000);
```

Now check the user_log table:

```sql
SELECT * FROM user_log;
```
You should see Ritika's info automatically logged.

<hr>

## Dropping a Trigger

If you need to remove a trigger:

```sql
DROP TRIGGER IF EXISTS after_user_insert;
```

## Summary

<pre>
Trigger Component 	    Description
BEFORE / AFTER 	            When the trigger runs
INSERT / UPDATE / DELETE    What kind of action triggers it
NEW.column 	            Refers to the new row (for INSERT, UPDATE)
OLD.column 	            Refers to the old row (for UPDATE, DELETE)
FOR EACH ROW 	            Executes for each affected row
</pre>
