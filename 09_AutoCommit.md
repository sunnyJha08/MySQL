# MySQL Transactions and AutoCommit

By default, MySQL operates in <b> AutoCommit </b> mode. This means that every SQL statement is treated as a <b> transaction </b> and is committed automatically. However, for more control over when changes are saved, you can turn <b> AutoCommit </b> off and manage transactions manually.

<hr>

## 1. Disabling AutoCommit

When <b> AutoCommit </b> is off, you can explicitly control when to commit or rollback changes.

### To disable AutoCommit:

```sql
SET autocommit = 0;
```

This turns off AutoCommit, meaning that changes you make won't be saved to the database unless you explicitly tell MySQL to commit them.

<i> <b> Important </b>: Until you execute a COMMIT, your changes are not permanent. </i>

## 2. COMMIT — Save Changes to the Database

Once you’ve made changes and you’re confident that everything is correct, you can use the COMMIT command to save those changes.

### To commit a transaction:

```sql
COMMIT;
```

This saves all the changes made since the last COMMIT or ROLLBACK. After this point, the changes become permanent.

## 3. ROLLBACK — Revert Changes to the Last Safe Point

If you make an error or decide you don't want to save your changes, you can rollback the transaction to its previous state.

### To rollback a transaction:

```sql
ROLLBACK;
```

This undoes all changes since the last COMMIT or ROLLBACK.

<hr>

### Example Workflow

Here’s a simple example of using COMMIT and ROLLBACK in a transaction:

1. Turn off AutoCommit:

```sql
SET autocommit = 0;
```

2. Make some changes (e.g., updating a salary):

```sql
UPDATE users SET salary = 80000 WHERE id = 5;
```

3. Decide whether to commit or rollback:

a. If you’re happy with the changes, run:

```sql
 COMMIT;
```

b. If you’re not happy and want to revert the changes, run:

```sql
ROLLBACK;
```

<hr>

## 4. Enabling AutoCommit Again

If you want to turn AutoCommit back on (so that every statement is automatically committed), you can do so with:

```sql
SET autocommit = 1;
```

<hr>

<ul>
<h2> Best Practices </h2>

<li> Use COMMIT when you want to make changes permanent.

<li> Use ROLLBACK to discard changes if something goes wrong.

<li> Consider disabling AutoCommit when performing complex updates to avoid saving partial or incorrect data.
