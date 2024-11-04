## 10.1

1. It accepts a value from the inner query to complete its SELECT statement.
2. An inner query that returns one or more rows to the outer query
3. An inner query that is nested within an outer query
4. An inner query that compares multiple columns at the same time
5. An inner query that returns only one row to the outer query
6. An inner query that compares the multiple columns one at a time in different subqueries
7. Another name for a subquery

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













