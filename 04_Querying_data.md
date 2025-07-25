# 📘 Querying Data in MySQL using SELECT
#### The *SELECT* statement is used to query data from a table in MySQL. Below is a comprehensive explanation of various *SELECT* use cases, with inline comments for better understanding.

## 🧱 Basic Syntax

```sql
SELECT column1, column2 FROM table_name;
```

This selects specific columns (column1, column2) from the specified table (table_name).

```sql
SELECT * FROM users;
```
The * selects all columns from the users table.

## 🔎 Filtering Rows with WHERE
#### Equal To

```sql
SELECT * FROM users WHERE gender = 'Male';

```
Retrieves all records where the gender column equals 'Male'.

#### Not Equal To

```sql
SELECT * FROM users WHERE gender != 'Female';
-- or
SELECT * FROM users WHERE gender <> 'Female';
```
Both queries return all users not identified as 'Female'.

#### Greater Than / Less Than

```sql
SELECT * FROM users WHERE date_of_birth < '1995-01-01';
```
Selects users born before January 1, 1995.


```sql
SELECT * FROM users WHERE id > 10;
```
Selects users with id values greater than 10.

#### Greater Than or Equal / Less Than or Equal

```sql
SELECT * FROM users WHERE id >= 5;
```
Returns users with id greater than or equal to 5.


```sql
SELECT * FROM users WHERE id <= 20;
```
Returns users with id less than or equal to 20.

## 🕳️ Working with NULL
#### IS NULL

```sql
SELECT * FROM users WHERE date_of_birth IS NULL;
```
Selects users whose date_of_birth is not provided (NULL).

#### IS NOT NULL

```sql
SELECT * FROM users WHERE date_of_birth IS NOT NULL;
```
Selects users whose date_of_birth has a value.

## 🔢 Range and Set Filters
#### BETWEEN

```sql
SELECT * FROM users WHERE date_of_birth BETWEEN '1990-01-01' AND '2000-12-31';
```
Selects users born between Jan 1, 1990 and Dec 31, 2000, inclusive.

#### IN

```sql
SELECT * FROM users WHERE gender IN ('Male', 'Other');
```
Selects users whose gender is either 'Male' or 'Other'.

## 🔍 Pattern Matching with LIKE

```sql
SELECT * FROM users WHERE name LIKE 'A%';
```
Finds users whose name starts with 'A'.


```sql
SELECT * FROM users WHERE name LIKE '%a';
```
Finds users whose name ends with 'a'.


```sql
SELECT * FROM users WHERE name LIKE '%li%';
```
Finds users whose name contains 'li'.

## 🧩 Combining Conditions with AND / OR

```sql
SELECT * FROM users WHERE gender = 'Female' AND date_of_birth > '1990-01-01';
```
Selects female users born after January 1, 1990.


```sql
SELECT * FROM users WHERE gender = 'Male' OR gender = 'Other';
```
Selects users who are either Male or Other gender.

## 📊 Sorting Results with ORDER BY

```sql
SELECT * FROM users ORDER BY date_of_birth ASC;
```
Sorts users by date_of_birth in ascending order (oldest to youngest).


```sql
SELECT * FROM users ORDER BY name DESC;
```
Sorts users by name in descending alphabetical order.

## 🎚️ Limiting Results with LIMIT

```sql
SELECT * FROM users LIMIT 5;
```
Returns the first 5 rows.


```sql
SELECT * FROM users LIMIT 10 OFFSET 5;
```
Skips the first 5 rows, then returns the next 10.


```sql
SELECT * FROM users LIMIT 5, 10;
```
This is shorthand for LIMIT 10 OFFSET 5:

Skip 5 rows, then return 10 rows.


```sql
SELECT * FROM users ORDER BY created_at DESC LIMIT 10;
```
Returns the 10 most recently created users (latest first).

## ❓ Quick Quiz — What do these queries do?
#### 1. High Earners, Recently Added

```sql
SELECT * FROM users WHERE salary > 60000 ORDER BY created_at DESC LIMIT 5;
```
Selects the top 5 most recently added users with a salary greater than 60,000.

#### 2. Salary Leaderboard

```sql
SELECT * FROM users ORDER BY salary DESC;
```
Lists all users sorted by salary, highest to lowest.

#### 3. Mid-Range Salary Users

```sql
SELECT * FROM users WHERE salary BETWEEN 50000 AND 70000;
```
Selects users with a salary between 50,000 and 70,000, inclusive.