# GROUP BY and HAVING in MySQL

### The GROUP BY clause is used to group rows that have the same values in specified columns. It is typically used with aggregate functions like COUNT, SUM, AVG, MIN, or MAX.

### The HAVING clause is used to filter groups after aggregation — similar to how WHERE filters individual rows.

<hr>

## Example Table: users

Assume this is your users table:

<pre>
id 	name 	gender 	salary 	referred_by_id
1 	Aarav 	Male 	80000 	NULL
2 	Sneha 	Female 	75000 	1
3 	Raj 	Male 	72000 	1
4 	Fatima 	Female 	85000 	2
5 	Priya 	Female 	70000 	NULL
</pre>

<hr>

## GROUP BY Example: Average Salary by Gender

```sql
SELECT gender, AVG(salary) AS average_salary
FROM users
GROUP BY gender;
```

<ul>
<h3> Explanation: </h3>
<li> This groups users by gender.
<li> Then calculates the average salary for each group.
</ul>

<hr>

## GROUP BY with COUNT

Find how many users were referred by each user:

```sql
SELECT referred_by_id, COUNT(*) AS total_referred
FROM users
WHERE referred_by_id IS NOT NULL
GROUP BY referred_by_id;
```

### Output:
<pre>
<h4>referred_by_id 	total_referred </h4>
1 	        2
2 	        1
</pre>

<hr>

## HAVING Clause: Filtering Groups

Let’s say we only want to show genders where the average salary is greater than ₹75,000.

```sql
SELECT gender, AVG(salary) AS avg_salary
FROM users
GROUP BY gender
HAVING AVG(salary) > 75000;
```

<ul>
<h3>Why not WHERE?</h3>
<li> WHERE is used before grouping.
<li> HAVING is used after groups are formed — it's the only way to filter aggregated values.
</ul>

<hr>

## Another Example: Groups with More Than 1 Referral

```sql
SELECT referred_by_id, COUNT(*) AS total_referred
FROM users
WHERE referred_by_id IS NOT NULL
GROUP BY referred_by_id
HAVING COUNT(*) > 1;
```

<hr>

## Summary

<pre>
Clause 	    Purpose 	                            Can use aggregates?
WHERE 	    Filters rows before grouping             No
GROUP BY 	Groups rows based on column values   N/A
HAVING 	    Filters groups after aggregation 	     Yes
</pre>

## Use GROUP BY to organize data, and HAVING to filter those groups based on aggregate conditions.
