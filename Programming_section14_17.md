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








