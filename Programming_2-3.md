### 1.3.1

1. JOIN - Display data from two or more related tables.

2. A symbol used to perform an operation on some values.

3. An implementation of an attribute or relationship in a table.

4. PROJECTION - The capability in SQL to choose the columns in a table that you want returned from a query.

5. NULL - A value that is unavailable, unassigned, unknown, or inapplicable.

6. ALIAS - Renames a column heading.

7. A mathematical equation.

8. SELECTION - The capability in SQL to choose the rows in a table returned from a query.

9. SELECT STATEMENT - Retrieves information from the database

10. SELECT CLAUSE - Specifies the columns to be displayed

11. FROM CLAUSE - Specifies the table containing the column listed in the select clause

12. KEY WORD - An individual SQL command

13. CLAUSE - Part of a SQL statement

14. STATEMENT - A combination of the two clauses

### 1.3.2

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

















