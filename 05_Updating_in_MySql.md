# UPDATE - Modifying Existing Data

#### The UPDATE statement is used to change values in one or more rows.
## Basic Syntax

```sql
UPDATE table_name
SET column1 = value1, column2 = value2
WHERE condition;
```
## Example: Update One Column

```sql
UPDATE users
SET name = 'Alicia'
WHERE id = 1;
```
This changes the name of the user with id = 1 to "Alicia".
## Example: Update Multiple Columns

```sql
UPDATE users
SET name = 'Robert', email = 'robert@example.com'
WHERE id = 2;
```
## Without WHERE Clause (Warning)

```sql
UPDATE users
SET gender = 'Other';
```
<i> This updates <b> every row </b> in the table. Be very careful when omitting the WHERE clause.</i>

<hr>

## Quick Quiz: Practice Your UPDATE Skills

#### Try answering or running these queries based on your users table.

### 1. Update the salary of user with id = 5 to ₹70,000.

```sql
UPDATE users
SET salary = 70000
WHERE id = 5;
```
### 2. Change the name of the user with email aisha@example.com to Aisha Khan.

```sql
UPDATE users
SET name = 'Aisha Khan'
WHERE email = 'aisha@example.com';
```
### 3. Increase salary by ₹10,000 for all users whose salary is less than ₹60,000.

```sql
UPDATE users
SET salary = salary + 10000
WHERE salary < 60000;
```
### 4. Set the gender of user Ishaan to Other.

```sql
UPDATE users
SET gender = 'Other'
WHERE name = 'Ishaan';
```

### 5. Reset salary of all users to ₹50,000 (Careful - affects all rows).

```sql
UPDATE users
SET salary = 50000;
```

"Note: This query will overwrite salary for every user. Use with caution!"
