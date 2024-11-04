## 10.1

1. It accepts a value from the inner query to complete its SELECT statement.
2. An inner query that returns one or more rows to the outer query
3. An inner query that is nested within an outer query
4. An inner query that compares multiple columns at the same time
5. An inner query that returns only one row to the outer query
6. An inner query that compares the multiple columns one at a time in different subqueries
7. Another name for a subquery


### Exercise 
1. What is the purpose of using a subquery?
   - The subquery executes to find the information you don't know.
2. What is a subquery?
   - A subquery is a SELECT statement that is embedded in a clause of another SELECT statement
3. What DJs on Demand d_play_list_items song_id’s have the same event_id as song_id 45?
   ```SQL
      Select event_id from d_play_list_items
      where event_id =
      (select song_id from d__play_list_items where song_id = 45)
   ```
4. Which events in the DJs on Demand database cost more than event_id = 100?
   ```SQL
      Select name from d_events
      where cost >
      (select costs from d_events where id = 100)
   ```
5. Find the track number of the song that has the same CD number as “Party Music for All Occasions.”
   ```SQL
      Select track, cd_number from d_track_listings
      where track =
      (select cd_number from d_track_listings where cd_number = 91)
   ```
6. List the DJs on Demand events whose theme code is the same as the code for “Tropical.”
   ```SQL
      Select track, cd_number from d_track_listings
      where track =
      (select cd_number from d_track_listings where cd_number = 91)
   ```
7. What are the names of the Global Fast Foods staff members whose salaries are greater than the
staff member whose ID is 12?
   ```SQL
    SELECT first_name, last_name, salary
    FROM employees
    WHERE salary >
    (SELECT salary
    FROM employees
    WHERE staff_id = 12);
   ```
8. What are the names of the Global Fast Foods staff members whose staff types are not the same
as Bob Miller’s?
   ```SQL
    SELECT first_name, last_name, job_id
    FROM employees
    WHERE job_id !=
    (SELECT job_id
    FROM employees
    WHERE last_name = "Miller");
   ```
9. Which Oracle employees have the same department ID as the IT department?
   ```SQL
    SELECT first_name, last_name, department_id
    FROM employees
    WHERE department_id =
    (SELECT job_id
    FROM employees
    WHERE last_name = "Miller");
   ```
10. What are the department names of the Oracle departments that have the same location ID as
Seattle?
   ```SQL
    SELECT dapartment_name
    FROM employees
    WHERE dpartment_ID =
    (SELECT location_id
    FROM employees
    WHERE location = "Seattle");
   ```
11. Indicate whether the statement regarding subqueries is True or False.
1. TRUE - It is good programming practice to place a subquery on the right side of the comparison operator.
2. False - A subquery can reference a table that is not included in the outer query’s FROM clause.
3. TRUE - Single-row subqueries can return multiple values to the outer query.

# 10.2


1. Write a query to return all those employees who have a salary greater than that of Lorentz and are in the same department as Abel.
   ```SQL
    SELECT First_name, last_name, salary
    FROM employees
    WHERE salary >
    (SELECT salary
    FROM employees
    WHERE first_name = "Lorentz")
    AND
    department_id = 
   (select department_id
    From employee
    where laat_name = "abel" ;
   ```
2. Write a query to return all those employees who have the same job id as Rajs and were hired after Davies.

3. What DJs on Demand events have the same theme code as event ID = 100?

4. What is the staff type for those Global Fast Foods jobs that have a salary less than those of any Cook staff-type jobs?

5. Write a query to return a list of department id’s and average salaries where the department’s average salary is greater than Ernst’s salary.

6. Return the department ID and minimum salary of all employees, grouped by department ID, having a minimum salary greater than the minimum salary of those employees whose department ID is not equal to 50.


# 10.3
1. What will be returned by a query if it has a subquery that returns a null ?
  - If IN or ANY are used, the outer query will return rows which match the non-null values, if all is used nothing is returned

2. Write a query that returns jazz and pop songs. Write a multi-row subquery and use the d_songs
and d_types tables. Include the id, title, duration, and the artist name.
   ```sql
      Select id, title, duration, name
      from d_songs
      Group by Type_code
      where type_code =
      (select code from d_types where code in (1,12))
   ```
3. Find the last names of all employees whose salaries are the same as the minimum salary for any
department.
   ```sql
      Select department_id, MIN(salary)
      From employees
      GROUP BY department_id
      HAVING MIN(salary) = 
      (Select salary
      From employees
      Where department_id IN (10,20))
      ORDER BY department_id;
   ```
4. Which Global Fast Foods employee earns the lowest salary? Hint: You can use either a single-
row or a multiple-row subquery.
   ```sql
      Select department_id, MIN(salary), First_name, Last_name
      From employees
      GROUP BY department_id
      HAVING MIN(salary) = ANY
      (Select salary
      From employees
      Where department_id IN (10,20))
      ORDER BY department_id;
   ```
5. Place the correct multiple-row comparison operators in the outer query WHERE clause of each of
the following:

1. Which CDs in our d_cds collection were produced before “Carpe Diem” was produced?
 - WHERE year < in (SELECT year ...

2. Which employees have salaries lower than any one of the programmers in the IT department?
 - WHERE salary < in (SELECT salary ...

3. What CD titles were produced in the same year as “Party Music for All Occasions” or “Carpe
Diem”?
 - WHERE year in (SELECT year ...

4. What song title has a duration longer than every type code 77 title?
WHERE duration > (SELECT duration ...


6. If each WHERE clause is from the outer query, which of the following are true?
- True WHERE size > ANY -- If the inner query returns sizes ranging from 8 to 12, the value 9
could be returned in the outer query.
- False WHERE book_number IN -- If the inner query returns books numbered 102, 105, 437,
and 225 then 325 could be returned in the outer query.
- True WHERE score <= ALL -- If the inner query returns the scores 89, 98, 65, and 72, then 82
could be returned in the outer query.
- False WHERE color NOT IN -- If the inner query returns red, green, blue, black, and then the
outer query could return white.
- True WHERE game_date = ANY -- If the inner query returns 05-Jun-1997, 10-Dec-2002, and
2-Jan-2004, then the outer query could return 10-Sep-2002.

7. The goal of the following query is to display the minimum salary for each department whose
minimum salary is less than the lowest salary of the employees in department 50. However, the
subquery does not execute because it has five errors. Find them, correct them, and run the query.
```sql
SELECT department_id
FROM employees
GROUP BY department_id
HAVING MIN(salary) >
(SELECT MIN(salary)
WHERE department_id < 50;)
WHERE MIN(salary)
```
8. Which statements are true about the subquery below?
SELECT employee_id, last_name
FROM employees
WHERE salary =
(SELECT MIN(salary)
FROM employees
GROUP BY department_id);
- True The inner query could be eliminated simply by changing the WHERE clause to
WHERE MIN(salary).
- False The query wants the names of employees who make the same salary as the smallest
salary in any department.
- False The query first selects the employee ID and last name, and then compares that to the
salaries in every department.
- False This query will not execute.

9. Write a pair-wise subquery listing the last_name, first_name, department_id, and manager_id for
all employees that have the same department_ id and manager_id as employee 141. Exclude
employee 141 from the result set.

10. Write a non-pair-wise subquery listing the last_name, first_name, department_id, and manager_id
for all employees that have the same department_ id and manager_id as employee 141.

## 10.4 

1. Explain the main difference between correlated and non-correlated subqueries?
  - A correlated subquery when the subquery references a column from a table referred to in the parent statement.

2. Write a query that lists the highest earners for each department. Include the last_name,
department_id, and the salary for each employee.
```sql
SELECT o.first_name,
o.last_name, o.salary, o.department_id
FROM employees o
WHERE o.salary =
(SELECT MAX(i.salary)
FROM employees i
WHERE i.department_id =
o.department_id);
```
3. Examine the following select statement and finish it so that it will return the last_name,
department_id, and salary of employees who have at least one person reporting to them. So we
are effectively looking for managers only. In the partially written SELECT statement, the WHERE
clause will work as it is. It is simply testing for the existence of a row in the subquery.
```sql
SELECT last_name,department_id,salary)
FROM employees outer
WHERE manager_id IN (SELECT manager_id
FROM (manager) inner
WHERE inner(manager_id) = inner(manager_id)
order by department_id
```
Finish off the statement by sorting the rows on the department_id column.

4. Using a WITH clause, write a SELECT statement to list the job_title of those jobs whose maximum
salary is more than half the maximum salary of the entire company. Name your subquery
MAX_CALC_SAL. Name the columns in the result JOB_TITLE and JOB_TOTAL, and sort the
result on JOB_TOTAL in descending order.
Hint: Examine the jobs table. You will need to join JOBS and EMPLOYEES to display the
job_title.





