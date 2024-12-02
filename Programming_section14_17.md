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




