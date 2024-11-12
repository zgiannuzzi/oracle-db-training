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
















