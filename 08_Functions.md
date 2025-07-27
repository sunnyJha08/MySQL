# SQL Functions (MySQL)

<strong> SQL functions help you <b> analyze, transform, or summarize </b> data in your tables. </strong>

<ul>
<h3> We'll use the users table which includes:</h3>
<li> id, name, email, gender, date_of_birth, salary, created_at
</ul>

## 1. Aggregate Functions

These return a <b> single value </b> from a set of rows.

COUNT()

Count total number of users:

```sql
SELECT COUNT(*) FROM users;
```

Count users who are Female:

```sql
SELECT COUNT(*) FROM users WHERE gender = 'Female';
```

### MIN() and MAX()

Get the minimum and maximum salary:

```sql
SELECT MIN(salary) AS min_salary, MAX(salary) AS max_salary FROM users;
```

### SUM()

Calculate total salary payout:

```sql
SELECT SUM(salary) AS total_payroll FROM users;
```

### AVG()

Find average salary:

```sql
SELECT AVG(salary) AS avg_salary FROM users;
```

### Grouping with GROUP BY

Average salary by gender:

```sql
SELECT gender, AVG(salary) AS avg_salary
FROM users
GROUP BY gender;
```

## 2. String Functions

### LENGTH()

Length of user names:

```sql
SELECT name, LENGTH(name) AS name_length FROM users;
```

### LOWER() and UPPER()

Convert names to lowercase or uppercase:

```sql
SELECT name, LOWER(name) AS lowercase_name FROM users;
SELECT name, UPPER(name) AS uppercase_name FROM users;
```

### CONCAT()

Combine name and email:

```sql
SELECT CONCAT(name, ' <', email, '>') AS user_contact FROM users;
```

## 3. Date Functions

### NOW()

Current date and time:

```sql
SELECT NOW();
```

<b> YEAR(), MONTH(), DAY()

Extract parts of date_of_birth: </b>

```sql
SELECT name, YEAR(date_of_birth) AS birth_year FROM users;
```

### DATEDIFF()

Find number of days between today and birthdate:

```sql
SELECT name, DATEDIFF(CURDATE(), date_of_birth) AS days_lived FROM users;
```

### TIMESTAMPDIFF()

Calculate age in years:

```sql
SELECT name, TIMESTAMPDIFF(YEAR, date_of_birth, CURDATE()) AS age FROM users;
```

## 4. Mathematical Functions

### ROUND(), FLOOR(), CEIL()

```sql
SELECT salary,
       ROUND(salary) AS rounded,
       FLOOR(salary) AS floored,
       CEIL(salary) AS ceiled
FROM users;
```

### MOD()

Find even or odd user IDs:

```sql
SELECT id, MOD(id, 2) AS remainder FROM users;
```

## 5. Conditional Functions

### IF()

```sql
SELECT name, gender,
       IF(gender = 'Female', 'Yes', 'No') AS is_female
FROM users;
```

## Summary Table
<pre> <b>
FUNCTION           	PURPOSE <br> </b>
COUNT()            	Count rows <br>
SUM() 	            Total of a column <br>
AVG() 	            Average of values <br>
MIN()/MAX()       	Lowest / highest value <br>
LENGTH() 	          String length <br>
CONCAT()           	Merge strings <br>
YEAR()/DATEDIFF() 	Date breakdown / age <br>
ROUND() 	          Rounding numbers <br>
IF()               	Conditional logic 
</pre>
