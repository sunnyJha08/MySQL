# MySQL Views

### A view in MySQL is a virtual table based on the result of a SELECT query. It does not store data itself — it always reflects the current data in the base tables.

<ul>
<h3> Views are useful when: </h3>
<li> You want to simplify complex queries
<li> You want to reuse logic
<li> You want to hide certain columns from users
<li> You want a "live snapshot" of filtered data
</ul>

<hr>

## Creating a View

Suppose we want a view that lists all users earning more than ₹70,000.

```sql
CREATE VIEW high_salary_users AS
SELECT id, name, salary
FROM users
WHERE salary > 70000;
```

<hr>

## Querying the View

```sql
SELECT * FROM high_salary_users;
```

This will return all users from the users table where salary is above ₹70,000.

<hr>

## Demonstrating That a View is Always Up-To-Date

Let’s see what happens when the underlying data changes.
#### Step 1: View before update

```sql
SELECT * FROM high_salary_users;
```

### Output:

<pre>
id 	name 	salary
2 	Sneha 	75000
5 	Fatima 	80000
</pre>

#### Step 2: Update a user's salary

```sql
UPDATE users
SET salary = 72000
WHERE name = 'Raj';
```

#### Step 3: Query the view again

```sql
SELECT * FROM high_salary_users;
```

### New Output:

<pre>
id 	name 	salary
2 	Sneha 	75000
5 	Fatima 	80000
3 	Raj 	72000
</pre>

<i> Notice how Raj is now included in the view — without updating the view itself. That’s because views always reflect live data from the original table. </i>

<hr>

## Dropping a View

To remove a view:

```sql
DROP VIEW high_salary_users;
```

<hr>

<ul>
<h3> Summary </h3>
<li> Views act like saved SELECT queries
<li> Views are not duplicated data
<li> Changes to base tables are reflected automatically
<li> Great for simplifying complex queries or creating filtered access
</ul>
