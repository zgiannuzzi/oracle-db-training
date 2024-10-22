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
____ a. A join is a type of query that gets data from more than one table based on columns with the same name.
____ b. To join tables using an equijoin, there must be a common column in both tables and that column is usually a primary key in one of the tables.
____ c. A Cartesian product occurs because the query does not specify a WHERE clause.
____ d. Table aliases are required to create a join condition.
____ e. If a table alias is used for a table name in the FROM clause, it must be substituted for the table name throughout the SELECT statement.
____ f. Table alias must be only one character in length.
____ g. A simple join or inner join is the same as an equijoin.

8. What advantage does being able to combine data from multiple tables have for a business?



















