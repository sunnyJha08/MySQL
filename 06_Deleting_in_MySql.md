# DELETE - Removing Data from a Table

The DELETE statement removes rows from a table.
## Basic Syntax

```sql
DELETE FROM table_name
WHERE condition;
```
## Example: Delete One Row

```sql
DELETE FROM users
WHERE id = 3;
```
## Delete Multiple Rows

```sql
DELETE FROM users
WHERE gender = 'Other';
```
## Delete All Rows (but keep table structure)

```sql
DELETE FROM users;
```

## Drop the Entire Table (use with caution)

```sql
DROP TABLE users;
```
"This removes the table structure and all data permanently.

## Best Practices

<strong> Always use WHERE unless you're intentionally updating/deleting everything.

Consider running a SELECT with the same WHERE clause first to confirm what will be affected: </strong>

```sql
SELECT * FROM users WHERE id = 3;
```
<strong> Always back up important data before performing destructive operations. </strong>

## Quick Quiz: Practice Your DELETE Skills

what will happen if you run these queries?

```sql
DELETE FROM users
WHERE salary < 50000;
```
```sql
DELETE FROM users
WHERE salary IS NULL;
```