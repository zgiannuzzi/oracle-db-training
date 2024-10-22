## 7.1

1. Cartesian Product - Results from an invalid or omitted join condition; all combinations of rows are displayed
2. EQUIJOIN - Values in a column in one table are equal to a value in another table; also called an inner join or simple join
3. Connection command exclusive to a specific company
4. Alias - Gives a table another name to simplify queries and improve performance
5. Display data from two or more related tables

1. Create a Cartesian product that displays the columns in the d_play_list_items and the d_track_listings in the DJs on Demand database.
   ```sql
      Select d_play_list_items.*, d_track_listings.* from d_play_list_items, d_track_listings
   ```
2. Correct the Cartesian product produced in question 1 by creating an equijoin using a common column.
   ```sql
      Select d_play_list_items.*, d_track_listings.* from d_play_list_items, d_track_listings where d_play_list_items.song_id = d_track_listings.song_id
   ```  
3. Write a query to display the title, type, description, and artist from the DJs on Demand database.
   ```sql
      Select d_songs.title, d_songs.type_code, d_songs.artist, d_types.description from d_songs, d_types where d_songs.type_code = d_types.code
   ```
4. Rewrite the query in question 3 to select only those titles with an ID of 47 or 48.
   ```sql
      Select d_songs.title, d_songs.type_code, d_songs.artist, d_types.description from d_songs, d_types
      where d_songs.type_code = d_types.code
      AND (d_songs.title = 47 or d_songs.title = 48) 
   ```
5. Write a query that extracts information from three tables in the DJs on Demand database, the d_clients table, the d_events table, and the d_job_assignments table.
   ```sql
      Select d_clients.firstname, d_events.name, d_job_assignments.job_date from d_clients, d_events, d_job_assignments
      where d_clients.client_number = d_events.client_number
      AND d.events.id = d_job_assignments.event_id
   ```
6. Create and execute an equijoin between DJs on Demand tables d_track_listings and d_cds. Return the song_id and the title only.
   ```sql
      select d_track_listings.song_id, d_cds.title from d_track_listings, d_cds where d_track_listings.cd_number = d_cds.dc_number
   ```
7. Mark T for the statements that are true and F for the statements that are false.

1. TRUE - A join is a type of query that gets data from more than one table based on columns with the same name.
2. TRUE - To join tables using an equijoin, there must be a common column in both tables and that column is usually a primary key in one of the tables.
3. TRUE - A Cartesian product occurs because the query does not specify a WHERE clause.
4. FALSE - Table aliases are required to create a join condition.
5. FALSE - If a table alias is used for a table name in the FROM clause, it must be substituted for the table name throughout the SELECT statement.
6. FALSE - Table alias must be only one character in length.
7. TRUE - A simple join or inner join is the same as an equijoin.

8. What advantage does being able to combine data from multiple tables have for a business?
   - Makes easier to view data
   - Allows you to make mulitple connections over tables
   - 

## 7.2 

1. Create a join based on the cost of the event between the DJs on Demand tables D_EVENTS and D_PACKAGES. Show the name of the event and the code for each event.
  ```sql

  ```
2. Using the Oracle database, create a query that returns the employee last name, salary, and job-grade level based on the salary. Select the salary between the lowest and highest salaries.
  ```sql
    SELECT last_name, salary, grade_level, lowest_sal, highest_sal
    FROM employees, job_grades
    WHERE (salary BETWEEN lowest_sal AND highest_sal);
  ```
3. What condition requires the creation of a nonequijoin?
  ```sql
   the condition used is something other than equals
  ```
4. Rewrite the following nonequijoin statement using the logical condition operators (AND, OR, NOT): WHERE a.ranking BETWEEN g.lowest_rank AND g.highest_rank
  ```sql
      WHERE (a.ranking >= g.lowest_rank) AND (a.ranking <= g.highest_rank)
  ```
5. How do you know when to use a table alias and when not to use a table alias?
   - if you use a table alias in the select statement you must continue to use the alias
   - To distinguish columns that have identical names but reside in different tables, use table aliases
6. What kind of join would you use if you wanted to find data between a range of numbers?
   - nonequijoin
7. You need to produce a report for Global Fast Foods showing customers and orders. A customer must be included on the report even if the customer has had no orders.
  ```sql
     Select c.firstname, o.order_number from f_customers c, f_orders o where c.id = o.cust_id(+)
  ```
8. Create a query of the Oracle database that shows employee last names, department IDs, and department names. Include all employees even if they are not assigned to a department.
  ```sql
   SELECT e.last_name, d.department_id, d.department_name
   FROM employees e, departments d
   WHERE e.department_id = d.department_id(+);
  ```
9. Modify the query in problem 8 to return all the department IDs even if no employees are assigned to them.
  ```sql
   SELECT e.last_name, d.department_id, d.department_name
   FROM employees e, departments d
   WHERE e.department_id(+) = d.department_id;
  ```
10. There are one or more errors in each of the following statements. Describe the errors and correct them.
 - WHERE e.department_id(+) = d.department_id (+);
   - Can not perform a "full outer join" have to get rif of (+) on one of the sides 
 - SELECT e.employee id, e.last name, d.location id FROM employees, departments WHERE e.department_id = d.department_id(+);
   - need to alias the tables because they are used in Select statement
   - Fix - FROM employees e, departments d

11. Create a query that will show all CD titles and song IDs in the DJs on Demand database even if there is no CD number in the track-listings table.
  ```sql
   SELECT d_cds.title, d_songs.id
   FROM d_cds, d_songs
   WHERE d_cds.number = d_track_listings.cd_number(+);
  ```


















