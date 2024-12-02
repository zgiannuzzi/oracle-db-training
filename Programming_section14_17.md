# 14.1 

### Vocabulary 

1. UNIQUE  - Every value in a column or set of columns (a composite key) must be unique
2. NOT NULL - For every row entered into the table, there must be a value for that column
3. PRIMARY KEY - Constraint ensures that the column contains no null values and uniquely identifies each row of the table
4. CHECK - Specifies a condition for a column that must be true for each row of data
5. REFFERENCES - Identifies that table and column in the parent table
6. UNIQUE - An integrity constraint that requires every value in a column or set of columns be unique
7. FOREIGN KEY - Designates a column (child table) that establishes a relationship between a primary key in the same table and a different table (parent table)
8. References one or more columns and is defined separately from the definitions of the columns in the table
9. CONSTRAINGT - Database rule.
10. COLUMN LEVEL - Database rule that references a single column


### Exercise

1. What is a “constraint” as it relates to data integrity?
  - contraints are integral to datat integrity as with contraints can require certain entrys be required and others not so if something needs an ID a contraint can be set where the ID field cant be null 

3. What are the limitations of constraints that may be applied at the column level and at the table level?

4. Why is it important to give meaningful names to constraints?
  - Easy to identify what you are constraining. other wise can accidently remove a constrait you may want to keep 
5. Based on the information provided by the owners, choose a datatype for each column. Indicate
the length, precision, and scale for each NUMBER datatype.
  - ID NUMBER 3
  - name VARCHAR2 40
  - date_opened DATE
  - Adress VARCHAR2 40
  - city VARCHAR2 40
  - zip_code VARCHAR2 40
  - phone VARCHAR2 40
  - email VARCHAR2 40
  - manager_id NUMBER 3
  - emergency_contact VARCHAR2 40
6. Use “nullable” to indicate those columns that can have null values.
 - Every column except the following id, date_opened, address, city

7. Write the CREATE TABLE statement for the Global Fast Foods locations table to define the
constraints at the column level.

8. Execute the CREATE TABLE statement in Oracle Application Express.
  - got a table created message 
9. Execute a DESCRIBE command to view the Table Summary information.
```sql
DESCRIBE global_locations 
```
10. Rewrite the CREATE TABLE statement for the Global Fast Foods locations table to define the
UNIQUE constraints at the table level. Do not execute this statement

```sql
create table global_locations
(ID NUMBER (3) CONSTRAINT id_pk PRIMARY KEY,
name VARCHAR2 (40),
date_opened DATE CONSTRAINT dt_opened_nn NOT NULL ENABLE,
Adress VARCHAR2 (40) CONSTRAINT address_nn NOT NULL ENABLE,
city VARCHAR2 (40) CONSTRAINT city_nn NOT NULL ENABLE,
zip_code VARCHAR2 (40),
phone VARCHAR2 (40),
email VARCHAR2 (40),
manager_id NUMBER (3),
emergency_contact VARCHAR2 (40));
```
# 14.2 

### Vocabulary
1. ON DELETE Allows a foreign key row that is referenced to a primary key row to be deleted
2. CHECK Explicitly defines a condition that must be met
3. PRIMARY KEY A column or set of columns that uniquely identifies each row in a table
4. NOT NULL Constraint ensures that the column contains no null values
5. ON DELETE SET NULL Allows a child row to remain in a table with null values when a parent record has been deleted
6. FOREIGN KEY Establishes a relationship between the foreign key column and a primary key or unique key in the same table or a different table

### Exercise
1. What is the purpose of a
   - PRIMARY KEY - identifys a unique row in table 
   - FOREIGN KEY - a value that links one table to another  
   - CHECK CONSTRAINT

3. Using the column information for the animals table below, name constraints where applicable at
the table level, otherwise name them at the column level. Define the primary key (animal_id). The
license_tag_number must be unique. The admit_date and vaccination_date columns cannot
contain null values.
animal_id NUMBER(6) - PRIMARY KEY 
name VARCHAR2(25)
license_tag_number NUMBER(10) - UNIQUE 
admit_date DATE - NOT NULL 
adoption_id NUMBER(5),
vaccination_date DATE - NOT NULL

4. Create the animals table. Write the syntax you will use to create the table.
```sql
CREATE TABLE  animals
(animal_id NUMBER(3) CONSTRAINT anl_id_pk PRIMARY KEY,
name VARCHAR2(40),
license_tag_number NUMBER(10) CONSTRAINT tag_num_uk UNIQUE,
admit_date DATE CONSTRAINT dat_nn NOT NULL ENABLE,
adoption_id NUMBER(5,
vaccination_date DATE CONSTRAINT vac_dat_nn NOT NULL ENABLE
);
```
5. Enter one row into the table. Execute a SELECT * statement to verify your input. Refer to the
graphic below for input.
101 Spot 35540 10-Oct-2004 205 12-Oct-2004
```sql
INSERT INTO animals (animal_id, name, license_tag_number, admit_date, adoption_id, vaccination_date)
VALUES(101, 'Spot', 35540, TO_DATE('10-Oct-2004', 'DD-Mon-YYYY'), 205, TO_DATE('12-Oct-2004', 'DD-Mon-YYYY'));
SELECT * FROM animals;
```

6. Write the syntax to create a foreign key (adoption_id) in the animals table that has a
corresponding primary- key reference in the adoptions table. Show both the column-level and
table-level syntax. Note that because you have not actually created an adoptions table, no
adoption_id primary key exists, so the foreign key cannot be added to the animals table.
- column level

- table level - 
```sql
INSERT INTO animals (animal_id, name, license_tag_number, admit_date, adoption_id, vaccination_date)
VALUES(101, 'Spot', 35540, TO_DATE('10-Oct-2004', 'DD-Mon-YYYY'), 205, TO_DATE('12-Oct-2004', 'DD-Mon-YYYY'));
SELECT * FROM animals;
```

7. What is the effect of setting the foreign key in the ANIMAL table as:
a. ON DELETE CASCADE
b. ON DELETE SET NULL
8. What are the restrictions on defining a CHECK constraint?

# 14.3 

## Vocabulary 

1. DISABLE To deactivate an integrity constraint
2. CASCADE Disables dependent integrity constraints
3. ALTER To add, modify, or drop columns from a table
4. ENABLE To activate an integrity constraint currently disabled
5. DROP Removes a constraint from a table
6. DROP COLUMN Allows user to delete a column from a table
7. CASCADE Defines the actions the database server takes when a user
attempts to delete or update a key to which existing foreign keys
point


## Exercise 

1. What are four functions that an ALTER statement can perform on constraints?
- ADD 
- DROP
- ENABLE
- DISABLE
        
2. Since the tables are copies of the original tables, the integrity rules are not passed onto the new
tables; only the column datatype definitions remain. You will need to add a PRIMARY KEY
constraint to the copy_d_clients table. Name the primary key copy_d_clients_pk . What is the
syntax you used to create the PRIMARY KEY constraint to the copy_d_clients.table?
```sql
ALTER TABLE copy_d_clients
ADD  CONSTRAINT copy_d__pk PRIMARY KEY (client_number);
```
3. Create a FOREIGN KEY constraint in the copy_d_events table. Name the foreign key
copy_d_events_fk. This key references the copy_d_clients table client_number column. What is
the syntax you used to create the FOREIGN KEY constraint in the copy_d_events table?
```sql
ALTER TABLE copy_d_events 
ADD CONSTRAINT copy_d_fk FOREIGN KEY;
```
4. Use a SELECT statement to verify the constraint names for each of the tables. Note that the
tablenames must be capitalized.
a. The constraint name for the primary key in the copy_d_clients table is _______________.
b. The constraint name for the foreign key in the copy_d_events table is _______________.

5. Drop the PRIMARY KEY constraint on the copy_d_clients table. Explain your results.
```sql
ALTER TABLE copy_d_clients
DROP CONSTRAINT COPY_D_PK  ;
```
6. Add the following event to the copy_d_events table. Explain your results.
140 Cline Bas Mitzvah 15-Jul-2004 Church and Private Home formal 4500 105 87 77 7125
```sql
copy_d_events(id,name,event_date,description,cost,venue_id,package_code,theme_code,client_number)
VALUES(140,'Cline Bas Mitzvah',TO_DATE('15-Jul-2004','dd-Mon-yyyy'),'Church and Private Home formal',4500,105,87,77,7125);
```

7. Create an ALTER TABLE query to disable the primary key in the copy_d_clients table. Then add
the values from #6 to the copy_d_events table. Explain your results.
```sql
ALTER TABLE copy_d_clients
DISABLE CONSTRAINT COPY_D_PK CASCADE;
```
8. Repeat question 6: Insert the new values in the copy_d_events table. Explain your results.

9. Enable the primary-key constraint in the copy_d_clients table. Explain your results.
```sql
ALTER TABLE copy_d_clients
ENABLE CONSTRAINT COPY_D_PK ;
```
10. If you wanted to enable the foreign-key column and reestablish the referential integrity between
these two tables, what must be done?

# 15.1 
Creating Views

1. View - A subset of data from one or more tables that is generated from a query and stored as a virtual table
2. View_name - Name of view
3. FORCE - Creates a view regardless of whether or not the base tables exist
4. SIMPLE - Derives data from a table, no functions or groups, performs DML operations through the view
5. NOFORCE - Creates the view only if the base table exists
6. CREATE VIEW - Statement used to create a new view
7. ALIAS - Specifies a name for each expression selected by the view’s query
8. Subquery - A complete SELECT statement
9. Complex - Derives data from more than one table, contains functions or groups of data, and does not always allow DML operations through the view
10 Replace - Re-creates the view if it already exists

1. What are three uses for a view from a DBA’s perspective?
  - restrict access
  - create simple views
  - Abiluty to alias values 
2. Create a simple view called view_d_songs that contains the ID, title, and artist from the DJs on
Demand table for each “New Age” type code. In the subquery, use the alias “Song Title” for the
title column.
```sql
CREATE VIEW view_d_songs AS
SELECT d_songs.id, d_songs.title "Song Title", d_songs.artist
from d_songs INNER JOIN d_types ON d_songs.type_code = d_types.code
where d_types.description = 'New Age';
```
3. SELECT *
FROM view_d_songs.
What was returned?

4. REPLACE view_d_songs. Add type_code to the column list. Use aliases for all columns.
```sql
CREATE VIEW view_d_songs AS
SELECT d_songs.id, d_songs.title "Song Title", d_songs.artist, d_songs.type_code
from d_songs INNER JOIN d_types ON d_songs.type_code = d_types.code
where d_types.description = 'New Age';
```
5. Jason Tsang, the disk jockey for DJs on Demand, needs a list of the past events and those
planned for the coming months so he can make arrangements for each event’s equipment setup.
As the company manager, you do not want him to have access to the price that clients paid for
their events. Create a view for Jason to use that displays the name of the event, the event date,
and the theme description. Use aliases for each column name.

6. It is company policy that only upper-level management be allowed access to individual employee
salaries. The department managers, however, need to know the minimum, maximum, and
average salaries, grouped by department. Use the Oracle database to prepare a view that
displays the needed information for department managers.

# 15.2 

## Vocabulary 
1. Rownum -  pseudocolumn which assigns a sequential value starting with 1 to each of the rows returned from the subquery
2.  With check option Specifies that INSERTS and UPDATES performed through the view can’t create rows which the view cannot select
3. with read only -Ensures that no DML operations can be performed on this view

### Exercise 

1. Query the data dictionary USER_UPDATABLE_COLUMNS to make sure the columns in the base
tables will allow UPDATE, INSERT, or DELETE. Use a SELECT statement. All table names in the
data dictionary are stored in uppercase.

2. Use the CREATE or REPLACE option to create a view of all the columns in the copy_d_songs
table called view_copy_d_songs.
```sql
CREATE OR REPLACE VIEW view_copy_d_songs AS
SELECT * FROM copy_d_songs;
```
3. Use view_copy_d_songs to INSERT the following data into the underlying copy_d_songs table.
Execute a SELECT * from copy_d_songs to verify your DML command. See the graphic.
```sql
INSERT INTO view_copy_d_songs(id,title,duration,artist,type_code)
VALUES(88,'Mello Jello','2 min','The What',4);
```

4. Create a view based on the DJs on Demand COPY_D_CDS table. Name the view
read_copy_d_cds. Select all columns to be included in the view. Add a WHERE clause to restrict
the year to 2000. Add the WITH READ ONLY option.
```sql
CREATE OR REPLACE VIEW read_copy_d_cds  AS
SELECT * FROM copy_d_cds where year = '2000'
WITH READ ONLY ;
```
5. Using the read_copy_d_cds view, execute a DELETE FROM read_copy_d_cds WHERE
cd_number = 90;

6. Use REPLACE to modify read_copy_d_cds. Replace the READ ONLY option with WITH CHECK
OPTION CONSTRAINT ck_read_copy_d_cds. Execute a SELECT * statement to verify that the
view exists.
```sql
REPLACE VIEW read_copy_d_cds  AS
SELECT * FROM copy_d_cds
WHERE year = '2000'
WITH CHECK OPTION CONSTRAINT ck_read_copy_d_cds;
```
7. Use the read_copy_d_cds view to delete any CD of year 2000 from the underlying copy_d_cds.
```sql
DELETE FROM read_copy_d_cds
WHERE year = '2000';
```
8. Use the read_copy_d_cds view to delete cd_number 90 from the underlying copy_d_cds table.
```sql
DELETE FROM read_copy_d_cds
WHERE cd = 90;
```
9. Use the read_copy_d_cds view to delete year 2001 records.
```sql
DELETE FROM read_copy_d_cds
WHERE year = '2001';
```
10. Execute a SELECT * statement for the base table copy_d_cds. What rows were deleted?

11. What are the restrictions on modifying data through a view?

12. What is Moore’s Law? Do you consider that it will continue to apply indefinitely? Support your
opinion with research from the internet.
  - The niumber of transistors on a computer chip roughly doubles every 2 years
13. What is the “singularity” in terms of computing?
    - Technology grows so much that it is no longer controllable 


# 15.3 

## Vocabulary 

1. Top n - Asks for the N largest or smallest values in a column
2. DROP - Removes a view
3. INLINE Subquery with an alias that can be used within a SQL statement

# Exercise 
1. Create a view from the copy_d_songs table called view_copy_d_songs that includes only the title
and artist. Execute a SELECT * statement to verify that the view exists.
```sql
CREATE VIEW view_copy_d_songs AS
SELECT title, artist FROM copy_d_songs;
```
2. Issue a DROP view_copy_d_songs. Execute a SELECT * statement to verify that the view has
been deleted.
```sql
DROP VIEW view_copy_d_songs 
SELECT * FROM copy_d_songs;
```
3. Create a query that selects the last name and salary from the Oracle database. Rank the salaries
from highest to lowest for the top three employees.
```sql
SELECT last_name, salary FROM employees ORDER BY salary DESC
```
4. Construct an inline view from the Oracle database that lists the last name, salary, department ID,
and maximum salary for each department. Hint: One query will need to calculate maximum salary
by department ID.

5. Create a query that will return the staff members of Global Fast Foods ranked by salary from
lowest to highest.
```sql
SELECT ROWNUM , last_name, salary from f_staffs ORDER BY salary);
```
# 16.1
1. CREATE SEQUENCE - Command that automatically generates sequential numbers
2. Sequence - Generates a numeric value
3. NEXTVAL - Returns the next available sequence value
4. INCREMENT - BY Specifies the interval between sequence numbers
5. NOMAXVALUE - Specifies a maximum value of 10^27 for an ascending sequence and -1 for a descending sequence (default)
6. CURRVAL - returns the current sequence value
7. MIONVALL - specifies the minimum sequence value
8. CYCLE/NOCUCLE - specifies whether the sequence continues to generate values after reaching its maximum or minimum values
9. NOMINVAL - specifies a minimum value of 1 for an ascending sequence and –(10^26) for a descending sequence (default)
10. MAXVALUE - specifies a maximum or default value the sequence can generate
11. START WITH - specifies the first sequence number to be generated
12. CACHE - specifies how many values the Server pre-allocates and keeps in memory

1. Using CREATE TABLE AS subquery syntax, create a seq_d_songs table of all the columns in the
DJs on Demand database table d_songs. Use the SELECT * in the subquery to make sure that
you have copied all of the columns.
```sql
CREATE TABLE seq_d_songs AS (SELECT * FROM d_songs);
SELECT * FROM d_songs;
```
2. Because you are using copies of the original tables, the only constraints that were carried over
were the NOT NULL constraints. Create a sequence to be used with the primary-key column of
the seq_d_songs table. To avoid assigning primary-key numbers to these tables that already
exist, the sequence should start at 100 and have a maximum value of 1000. Have your sequence
increment by 2 and have NOCACHE and NOCYCLE. Name the sequence seq_d_songs_seq.
```sql
CREATE SEQUENCE seq_d_songs_seq
INCREMENT BY 2
START WITH 100
MAXVALUE 1000
NOCYCLE
NOCACHE;
```
3. Query the USER_SEQUENCES data dictionary to verify the seq_d_songs_seq SEQUENCE
settings.

4. Insert two rows into the seq_d_songs table. Be sure to use the sequence that you created for the
ID column. Add the two songs shown in the graphic.

5. Write out the syntax for seq_d_songs_seq to view the current value for the sequence. Use the
DUAL table. (Oracle Application Developer will not run this query.)
```sql
SELECT seq_d_songs_seq.CURRVAL FROM DUAL
```
6. What are three benefits of using SEQUENCEs?
  - avoid using the same numbers
  - saves time
  - 
7. What are the advantages of caching sequence values?

8. Name three reasons why gaps may occur in a sequence?
 - same sequene being used in other tables
 - database breaks 


# 16.2


## Vocabulary 
1. Confirms the existence of indexes from the USER_INDEXES data dictionary view
2. INDEX Schema object that speeds up retrieval of rows
3. To refer to a table by another name to simplify access
4. Composite An index that you create on multiple columns in a table
5. Unique The Oracle Server automatically creates this index when you define a column in a table to have a PRIMARY KEY or a UNIQUE KEY constraint
6. function based Stores the indexed values and uses the index based on a SELECT statement to retrieve the data
7. drop - Removes an index
8. Synonym - Gives alternative names to objects

## Exercise 
1. What is an index and what is it used for?
  - give the abilty to traverse  table faster 
2. What is a ROWID, and how is it used?
  - indexs use rowid faster way to access a particular row 
3. When will an index be created automatically?
  - Primary and unique keys 
4. Create a nonunique index (foreign key) for the DJs on Demand column (cd_number) in the
D_TRACK_LISTINGS table. Use the Oracle Application Developer SQL Workshop Data Browser
to confirm that the index was created.
```sql
CREATE INDEX cd_number_fk_i
on d_track_listings (cd_number);
```
5. Use the join statement to display the indexes and uniqueness that exist in the data dictionary for
the DJs on Demand D_SONGS table.

6. Use a SELECT statement to display the index_name, table_name, and uniqueness from the data
dictionary USER_INDEXES for the DJs on Demand D_EVENTS table.
```sql
SELECT index_name, table_name,uniqueness  FROM user_indexes  where table_name = 'D_EVENTS';
```
7. Write a query to create a synonym called dj_tracks for the DJs on Demand d_track_listings table.
```sql
CREATE SYNONYM dj_tracks FOR d_track_listings;
```
8. Create a function-based index for the last_name column in DJs on Demand D_PARTNERS table
that makes it possible not to have to capitalize the table name for searches. Write a SELECT
statement that would use this index.

9. Create a synonym for the D_TRACK_LISTINGS table. Confirm that it has been created by
querying the data dictionary.
```sql
CREATE SYNONYM dj_tracks FOR d_track_listings;
```
10. Drop the synonym that you created in question 9
```sql
DROP SYNONYM dj_tracks;
```

# 17.1 

## Exercise 
1. What are system privileges concerned with?
  - what you are able to do at the database level, eg. create tables 
2. What are object privileges concerned with?
  - what you are able to do on a "table" level eg. alter or update tables 
3. What is another name for object security?
  - data security
4. What commands are necessary to allow Scott access to the database with a password of tiger?
```sql
CREATE USER scott IDENTIFIED BY tiger;
```
5. What are the commands to allow Scott to SELECT from and UPDATE the d_clients table?
```sql
GRANT SELECT, UPDATE ON d_clients to scott;
```
6. What is the command to allow everybody the ability to view the d_songs table?
```sql
GRANT SELECT ON d_songs to PUBLIC;;
```
7. Query the data dictionary to view the object privileges granted to you the user.
```sql
CREATE USER scott IDENTIFIED BY tiger;
```
8. What privilege should a user be given to create tables?
  - CREATE TABLE
9. If you create a table, how can you pass along privileges to other users just to view your table?
```sql
GRANT SELECT ON d_songs to name1, name2...
```
10. What syntax would you use to grant another user access to your copy_employees table?
```sql
GRANT ALL ON copy_employees to name1,name2...
```
11. How can you find out what privileges you have been granted for columns in the tables belonging
to others?

# 17.2 

1. What is a role?
  - Role is predefined set of privleges 
2. What are the advantages of a role to a DBA?
  - Control what users have access too and changes they can make 
3. Give the ability to another user in your class to look at one of your tables. Give him the right to let
other students have that ability.
  
4. You are the DBA. You are creating many users who require the same system privileges. What
should you use to make your job easier?
  - Group together privleges into a role and assign the role to those people 
5. What is the syntax to accomplish the following?
  - Create a role of manager that has the privileges to select, insert, and update and delete from the employees table
    ```sql
      CREATE ROLE manager;
      GRANT SELECT, INSERT, UPDATE, DELETE ON employees TO manager;
    ```
  - Create a role of clerk that just has the privileges of select and insert on the employees table
    ```sql
      CREATE ROLE clerk;
      GRANT SELECT, INSERT ON employees TO clerk;
    ```
  - Grant the manager role to user scott
    ```sql
      GRANT manager to scott
    ```
  - Revoke the ability to delete from the employees table from the manager role
    ```sql
       REVOKE DELETE ON employees from manager
    ```
6. What is the purpose of a database link?


# 17.3 

1. Working with the employees table, and using regular expressions, write a query that returns
employees whose first names start with a “S” (uppercase) followed by either a “t” (lowercase) or
“h” (lowercase).
```sql
SELECT * FROM employees
WHERE REGEXP_LIKE(first_name, '^S(t|h)');
```
2. Investigate the LOCATIONS table.
   - Describe the table.
       ```sql
         Describe locations 
       ```
   - Perform a select that returns all rows and all columns of that table.
       ```sql
        SELECT * FROM locations 
       ```
   - Write a query using regular expressions that removes the spaces in the street_address column in the LOCATIONS table.
       ```sql
       SELECT street_address, REGEXP_REPLACE(street_address, ' ','') AS "NEW ADDRESS" FROM locations; 
       ```






















