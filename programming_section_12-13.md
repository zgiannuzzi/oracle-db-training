## 12.1


### Vocabulary

1. Someone doing “real work” with the computer, using it as a means rather than an end
2. Consists of a collection of DML statements that form a logical unit of work.
3. Fully and clearly expressed; leaving nothing implied
4. Adds a new row to a table

## Exercise 

1. Give two examples of why it is important to be able to alter the data in a database.
  - Flexibility
  - record keeping
2. DJs on Demand just purchased four new CDs. Use an explicit INSERT statement to add each CD
to the copy_d_cds table. After completing the entries, execute a SELECT * statement to verify
your work.
```sql
INSERT INTO copy_d_cds (cd_number, tilte, producer, year)
VALUES(97, 'Celebrate the Day', 'R & B Inc.', 2003);

INSERT INTO copy_d_cds (cd_number, tilte, producer, year)
VALUES(98, 'Holiday Tunes for All Ages', 'Tunes are Us', 2004);

INSERT INTO copy_d_cds (cd_number, tilte, producer, year)
VALUES(99, 'Party Music', 'Old Town Records', 2004);

INSERT INTO copy_d_cds (cd_number, tilte, producer, year)
VALUES(100, 'Best of Rock and Roll', 'Old Town Records', 2004);

select * from copy_d_cds
```


3. DJs on Demand has two new events coming up. One event is a fall football party and the other
event is a sixties theme party. The DJs on Demand clients requested the songs shown in the table
for their events. Add these songs to the copy_d_songs table using an implicit INSERT statement.

```sql
INSERT INTO copy_d_songs
VALUES(52, 'Surfing Summer', 'Not known', 12);

INSERT INTO copy_d_songs 
VALUES(53, 'Victory Victory', '5 min', 12);

select * from copy_d_songs
```
4. Add the two new clients to the copy_d_clients table. Use either an implicit or an explicit INSERT

```sql
INSERT INTO copy_d_clients
VALUES(6655, 'Ayako', Dahish' ,3608859030, 'dahisha@harbor.net');

INSERT INTO copy_d_clients
VALUES(6689, 'Nick' ,'Neuville', 9048953049,'nnicky@charter.net');

select * from copy_d_clients
```

5. Add the new client’s events to the copy_d_events table. The cost of each event has not been
determined at this date.

```sql
INSERT INTO copy_d_events (ID, Name, Event_Date, Description, Cost, Venue_IDPackage_Code, Theme_Code, Client_Number)
VALUES(110, 'Ayako Anniversary' '07-Jul-2004', 'Party for 50, sixties dress, decorations', 245, 79, 240, 6655);

INSERT INTO copy_d_events (ID, Name, Event_Date, Description, Cost, Venue_IDPackage_Code, Theme_Code, Client_Number)
VALUES(15, 'Neuville Sports Banquet' '09-Sep-2004', 'Barbecue atresidence,collegealumni, 100 people', 315, 87, 340, 6689);

select * from copy_d_clients
```

6. Create a table called rep_email Populate this table by running a query on the employees table that includes only those employees
who are REP’s.

```sql
INSERT INTO rep_email (ID, first_name, last_name, email)
Select job_id, fist_name. last_name, email
from employee
where job_id contains(job_id,"REP")
```

## 12.2 


### Vocab

1. Modifies existing rows in a table
2. retrieves information from one table & uses the information toupdate another table
3. Ensures that the data adheres to a predefined set of rules
4. deletes information on a linked table based on what was deleted on the other table
5. Removes existing rows from a table

### Exercise

1. Monique Tuttle, the manager of Global Fast Foods, sent a memo requesting an immediate change
in prices. The price for a strawberry shake will be raised from $3.59 to $3.75, and the price for
fries will increase to $1.20. Make these changes to the copy_f_food_items table.

```sql
UPDATE copy_f_food_items 
SET price = 3.75
WHERE description = 'Strawberry Shake'

UPDATE copy_f_food_items 
SET price = 1.20
WHERE description = 'Fries'
```
2. Bob Miller and Sue Doe have been outstanding employees at Global Fast Foods. Management
has decided to reward them by increasing their overtime pay. Bob Miller will receive an additional
$0.75 per hour and Sue Doe will receive an additional $0.85 per hour. Update the copy_f_staffs
table to show these new values. (Note: Bob Miller currently doesn’t get overtime pay. What
function do you need to use to convert a null value to 0?)

```sql
UPDATE copy_f_staffs
SET overtime_rate = Overtime_rate + 0.75
WHERE ID = 12 

UPDATE copy_f_staffs
SET overtime_rate = Overtime_rate + 0.85
WHERE ID = 9 
```

3. Add the orders shown to the Global Fast Foods copy_f_orders table:

```sql
 Insert into copy_f_orders
 (5678,TO_DATE('09-23-2004','mm-dd-yyyy'),145.98,225,12);



```
4. Add the new customers shown below to the copy_f_customers table. You may already have
added Katie Hernandez. Will you be able to add all these records successfully?
- Last query would not work becuase zip code cannot be null
```sql
INSERT INTO copy_f_customers
VALUES(145, 'katie', 'Hernandez' ,'92 chico way','los angeles','CA',98008, '8586667641');

INSERT INTO copy_f_customers
VALUES(145, 'katie', 'Hernandez' ,'92 chico way','DENVER','CO',80291, '7193343523');

INSERT INTO copy_f_customers
VALUES(225, 'Devin', 'Spode' ,'1923 Silverado','los angeles','CA',98008, '8586667641');

INSERT INTO copy_f_customers
VALUES(225, 'Adam', 'Zurn' ,'5 Admiral Way','Seattle','WA', '4258879009');
```

5. Sue Doe has been an outstanding Global Foods staff member and has been given a salary raise.
She will now be paid the same as Bob Miller. Update her record in copy_f_staffs.
```sql
UPDATE copy_f_staffs
Set Salary = (select salary from copy_f_staffs where ID = 9)
where ID = 12
```

6. Global Fast Foods is expanding their staff. The manager, Monique Tuttle, has hired Kai Kim. Not
all information is available at this time, but add the information shown here
INSERT INTO copy_f_customers
```sql
INSERT INTO copy_f_staff
VALUES(25, 'Kai', 'Kim' ,TO_DATE('03-11-1998','dd-mm-yyyy'),6.75,'Order taker');
```

7. Now that all the information is available for Kai Kim, update his Global Fast Foods record to
include the following: Kai will have the same manager as Sue Doe. He does not qualify for
overtime. Leave the values for training, manager budget, and manager target as null.
```sql
UPDATE copy_f_staffs
Set Manager_Id = (select Manager_id from copy_f_staffs where ID = 12)
where ID = 25
```
8. Execute the following SQL statement. Record your results.
```sql
DELETE from departments
WHERE department_id = 60;

#Removes IT department from departments table 
```

9. Kim Kai has decided to go back to college and does not have the time to work and go to school.
Delete him from the Global Fast Foods staff. Verify that the change was made.

```sql
DELETE from copy_f_staffs
WHERE id = 25;
```
10. Create a copy of the employees table and call it lesson7_emp;
Once this table exists, write a correlated delete statement that will delete any employees from the
lesson7_employees table that also exist in the job_history table.

```sql
DELETE from lesson7_emp
WHERE id = (select id from job history)
```
## 12.3

### Exercise

1. When would you want a DEFAULT value?
   -In the event that a new row is inserted and no value for
    the column is assigned, the default value will be
    assigned instead of a null value.
   - So your table does not contain null values


2. Currently, the Global Foods F_PROMOTIONAL_MENUS table START_DATE column does not
have SYSDATE set as DEFAULT. Your manager has decided she would like to be able to set the
starting date of promotions to the current day for some entries. This will require three steps:

- created table 
- Altered start date 
``` sql
INSERT INTO copy_f_promotional 
VALUES(120, ‘New Customer.’, 'Kim' ,DEFAULT ,'01-Jun-2005','10%');
```

3. Allison Plumb, the event planning manager for DJs on Demand, has just given you the following
list of CDs she acquired from a company going out of business. She wants a new updated list of
CDs in inventory in an hour, but she doesn’t want the original D_CDS table changed. Prepare an
updated inventory list just for her.

```sql


```

5. Run the following 3 statements to create 3 new tables for use in a Multi-table insert statement. All
3 tables should be empty on creation, hence the WHERE 1=2 condition in the WHERE clause.

## 13.1

### Vocab

1. Created and maintained by the Oracle Server and contains information about the database
2. A collection of objects that are the logical structures that directly refer to the data in the database
3. Specifies a preset value if a value is omitted in the INSERT statement
4. Stores data; basic unit of storage composed of rows and columns
5. Command use to make a new table

### Exercise 
1. Complete the GRADUATE CANDIDATE table instance chart. Credits is a foreign-key column
referencing the requirements table

- Student_id 
  - Key type
  - nulls/unique
  - FK column
  - Data type
  - length 

- last_name
  - Key type
  - nulls/unique
  - FK column
  - Data type
  - length 

- First_name
  - Key type
  - nulls/unique
  - FK column
  - Data type
  - length 

- Credits
  - Key type
  - nulls/unique
  - FK column
  - Data type
  - length
    
- Graduation_date
  - Key type
  - nulls/unique
  - FK column
  - Data type
  - length 
2. Write the syntax to create the grad_candidates table.
```sql
CREATE TABLE "grad_candidates"
  ("Student_id" NUMBER(6),
   "last_name" Varchar2(20),
   "first_name" Varchar2(20),
   "credits" NUMBER(3),
   "gradutation_date" DATE,
```    
3. Confirm creation of the table using DESCRIBE.
```sql
Describe  grad_candidates;
```
4. Create a new table using a subquery. Name the new table your last name -- e.g., smith_table.
Using a subquery, copy grad_candidates into smith_table
```sql
COPY TABLE "grad_candidates"
"giannuzzi"
```
5. Insert your personal data into the table created in question 4.
```sql
INSERT INTO giannuzzi
Select * from grad_candidates
```
6. Query the data dictionary for each of the following:

## 13.2 

1. Allows time to be stored as an interval of years and months
2. When a column is selected in a SQL statement the time is automatically converted to the user’s timezone
3. Binary large object data up to 4 gigabytes
4. Stores a time zone value as a displacement from Universal Coordinated Time or UCT
5. Allows time to be stored as an interval of days to hours, minutes, and seconds
6. Character data up to 4 gigabytes
7. Allows the time to be stored as a date with fractional seconds

### Exercise 

1. Create tables using each of the listed time-zone data types, use your time-zone and one other in
your examples. Answers will vary
```sql
CREATE TABLE question_1
(first_column TIMESTAMP WITH LOCAL TIME ZONE,
 second_column INTERVAL YEAR(3) TO MONTH,
 third_column INTERVAL DAY(3) TO SECOND);

Select * from question_1
```
- 1 with flights and how they are scheduled its important you are using the time zone where your flight is coming out of
- 2 Delevery dates and times could be affected
- 3 Meeetings and phone calls for being awarre of time differences

### 13.3 

1. Why is it important to be able to modify a table?
   - saves time
   - Flexibility
2. CREATE a table called Artists.
```sql
CREATE TABLE Artists
(artist_ID Number(3)
 first_name Varchar2(20)
 last_name  Varchar2(20)
 band_name  Varchar2(35)
 email Varchar2(35)
 hourly_rate Number(3)


insert into Artists
VALUES(1, 'test' , 'testing' ,'The Hobbits','test@test.email',50);

insert into Artists
VALUES(2, 'test2' , 'testing2' ,'The bobbits','test2@test.email',80);

Alter table "Artists" ADD CONSTRAINT "T_artist_FK"" FOREIGN KEY ("artist_id")
DROP TABLE Artists
Rename Artists to ARTISTS
TRUNCATE TABLE ARTISTS
COMMENT ON TABLE ARTISTS
IS 'This is a table;
```

3. In your o_employees table, enter a new column called “Termination.” The datatype for the new
column should be VARCHAR2. Set the DEFAULT for this column as SYSDATE to appear as
character data in the format: February 20th, 2003.

```sql
ALTER TABLE o_employees
ADD Termination varchar2(30) DEFAULT TO_DATE(SYSDATE,'mm-dd-yyyy');
```
4. Create a new column in the o_employees table called start_date. Use the TIMESTAMP WITH
LOCAL TIME ZONE as the datatype

```sql
ALTER TABLE o_employees
ADD start_date DATE TIMESTAMP WITH LOCAL TIME ZONE;
```


5. Truncate the o_jobs table. Then do a SELECT * statement.
Are the columns still there? Is the data still there?
```sql
ALTER TABLE o_employees
ADD start_date DATE TIMESTAMP WITH LOCAL TIME ZONE;
```


6. What is the distinction between TRUNCATE, DELETE, and DROP for tables?
 - Truncating a table removes all rows from a table and releases the storage space used by that table
 - Deleteing is the same as truncating but it does not remove storage space
 - The DROP TABLE statement removes the definition of an Oracle table. Only the creator of the table or a user with DROP ANY TABLE privilege (usually only the DBA) can remove a table
   
7. List the changes that can and cannot be made to a column.
 - Change the name
 - Add a column
 - remove a column 

8. Add the following comment to the o_jobs table:
```sql
COMMENT ON TABLE o_jobs
IS 'New job description added;
```

9. Rename the o_jobs table to o_job_description.
```sql
RENAME o_jobs to o_job_description
```

10. F_staffs table exercises
11. Still working with the copy_f_staffs table, perform an update on the table

- ```sql
  Select * From copy_f_staffs
  ```
- ```sql
  update copy_f_staffs
  set salary = 500000
  where ID = 12
  commit 
  ```
- ```sql
  Select * From copy_f_staffs
  ```
- ```sql
  update copy_f_staffs
  set salary = 2
  where ID = 12
  commit
  ```

- ```sql
  Select * From copy_f_staffs
  ```
- ```sql
   FLASHBACK TABLE copy_f_staffs TO BEFORE DROP;
  ```
- ```sql
   FLASHBACK TABLE copy_f_staffs TO BEFORE DROP;
  ```















