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
a. SELECT manager_id
FROM employees
WHERE AVG(salary) < 16000
GROUP BY manager_id;
b. SELECT cd_number, COUNT(title)
FROM d_cds
WHERE cd_number < 93;
c. SELECT ID, MAX(ID), artist AS Artist
FROM d_songs
WHERE duration IN('3 min', '6 min', '10 min')
HAVING ID < 50
GROUP by ID;
d. SELECT loc_type, rental_fee AS Fee
FROM d_venues
WHERE id <100
GROUP BY "Fee"
ORDER BY 2;

3. Rewrite the following query to accomplish the same result:
SELECT DISTINCT MAX(song_id)
FROM d_track_listings
WHERE track IN ( 1, 2, 3);

4. Indicate True or False
_____ a. If you include a group function and any other individual columns in a SELECT clause,
then each individual column must also appear in the GROUP BY clause.
_____ b. You can use a column alias in the GROUP BY clause.
_____ c. The GROUP BY clause always includes a group function.

5. Write a query that will return both the maximum and minimum average salary grouped by
department from the employees table.

6. Write a query that will return the average of the maximum salaries in each department for the
employees table.




## 9.2

Used to create subtotals that roll up from the most detailed level
to a grand total, following a grouping list specified in the clause
An extension to the GROUP BY clause like ROLLUP that
produces cross-tabulation reports
Used to specify multiple groupings of data
Try It / Solve It
1. Within the Employees table, each manager_id is the manager of one or more employees who
each have a job_id and earn a salary. For each manager, what is the total salary earned by all of
the employees within each job_id? Write a query to display the Manager_id, job_id, and total
salary. Include in the result the subtotal salary for each manager and a grand total of all salaries.
2. Amend the previous query to also include a subtotal salary for each job_id regardless of the
manager_id.
3. Using GROUPING SETS, write a query to show the following groupings:
• department_id, manager_id, job_id
• manager_id, job_id
• department_id, manager_id
