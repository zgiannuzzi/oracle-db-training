## 9.1 

Used to specify which groups are to be displayed; restricts groups that do not meet group criteria
Divides the rows in a table into groups


1. In the SQL query shown below, which of the following is true about this query?

1. True - Kimberly Grant would not appear in the results set.
2. True - The GROUP BY clause has an error because the manager_id is not listed in the SELECT clause.
3. false - Only salaries greater than 16001 will be in the result set.
4. false - Names beginning with Ki will appear after names beginning with Ko.
5. false - Last names such as King and Kochhar will be returned even if they don’t have salaries > 16000.
```sql
SELECT last_name, MAX(salary)
FROM employees
WHERE last_name LIKE 'K%'
GROUP BY manager_id, last_name
HAVING MAX(salary) >16000
ORDER BY last_name DESC ;
```
2. Each of the following SQL queries has an error. Find the error and correct it. Use Oracle
Application Express to verify that your corrections produce the desired results.
a.
```sql
SELECT manager_id
FROM employees
GROUP BY manager_id;
WHERE AVG(salary) < 16000
```
b. 
```sql
SELECT cd_number, COUNT(title)
FROM d_cds
WHERE cd_number < 93;
```
c.
```sql
SELECT ID, MAX(ID), artist AS Artist
FROM d_songs
GROUP by ID;
HAVING ID < 50
WHERE duration IN('3 min', '6 min', '10 min')
```
d.
```sql
SELECT loc_type, rental_fee AS Fee
FROM d_venues
GROUP BY "Fee"
WHERE id < 100
ORDER BY 2;
```
4. Rewrite the following query to accomplish the same result:
```sql
SELECT DISTINCT MAX(song_id)
FROM d_track_listings
Group BY MAX(song_ID)
WHERE track <= 3
```
5. Indicate True or False
1. TRUE - If you include a group function and any other individual columns in a SELECT clause, then each individual column must also appear in the GROUP BY clause.
2. FALSE You can use a column alias in the GROUP BY clause.
3. FALSE The GROUP BY clause always includes a group function.

6. Write a query that will return both the maximum and minimum average salary grouped by
department from the employees table.
```sql
SELECT max(avg(salary)), min(avg(salary))
FROM employees
GROUP by department_id;
```
7. Write a query that will return the average of the maximum salaries in each department for the
employees table.
```sql
SELECT max(avg(salary))
FROM employees
GROUP by department_id;
```

## 9.2

1. Rollup -Used to create subtotals that roll up from the most detailed level to a grand total, following a grouping list specified in the clause
2. CUBE - An extension to the GROUP BY clause like ROLLUP that produces cross-tabulation reports
3. GROUPING SETS - Used to specify multiple groupings of data

1. Within the Employees table, each manager_id is the manager of one or more employees who
each have a job_id and earn a salary. For each manager, what is the total salary earned by all of
the employees within each job_id? Write a query to display the Manager_id, job_id, and total
salary. Include in the result the subtotal salary for each manager and a grand total of all salaries.
```sql
SELECT manager_id, job_id, SUM(salary)
FROM employees
GROUP BY ROLLUP (manager_id, job_id);
```

2. Amend the previous query to also include a subtotal salary for each job_id regardless of the
manager_id.
```sql
SELECT manager_id, job_id, SUM(salary)
FROM employees
GROUP BY Cube (manager_id, job_id);
```


3. Using GROUPING SETS, write a query to show the following groupings:
• department_id, manager_id, job_id
• manager_id, job_id
• department_id, manager_id



## 9.3

1. UNION - operator that returns all rows from both tables and eliminates duplicates
2. - columns that were made up to match queries in another table that are not in both tables
3. UNION ALL - operator that returns all rows from both tables, including duplicates
4. Set Operators - used to combine results into one single result from multiple SELECT statements
5. MINUS - operator that returns rows that are unique to each table
6. INTERSECT - operator that returns rows common to both tables

1. Name the different Set operators?
   - Union
   - Union all
   - minus
   - instersect
3. Write one query to return the employee_id, job_id, hire_date, and department_id of all employees
and a second query listing employee_id, job_id, start_date, and department_id from the
job_history table and combine the results as one single output. Make sure you suppress
duplicates in the output.
```sql
SELECT hire_date, employee_id, job_id, department_id 
FROM employees
UNION
SELECT employee_id, job_id, start_date
FROM job_history
```
5. Amend the previous statement to not suppress duplicates and examine the output. How many
extra rows did you get returned and which were they? Sort the output by employee_id to make it
easier to spot.
```sql
SELECT hire_date, employee_id, job_id, department_id 
FROM employees
UNION ALL
SELECT employee_id, job_id, start_date
FROM job_history
Order by employee_id
```
6. List all employees who have not changed jobs even once. (Such employees are not found in the
job_history table)
```sql
SELECT hire_date, employee_id, job_id
FROM employees
UNION 
SELECT TO_DATE(null)employee_id, job_id, start_date
FROM job_history
```
8. List the employees that HAVE changed their jobs at least once.
```sql
SELECT hire_date, employee_id, job_id
FROM job_history
UNION 
SELECT employee_id, job_id, start_date
FROM employees
```
9. Using the UNION operator, write a query that displays the employee_id, job_id, and salary of ALL
present and past employees. If a salary is not found, then just display a 0 (zero) in its place.
