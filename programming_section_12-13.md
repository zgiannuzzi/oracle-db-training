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








