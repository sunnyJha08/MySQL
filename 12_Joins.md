SQL JOINs in MySQL

In SQL, JOINs are used to combine rows from two or more tables based on related columns — usually a foreign key in one table referencing a primary key in another.

We’ll use the following two tables:
users table
id 	name
1 	Aarav
2 	Sneha
3 	Raj
addresses table
id 	user_id 	city
1 	1 	Mumbai
2 	2 	Kolkata
3 	4 	Delhi

Note: user_id is a foreign key that references users.id.
1. INNER JOIN

Returns only the matching rows from both tables.

SELECT users.name, addresses.city
FROM users
INNER JOIN addresses ON users.id = addresses.user_id;

Output:
name 	city
Aarav 	Mumbai
Sneha 	Kolkata

    Raj is excluded because there is no matching address. Delhi is excluded because its user_id (4) is not in users.

Visual Representation:

users          addresses
 -----           ------
|  1  |         |  1  |
|  2  |         |  2  |
|     |         |     |
 => only matching pairs

2. LEFT JOIN

Returns all rows from the left table (users), and matching rows from the right table (addresses). If no match is found, NULLs are returned.

SELECT users.name, addresses.city
FROM users
LEFT JOIN addresses ON users.id = addresses.user_id;

Output:
name 	city
Aarav 	Mumbai
Sneha 	Kolkata
Raj 	NULL

    Raj is shown even though he doesn’t have an address.

Visual Representation:

users          addresses
 -----           ------
|  1  |         |  1  |
|  2  |         |  2  |
|  3  |         |     |
 => all users + matched addresses (or NULL)

3. RIGHT JOIN

Returns all rows from the right table (addresses), and matching rows from the left table (users). If no match is found, NULLs are returned.

SELECT users.name, addresses.city
FROM users
RIGHT JOIN addresses ON users.id = addresses.user_id;

Output:
name 	city
Aarav 	Mumbai
Sneha 	Kolkata
NULL 	Delhi

    Delhi is shown even though it points to a user_id that doesn't exist.

Visual Representation:

users          addresses
 -----           ------
|  1  |         |  1  |
|  2  |         |  2  |
|     |         |  4  |
 => all addresses + matched users (or NULL)

Summary Table
JOIN Type 	Description
INNER JOIN 	Only matching rows from both tables
LEFT JOIN 	All rows from left table + matching from right
RIGHT JOIN 	All rows from right table + matching from left
