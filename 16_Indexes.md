# MySQL Indexes

### Indexes in MySQL are used to speed up data retrieval. They work like the index of a book — helping the database engine find rows faster, especially for searches, filters, and joins.

<hr>

## Viewing Indexes on a Table

To see the indexes on a table, use:

```sql
SHOW INDEXES FROM users;
```

This shows all the indexes currently defined on the users table, including the automatically created primary key index.

<hr>

## Creating a Single-Column Index

Suppose you're frequently searching users by their email. You can speed this up by indexing the email column.

```sql
CREATE INDEX idx_email ON users(email);
```

<ul>
<h3> What this does: </h3>
<li> Creates an index named idx_email
<li> Improves performance of queries like:
</ul>

```sql
SELECT * FROM users WHERE email = 'example@example.com';
```

<hr>

<ul>
<h3> Important Notes </h3>
<li> Indexes consume extra disk space
<li> Indexes slow down INSERT, UPDATE, and DELETE operations slightly (because the index must be updated)
<li> Use indexes only when needed (i.e., for columns used in WHERE, JOIN, ORDER BY)
</ul>

<hr>

## Creating a Multi-Column Index

If you often query users using both gender and salary, a multi-column index is more efficient than separate indexes.

```sql
CREATE INDEX idx_gender_salary ON users(gender, salary);
```

#### Usage Example:

```sql
SELECT * FROM users
WHERE gender = 'Female' AND salary > 70000;
```

This query can take advantage of the combined index on gender and salary.

<hr>

## Index Order Matters

<ul>
<h3>For a multi-column index on (gender, salary): </h3>
<li>This works efficiently:

    WHERE gender = 'Female' AND salary > 70000

<li>But this may not use the index effectively:

    WHERE salary > 70000
</ul>

Because the first column in the index (gender) is missing in the filter.

<hr>

## Dropping an Index

To delete an index:

```sql
DROP INDEX idx_email ON users;
```

<hr>

## Summary

<pre>
Feature 	Description
SHOW INDEXES 	View current indexes on a table
CREATE INDEX 	Create single or multi-column indexes
DROP INDEX 	Remove an index
Use when 	Query performance on large tables is a concern
Avoid on 	Columns that are rarely queried or always unique
</pre>
