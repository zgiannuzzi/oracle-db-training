### 1.3.1

1.  JOIN - Display data from two or more related tables.

2.  A symbol used to perform an operation on some values.

3.  An implementation of an attribute or relationship in a table.

4.  PROJECTION - The capability in SQL to choose the columns in a table that you want returned from a query.

5.  NULL - A value that is unavailable, unassigned, unknown, or inapplicable.

6.  ALIAS - Renames a column heading.

7.  A mathematical equation.

8.  SELECTION - The capability in SQL to choose the rows in a table returned from a query.

9.  SELECT STATEMENT - Retrieves information from the database

10.  SELECT CLAUSE - Specifies the columns to be displayed

11.  FROM CLAUSE - Specifies the table containing the column listed in the select clause

12.  KEY WORD - An individual SQL command

13.  CLAUSE - Part of a SQL statement

14.  STATEMENT - A combination of the two clauses

### 2.1

1. Write a SQL statement that demonstrates projection.
 - SELECT FIRST_NAME FROM student

2. Write a query that displays the last_name and email addresses for all the people in the DJs on
Demand d_client table. The column headings should appear as “Client” and “Email Address.”
 - SELECT last_name as "Client", email as "Email Address" FROM d_client;

3. The manager of Global Fast Foods decided to give all employees at 5%/hour raise + a $.50
bonus/hour. However, when he looked at the results, he couldn't figure out why the new raises
were not as he predicted. Ms. Doe should have a new salary of $7.59, Mr. Miller's salary should
be $11.00, and Monique Tuttle should be $63.50.
He used the following query. What should he have done? SELECT last_name, salary *.05 +.50 FROM f_staffs;
 - SELECT last_name, salary *(.05 +.50) FROM f_staffs;

4. Which of the following would be the easiest way to see all rows in the d_songs table.
 - c. SELECT *

5. If tax = 8.5% * car_cost and license = car_cost * .01%, which value will produce the largest carpayment?
 - b. Payment = car_cost * 1.25 + 5.00 - (tax - license)

6. In the example below, identify the keywords, the clause(s), and the statement(s):
  - SELECT and FROM = KEYWORDS
  - SELECT employee_id, last_name and FROM employees  = CLAUSES
  - SELECT employee_id, last_name FROM employees = STATEMENT


7. Label each example as SELECTION or PROJECTION.
 - Please give me Mary Adam's email address = SELECTION
 - I would like only the manager_id column, and none of the other columns = PROJECTION 

8. Which of the following statements are true?
 - c. null * .05 = null 

9. How will the column headings be labeled in the following example? SELECT bear_id bears, color AS Color, age “age” FROM animals;
- BEARS, COLOR, age

10. Which of the following words must be in a SELECT statement in order to return all rows?
- b. SELECT and FROM 

### 2.1.3

1. DISTINCT - A command that suppresses duplicates
2. Concatenation - Links two columns together to form one character data column
3. Character String - A group of character data
4. DESC (DESCRIBE) - An SQL plus command that displays the structure of a table


1. The manager of Global Fast Foods would like to send out coupons for the upcoming sale. He wants to send one coupon to each household. Create the SELECT statement that returns the
customer last name and a mailing address.
 ``` sql
    Select DISTINCT last_name, address from CUSTOMER
 ```
3. Each statement below has errors. Correct the errors and execute the query in Oracle Application Express.
  - SELECT first name FROM f_staffs;
    -  ``` sql
         SELECT first_name FROM f_staffs;
       ```
  - SELECT first_name |" " | last_name AS "DJs on Demand Clients" FROM d_clients;
    -  ``` sql
         SELECT first_name || " " || last_name AS "DJs on Demand Clients" FROM d_clients;
       ```
  - SELECT DISCTINCT f_order_lines FROM quantity;
    -   ``` sql
         SELECT DISTINCT f_order_lines FROM quantitys;
        ```
 - SELECT order number FROM f_orders;
    -   ``` sql
         SELECT order_number FROM f_orders;
        ```
5. Sue, Bob, and Monique were the employees of the month. Using the f_staffs table, create a SELECT statement to display the results as shown in the Super Star chart.
Super Star
*** Sue *** Sue ***
*** Bob *** Bob ***
*** Monique *** Monique ***

6. Which of the following is TRUE about the following query?
SELECT first_name, DISTINCT birthdate FROM f_staffs;
a. Only two rows will be returned.
b. Four rows will be returned.
c. Only Fred 05-Jan-1988 and Lizzie 10-Nov-1987 will be returned.
d. No rows will be returned.

7. Global Fast Foods has decided to give all staff members a 5% raise. Prepare a report that presents the output as shown in the chart. EMPLOYEE LAST NAME CURRENT SALARY SALARY WITH 5% RAISE
   
8. Create a query that will return the structure of the Oracle database EMPLOYEES table. Which
columns are marked “nullable”? What does this mean?

9. The owners of DJs on Demand would like a report of all items in their D_CDs table with the
following column headings: Inventory Item, CD Title, Music Producer, and Year Purchased.
Prepare this report.

10. True/False -- The following SELECT statement executes successfully:
 - SELECT last_name, job_id, salary AS Sal FROM employees;
   - TRUE
11. True/False -- The following SELECT statement executes successfully:
  - SELECT * FROM job_grades;
   - TRUE

12. There are four coding errors in this statement. Can you identify them?
 - SELECT employee_id, last_name sal x 12 ANNUAL SALARY FROM employees;
   ``` sql
        SELECT employee_id, last_name, (salary * 12) as ANNUAL SALARY FROM employees;
   ```
13. In the arithmetic expression salary*12 - 400, which operation will be evaluated first?
  - Salary * 12

14. Which of the following can be used in the SELECT statement to return all columns of data in the Global Fast Foods f_staffs table?
 - both a and b

15. Using SQL to choose the columns in a table uses which capability?
 - projection

16. SELECT last_name AS "Employee". The column heading in the query result will appear as:
 - Employee

17. Which expression below will produce the largest value?
- SELECT salary*6 + 100

18. Which statement below will return a list of employees in the following format? Mr./Ms. Steven King is an employee of our company.
- SELECT 'Mr./Ms. '||first_name||' '||last_name ||' '||'is an employee of our company.' AS "Employees" FROM employees ;

20. Which is true about SQL statements?
a. SQL statements are case-sensitive - TRUE 
b. SQL clauses should not be written on separate lines. FALSE 
c. Keywords cannot be abbreviated or split across lines. TRUE 
d. SQL keywords are typically entered in lowercase; all other words in uppercase. FALSE 

21. Which queries will return three columns each with UPPERCASE column headings?
  - SELECT department_id, last_name, first_name AS UPPER CASE FROM employees

22. Which statement below will likely fail?
 - SELCT * FROM employees;


23. Click on the History link at the bottom of the SQL Commands window. Scroll or use the arrows at
the bottom of the page to find the statement you wrote to solve problem 3 above. (The one with
the column heading SuperStar). Click on the statement to load it back into the command window.
Execute the command again, just to make sure it is the correct one that works. Once you know it
works, click on the SAVE button in the top right corner of the SQL Commands window, and enter a
name for your saved statement. Use your own initials and “_superstar.sql”, so if your initials are
CT then the filename will be CT_superstar.sql.
Log out of OAE, and log in again immediately. Navigate back to the SQL Commands window,
click the Saved SQL link at the bottom of the page and load your saved SQL statement into the
Edit window. This is done by clicking on the script name. Edit the statement, to make it display +
instead of *. Run your amended statement and save it as initials_superplus.sql.

### 2.2

WHERE - Restricts the rows returned by a select statement
OPERATORS - Compares one expression to another value or expression

1. Using the Global Fast Foods database, retrieve the customer’s first name, last name, and address for the customer who uses ID 456.
    ``` sql
        SELECT first_name, last_name, address FROM f_customer WHERE ID = 456;
    ```
2. Show the name, start date, and end date for Global Fast Foods' promotional item “ballpen and highlighter” giveaway.
    ``` sql
        SELECT name, start_date, end_date FROM f_promotional_menus WHERE give_away = 'ballpen and highlighter';
    ```
3. Create a SQL statement that produces the following output: Oldest The 1997 recording in our database is The Celebrants Live in Concert

4. The following query was supposed to return the CD title “Carpe Diem" but no rows were returned. Correct the mistake in the statement and show the output.
    ``` sql
        SELECT produce, title
        FROM d_cds
        WHERE title = 'carpe diem' ;
    ```
    ``` sql
        SELECT produce, title
        FROM d_cds
        WHERE title = 'Carpe Diem' ;
    ```

6. The manager of DJs on Demand would like a report of all the CD titles and years of CDs that were
produced before 2000.
    ``` sql
        SELECT year, title
        FROM d_cds
        WHERE year < 2000 ;
    ```

8. Which values will be selected in the following query?
SELECT salary FROM employees WHERE salary <= 5000;
- b. 0 - 4999

For the next three questions, use the following table information:
TABLE NAME: students
COLUMNS:
studentno NUMBER(6)
fname VARCHAR2(12)
lname VARCHAR(20)
sex CHAR(1)
major VARCHAR2(24)


9. Write a SQL statement that will display the student number (studentno), first name (fname), and last name (lname) for all students who are female (F) in the table named students.
 ``` sql
       SELECT studentno, fname, lname FROM students where sex = 'F'
 ```
11. Write a SQL statement that will display the student number (studentno) of any student who has a PE major in the table named students. Title the studentno column Student Number.
 ``` sql
       SELECT studentno as "Student Number" FROM students where major = 'PE'
 ```
13. Write a SQL statement that lists all information about all male students in the table named students.
 ``` sql
       SELECT * FROM students where sex = 'M'
 ```
15. Write a SQL statement that will list the titles and years of all the DJs on Demand CDs that were not produced in 2000.
 ``` sql
       SELECT title, year FROM d_cds where year != 2000
 ```
17. Write a SQL statement that lists the Global Fast Foods employees who were born before 1980
 ``` sql
       SELECT first_name, last_name FROM f_staff where birthdate < 1980 
 ```
### 2.3 

1. ESCAPE - This option identifies that the escape characters should be interpreted literally
2. IS NULL - Condition tests for null values
3. BETWEEN...AND - Displays rows based on a range of values
4. inclusive - Including the specified limits and the area between them; the numbers 1-10, inclusive
5. LIKE - Selects rows that match a character pattern
6. IN - Tests for values in a specified list of values

1. Display the first name, last name, and salary of all Global Fast Foods staff whose salary is
between $5.00 and $10.00 per hour.
   ``` sql
       SELECT first_name, Last_name, salary FROM employees where salary between 5.00 and 10.00
   ```
3. Display the location type and comments for all DJs on Demand venues that are Private Home.
   ``` sql
       SELECT loc_type, comments FROM d_venues where loc_type = 'Private Home' '_o%'
   ```
5. Using only the less than, equal, or greater than operators, rewrite the following query:
   ``` sql
       SELECT first_name, last_name
       FROM f_staffs
       WHERE salary BETWEEN 20.00 and 60.00;
   ```
   ``` sql
       SELECT first_name, last_name
       FROM f_staffs
       WHERE salary >= 20.00 and <= 60.00;
   ```
7. Create a list of all the DJs on Demand CD titles that have “a” as the second letter in the title.
   ``` sql
       SELECT first_name, last_name FROM d_partners where title LIKE '_a%'
   ```
8. Who are the partners of DJs on Demand who do not get an authorized expense amount?
   ``` sql
       SELECT first_name, last_name FROM d_partners where auth_expense_amt IS NULL
   ```
10. Select all the Oracle database employees whose last names end with “s”. Change the heading of the column to read Possible Candidates.
   ``` sql
       SELECT  last_name as "Possible Candidates" FROM employees where last_name LIKE '%_s'
   ```
12. Which statement(s) are valid?
  -  WHERE quantity = NULL;
  -  WHERE quantity IS NULL;
  -  WHERE quantity != NULL;

13. Write a SQL statement that lists the songs in the DJs on Demand inventory that are type code 77, 12, or 1.
   ``` sql
       SELECT title FROM d_songs where ID IN (77,12,1)
   ```




