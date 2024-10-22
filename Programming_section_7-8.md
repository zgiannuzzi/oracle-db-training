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
## 8.1 

1. AVG - Calculates average value excluding nulls
2. COUNT - Returns the number of rows with non-null values for the expression
3. VARRIANCE - For two sets of data with approximately the same mean, the greater the spread, the greater the standard deviation.
4. Operate on sets of rows to give one result per group
5. MIN - Returns minimum value ignoring nulls
6. STDDEVUsed with columns that store numeric data to calculate the spread of data around the mean
7. SUM - Calculates the sum ignoring null values
8. MAX- Returns the maximum value ignoring nulls
9. To gather into a sum or whole


2. Create a query that will show the average cost of the DJs on Demand events. Round to two decimal places.
   ```sql
      select ROUND(AVG(COST),2)
      from d_events 
   ```
3. Find the average salary for Global Fast Foods staff members whose manager ID is 19.
   ```sql
      select AVG(Salary)
      from f_staffs Where manager_id = 19 
   ```

4. Find the sum of the salaries for Global Fast Foods staff members whose IDs are 12 and 9.
   ```sql
      select SUM(Salary)
      from f_staffs Where (id = 12 or id = 9) 
   ```
5. Using the Oracle database, select the lowest salary, the most recent hire date, the last name of
the person who is at the top of an alphabetical list of employees, and the last name of the person
who is at the bottom of an alphabetical list of employees. Select only employees who are in
departments 50 or 60.
   ```sql
      select min(Salary) , max(hire_data), min(last_name), max(last_name)
      from employees Where (department_id = 50 or department_id = 60) 
   ```
6. Your new Internet business has had a good year financially. You have had 1,289 orders this year.
Your customer order table has a column named total_sales. If you submit the following query, how
many rows will be returned?
   ```sql
    SELECT sum(total_sales)
    FROM orders;
   ```
   - 1 row will be returned
7. You were asked to create a report of the average salaries for all employees in each division of the
company. Some employees in your company are paid hourly instead of by salary. When you ran
the report, it seemed as though the averages were not what you expected—they were much
higher than you thought! What could have been the cause?
 - any onw who is salaried is probably paid more therefor when you take the average of the numbers you wind up with a much higher salary.

8. Employees of Global Fast Foods have birth dates of July 1, 1980, March 19, 1979, and March 30, 1969. If you select MIN(birthdate), which date will be returned?
      - March 30, 1969

9. Create a query that will return the average order total for all Global Fast Foods orders from
January 1, 2002, to December 21, 2002.
   ```sql
    SELECT AVG(order_total)
    FROM orders Where order_date Between '01-01-2002' and '12-21-2002';
   ```

10. What was the hire date of the last Oracle employee hired?
   ```sql
    SELECT MAX(hire_date)
    From Employees 
   ```

11. In the following SELECT clause, which value returned by the SELECT statement will be larger?
SELECT SUM(operating_cost), AVG(operating_cost)

12. Refer to the DJs on Demand database D_EVENTS table:
Which code is valid as part of an SQL query?
1. VALID - FROM event_date
2. VALID - SELECT SUM(cost)
3. NOT VALID - SELECT SUM(event_date)
4. VALID - SELECT AVG(cost) AS "Expense"
5. VALID - WHERE MIN(id) = 100
6. NOT VALID - SELECT MAX(AVG(cost))
7. VALID - SELECT MIN(event_date)

## 8.2 

1. Returns the number of non-null values in the expression column
2. The keyword used to return only non-duplicate values orcombinations of non-duplicate values in a query.
3. Returns the number of unique non-null values in the expression column.

1. How many songs are listed in the DJs on Demand D_SONGS table?
2. In how many different location types has DJs on Demand had venues?
3. The d_track_listings table in the DJs on Demand database has a song_id column and a
cd_number column. How many song IDs are in the table and how many different CD numbers are
in the table?
4. How many of the DJs on Demand customers have email addresses?
5. Some of the partners in DJs on Demand do not have authorized expense amounts (auth_expense_amt). How many partners do have this privilege?

6. What values will be returned when the statement below is issued?
SELECT COUNT(shoe_color), COUNT(DISTINCT shoe_color)
FROM shoes;
7. Create a query that will convert any null values in the auth_expense_amt column on the DJs on
Demand D_PARTNERS table to 100000 and find the average of the values in this column. Round
the result to two decimal places.
8. Which statement(s) is/are True about the following SQL statement:
SELECT AVG(NVL(selling_bonus, 0.10))
FROM bonuses;
_____ a. The datatypes of the values in the NVL clause can be any datatype except date data.
_____ b. If the selling_bonus column has a null value, 0.10 will be substituted.
_____ c. There will be no null values in the selling_bonus column when the average is calculated.
_____ d. This statement will cause an error. There cannot be two functions in the SELECT
statement.
9. Which of the following statements is/are TRUE about the following query?
SELECT DISTINCT colors, sizes
FROM items;
_____ a. Each color will appear only once in the result set.
_____ b. Each size will appear only once in the result set.
_____ c. Unique combinations of color and size will appear only once in the result set.
_____ d. Each color and size combination will appear more than once in the result set.













































