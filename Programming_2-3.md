### 1.3.1

JOIN - Display data from two or more related tables.

A symbol used to perform an operation on some values.

An implementation of an attribute or relationship in a table.

PROJECTION - The capability in SQL to choose the columns in a table that you want returned from a query.

NULL - A value that is unavailable, unassigned, unknown, or inapplicable.

ALIAS - Renames a column heading.

A mathematical equation.

SELECTION - The capability in SQL to choose the rows in a table returned from a query.

SELECT STATEMENT - Retrieves information from the database

SELECT CLAUSE - Specifies the columns to be displayed

FROM CLAUSE - Specifies the table containing the column listed in the select clause

KEY WORD - An individual SQL command

CLAUSE - Part of a SQL statement

STATEMENT - A combination of the two clauses

#### 1.3.2

1. Write a SQL statement that demonstrates projection.


2. Write a query that displays the last_name and email addresses for all the people in the DJs on
Demand d_client table. The column headings should appear as “Client” and “Email Address.”


3. The manager of Global Fast Foods decided to give all employees at 5%/hour raise + a $.50
bonus/hour. However, when he looked at the results, he couldn't figure out why the new raises
were not as he predicted. Ms. Doe should have a new salary of $7.59, Mr. Miller's salary should
be $11.00, and Monique Tuttle should be $63.50.
He used the following query. What should he have done? SELECT last_name, salary *.05 +.50 FROM f_staffs;


4. Which of the following would be the easiest way to see all rows in the d_songs table?
a. SELECT id, title, duration, artist, type_code
b. SELECT columns
c. SELECT *
d. SELECT all

5. If tax = 8.5% * car_cost and license = car_cost * .01%, which value will produce the largest car
payment?
a. Payment = (car_cost * 1.25) + 5.00 - (tax) - (license)
b. Payment = car_cost * 1.25 + 5.00 - (tax - license)

6. In the example below, identify the keywords, the clause(s), and the statement(s):
SELECT employee_id, last_name
FROM employees


7. Label each example as SELECTION or PROJECTION.
a. Please give me Mary Adam's email address.
b. I would like only the manager_id column, and none of the other columns.

8. Which of the following statements are true?
a. null * 25 = 0;
b. null * 6.00 = 6.00
c. null * .05 = null
d. (null + 1.00) + 5.00 = 5.00

9. How will the column headings be labeled in the following example?
SELECT bear_id bears, color AS Color, age “age”
FROM animals;
a. bears, color, age
b. BEARS, COLOR, AGE
c. BEARS, COLOR, age
d. Bears, Color, Age


10. Which of the following words must be in a SELECT statement in order to return all rows?
a. SELECT only
b. SELECT and FROM
c. FROM only
d. SELECT * only

















