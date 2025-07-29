# SQL JOINs in MySQL

### In SQL, JOINs are used to combine rows from two or more tables based on related columns — usually a foreign key in one table referencing a primary key in another. <br>

We’ll use the following two tables:

<pre>
users   table
id 	name
1 	Aarav
2 	Sneha
3 	Raj
</pre>

<pre>
addresses table
id 	user_id 	city
1 	1 	        Mumbai
2 	2 	        Kolkata
3 	4 	        Delhi
</pre>

Note: user_id is a foreign key that references users.id.

<hr>

## 1. INNER JOIN

Returns only the matching rows from both tables.

```sql
SELECT users.name, addresses.city
FROM users
INNER JOIN addresses ON users.id = addresses.user_id;
```

<pre>
Output:
name 	city
Aarav 	Mumbai
Sneha 	Kolkata
</pre>

<i> Raj is excluded because there is no matching address. Delhi is excluded because its user_id (4) is not in users. </i>

### Visual Representation:
```sql
users          addresses
 -----           ------
|  1  |         |  1  |
|  2  |         |  2  |
|     |         |     |
 => only matching pairs
```

## 2. LEFT JOIN

Returns all rows from the left table (users), and matching rows from the right table (addresses). If no match is found, NULLs are returned.

```sql
SELECT users.name, addresses.city
FROM users
LEFT JOIN addresses ON users.id = addresses.user_id;
```

<pre>
Output:
name 	city
Aarav 	Mumbai
Sneha 	Kolkata
Raj 	NULL
</pre>

<i> Raj is shown even though he doesn’t have an address. </i>

### Visual Representation:
```sql
users          addresses
 -----           ------
|  1  |         |  1  |
|  2  |         |  2  |
|  3  |         |     |
 => all users + matched addresses (or NULL)
```

## 3. RIGHT JOIN

Returns all rows from the right table (addresses), and matching rows from the left table (users). If no match is found, NULLs are returned.

```sql
SELECT users.name, addresses.city
FROM users
RIGHT JOIN addresses ON users.id = addresses.user_id;
```

<pre>
Output:
name 	city
Aarav 	Mumbai
Sneha 	Kolkata
NULL 	Delhi
</pre>

<i> Delhi is shown even though it points to a user_id that doesn't exist. </i>

### Visual Representation:

```sql
users          addresses
 -----           ------
|  1  |         |  1  |
|  2  |         |  2  |
|     |         |  4  |
 => all addresses + matched users (or NULL)
```

<hr>

### Summary Table

<pre>
JOIN Type 	Description
INNER JOIN 	Only matching rows from both tables
LEFT JOIN 	All rows from left table + matching from right
RIGHT JOIN 	All rows from right table + matching from left
</pre>
