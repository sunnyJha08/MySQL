# Subqueries in MySQL

## A subquery is a query nested inside another query. Subqueries are useful for breaking down complex problems into smaller parts.

<ul>
They can be used in:
    <li> SELECT statements
    <li> WHERE clauses
    <li> FROM clauses
</ul>

<hr>

## Example Scenario: Salary Comparison

Suppose we want to find all users who earn more than the average salary of all users.

<hr>

## Scalar Subquery Example

This subquery returns a single value — the average salary — and we compare each user's salary against it.

```sql
SELECT id, name, salary
FROM users
WHERE salary > (
    SELECT AVG(salary) FROM users
);
```

<ul>
<h3> Explanation: </h3>
<li> The inner query: SELECT AVG(salary) FROM users returns the average salary.
<li> The outer query selects all users with a salary greater than that average.
</ul>

<hr>

## Subquery with IN

Now let's say we want to find users who have been referred by someone who earns more than ₹75,000.

```sql
SELECT id, name, referred_by_id
FROM users
WHERE referred_by_id IN (
    SELECT id FROM users WHERE salary > 75000
);
```

<ul>
<h3> Explanation: </h3>
    <li> The inner query: SELECT id FROM users WHERE salary > 75000 returns a list of user IDs (referrers) who earn more than ₹75,000.
   <li> The outer query selects users whose referred_by_id is in that list.
</ul>

<hr>

## Other Places Subqueries Are Used

<ul>
You can also use subqueries:
<li> Inside SELECT columns (called scalar subqueries)
<li> In the FROM clause to create derived tables
</ul>

## Example in SELECT:

```sql
SELECT name, salary,
  (SELECT AVG(salary) FROM users) AS average_salary
FROM users;
```

This shows each user's salary along with the overall average.

<hr>

## Summary

<pre>
Subquery Type 	        Use Case
Scalar Subquery 	Returns one value (e.g. AVG, MAX)
Subquery with IN 	Returns multiple values
Subquery in SELECT 	Shows related calculated value
Subquery in FROM 	Acts as a virtual table
</pre>

### Subqueries are powerful tools when filtering based on computed or dynamic conditions.
