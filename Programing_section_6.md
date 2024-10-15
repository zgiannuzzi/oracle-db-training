# 6.1

### Vocabulary
1. Cross Join- Returns the Cartesian product from two tables.
2. Natural Join- Joins two tables based on the same column name.


### Exercise
1. Create a cross-join that displays the last name and department name from the employees and
departments tables.
```sql
SELECT last_name, department_name
FROM employees CROSS JOIN departments;
```

2. Create a query that uses a natural join to join the departments table and the locations table.
Display the department id, department name, location id, and city.
```sql
Select department_id, department_name, location_id, city
From Departments NATURAL JOIN locations;

```

3. Create a query that uses a natural join to join the departments table and the locations table.
Restrict the output to only department IDs of 20 and 50. Display the department id, department
name, location id, and city.
```sql
Select department_id, department_name, location_id, city
From Departments NATURAL JOIN locations
Where (department_id = 20 OR department_id = 50;
```

# 6.2
### Vocabulary
1. USING - Allows a natural join based on an arbitrary condition or two columns with different names.
2. ON clause -Performs an equijoin based on one specified column name

### Exercise
1. Join the Oracle database locations and departments table using the location_id column. Limit the
results to location 1400 only.
```sql
Select department_name, location_id
From locations JOIN department USING (location_id) 
Where location_id = 1400
```
2. Join DJs on Demand d_play_list_items, d_track_listings, and d_cds tables with the JOIN USING
syntax. Include the song ID, CD number, title, and comments in the output.
```sql
Select song_id, cd_number, title, comments
From d_track_listings JOIN d_cd USING(cd_number) join d_play_list_items USING(song_id);
```
3. Display the city, department name, location ID, and department ID for departments 10, 20, and 30
for the city of Seattle.
```sql
Select department_id, department_name, location_id, city
From locations JOIN department USING (location_id) 
Where (department_id IN (10,20,30) and city = 'Seattle'); 
```
4. Display country name, region ID, and region name for Americas.
```sql
Select country_name, region_id, region_name
From Countries JOIN regions USING (region_id)
Where region_id = 2;
```
5. Write a statement joining the employees and jobs tables. Display the first and last names, hire
date, job id, job title, and maximum salary. Limit the query to those employees who are in jobs that
can earn more than $12,000.
```sql
Select first_name, last_name, hire_date, job_id, job_title,max_salary)
From employees JOIN jobs using (job_id) 
Where max_salary > 12000;
```
6. Display job title, employee first name, last name, and email for all employees who are stock
clerks.
```sql
Select job_title, first_name, last_name, email 
From employees JOIN jobs using (job_id)
Where job_id = 'ST_CLERK';
```
# 6.3
### Vocabulary
1. FUll OUTER - Performs a join on two tables, retrieves all the rows in the Left
table, even if there is no match in the Right table. It also retrieves
all the rows in the Right table, even if there is no match in the Left
table.
2. LEFT OUTER - A join that returns the unmatched rows as well as matched rows
Performs a join on two tables, retrieves all the rows in the Left
table even if there is no match in the Right table.
3. RIGHT OUTER - Performs a join on two tables, retrieves all the rows
in the Right table even if there is no match in the Left table.
4. INNER JOIN - A join of two or more tables that returns only matched rows

### Exercise
1. Return the first name, last name, and department name for all employees including those employees not assigned to a department.
   ```sql
    SELECT e.last_name, d.department_id, d.department_name
    FROM employees e LEFT OUTER JOIN departments d
    ON (e.department_id = d.department_id);
   ```
2. Return the first name, last name, and department name for all employees including those departments that do not have an employee assigned to them.
  ```sql
    SELECT e.last_name, d.department_id, d.department_name
    FROM employees e RIGHT OUTER JOIN departments d
    ON (e.department_id = d.department_id);
   ```
3. Return the first name, last name, and department name for all employees including those
departments that do not have an employee assigned to them and those employees not assigned
to a department.
  ```sql
    SELECT e.last_name, d.department_id, d.department_name
    FROM employees e FULL OUTER JOIN departments d
    ON (e.department_id = d.department_id);
   ```
4. Create a query of the DJs on Demand database to return the first name, last name, event date,
and description of the event the client held. Include all the clients even if they have not had an
event scheduled.
  ```sql
   Select c.first_name, c.last_name, e.event_date, e.description
   From d_clients c  LEFT OUTER JOIN d_events e 
   on (c.client_number = e.client_number)
   ```
5. Using the Global Fast Foods database, show the shift description and shift assignment date even
if there is no date assigned for each shift description.
  ```sql
   Select d.description, a.shift_assign_date, 
   From f_shifts d RIGHT OUTER JOIN f_shift_assignments a 
   on (d.code = a.code)
   ```
# 6.4 
### Vocabulary
1. Self Join -Joins a table to itself
2. Hierarchical queries - Retrieves data based on a natural hierarchical relationship between rows in a table
3. LEVEL - Determines the number of steps down from the beginning row that should be returned by a hierarchical query
4. START - Identifies the beginning row for a hierarchical query
5. CONNECT BY PRIOR - Specifies the relationship between parent rows and child rows of a hierarchical query

### Exercise
1. Display the employee’s last name and employee number along with the manager’s last name and
manager number. Label the columns: Employee, Emp#, Manager, and Mgr#, respectively.
   ```sql
    SELECT w.last_name as "Employee", w.employee_id as "Emp#", m.last_name AS "Manager", w.manager_id as "Mgr#" 
    FROM employees w JOIN employees m
    ON (worker.manager_id = manager.employee_id);
   ```
2. Modify question 1 to display all employees and their managers, even if the employee does not
have a manager. Order the list alphabetically by the last name of the employee.
   ```sql
    SELECT w.last_name as "Employee", w.employee_id as "Emp#", m.last_name AS "Manager", w.manager_id as "Mgr#" 
    FROM employees w LEFT OUTER JOIN employees m
    ON (worker.manager_id = manager.employee_id);
   ```
3. Display the names and hire dates for all employees who were hired before their managers, along
with their managers’ names and hire dates. Label the columns Employee, Emp Hired, Manager
and Mgr Hired, respectively.
  ```sql
    SELECT w.last_name as "employee", w.hire_date as "Emp Hired", m.last_name AS "Manager", m.hire_date as "Mgr Hired" 
    FROM employees w JOIN employees m
    ON (worker.manager_id = manager.employee_id);
    WHERE w.hire_date < m.hire_date
   ```
4. Write a report that shows the hierarchy for Lex De Haans department. Include last name, salary,
and department id in the report.
   ```sql
   Select last_name, salary, department_ID 
   FROM employess
   START WITH last_name = 'De Haan'
   CONNECT BY PRIOR employee_id = manager_id;
   ```
5. What is wrong in the following statement?
   - Need to switch employee_id and manager_id 
   ```sql
   SELECT last_name, department_id, salary
   FROM employees
   START WITH last_name = 'King'
   CONNECT BY PRIOR manager_id = employee_id;
   ```
6. Create a report that shows the organization chart for the entire employee table. Write the report
so that each level will indent each employee 2 spaces. Since Oracle Application Express cannot
display the spaces in front of the column, use - (minus) instead.
   ```sql
    SELECT LPAD(last_name, LENGTH(last_name)+
    (LEVEL*2)-2,'-') AS "Org_Chart"
    FROM employees
    START WITH last_name = 'King'
    CONNECT BY PRIOR employee_id = manager_id;
   ```
7. Re-write the report from 6 to exclude De Haan and all the people working for him.
   ```sql
    SELECT LPAD(last_name, LENGTH(last_name)+
    (LEVEL*2)-2,'-') AS "Org_Chart"
    FROM employees
    START WITH last_name = 'King'
    CONNECT BY PRIOR employee_id = manager_id;
    AND last_name != 'De Haan'
   ```








