# More on MySQL

This section covers some essential MySQL features and operators that help you write more powerful and flexible queries.

<hr>

## 1. Logical Operators

Logical operators are used to combine multiple conditions in a WHERE clause.

<pre>
Operator 	Description 	                    Example
AND 	        All conditions must be true 	    salary > 50000 AND gender = 'Male'
OR 	        At least one condition is true 	    gender = 'Male' OR gender = 'Other'
NOT 	        Reverses a condition 	            NOT gender = 'Female'
</pre>

## 2. Add a Column to an Existing Table

Use ALTER TABLE to add a column:

```sql
ALTER TABLE users
ADD COLUMN city VARCHAR(100);
```

This adds a new column named city to the users table.

<hr>

## 3. Wildcard Operators

Wildcards are used with the LIKE operator for pattern matching in text.

<pre>
Wildcard 	Description 	                Example
% 	        Matches any sequence 	        WHERE name LIKE 'A%' (starts with A)
_ 	        Matches a single character      WHERE name LIKE '_a%' (second letter is 'a')
</pre>

<hr>

## 4. LIMIT with OFFSET

LIMIT is used to limit the number of rows returned. OFFSET skips a number of rows before starting to return rows.

```sql
SELECT * FROM users
ORDER BY id
LIMIT 5 OFFSET 10;
```

This skips the first 10 rows and returns the next 5.

Alternative syntax:

```sql
SELECT * FROM users
ORDER BY id
LIMIT 10, 5;
```

This also skips 10 and returns 5 (syntax: LIMIT offset, count).

<hr>

## 5. DISTINCT Keyword

DISTINCT is used to return only unique values.

```sql
SELECT DISTINCT gender FROM users;
```

Returns a list of unique gender values from the users table.

<hr>

## 6. TRUNCATE Keyword

TRUNCATE removes all rows from a table, but keeps the table structure.

```sql
TRUNCATE TABLE users;
```

<ul>
   <li> Faster than DELETE FROM users
   <li> Cannot be rolled back (unless in a transaction-safe environment)
</ul>

<hr>

## 7. CHANGE vs MODIFY Column

Both CHANGE and MODIFY are used to alter existing columns in a table, but they work slightly differently.

### CHANGE: Rename and change datatype

```sql
ALTER TABLE users
CHANGE COLUMN city location VARCHAR(150);
```

This renames city to location and changes its type.

### MODIFY: Only change datatype

```sql
ALTER TABLE users
MODIFY COLUMN salary BIGINT;
```

This changes only the datatype of salary.
# Conclusion

In this tutorial, we've covered the essentials of SQL, including how to create and manage databases, tables, and records. With this knowledge, you can start building and querying your own databases effectively.
