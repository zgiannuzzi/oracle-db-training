## 5.1

1. CHAR - Used for text and character data of fixed length, including numbers, dashes, and special characters.
2. Used to remove padded blanks or to suppress leading zeros
3. Conversion - Functions that convert a value from one datatype to another.
4. NUMBER - Used to store variable-length numeric data.
5. VARCHAR2 - Used for character data of variable length, including numbers, special characters, and dashes.
6. DATE - Used for date and time values.
7. TO_CHAR - Converts dates or numbers to character strings with optional formatting
8. Century value depends on the specified year and the last two digits of the current year
9. TO_NUMBER - Converts a character string containing digits to a number with optional formatting
10. Numeric day of the month
11. TO_DAte- Converts a character string representing a date to a date value with optional formatting


### Exercise 1

1. List the last names and birthdays of Global Fast Food Employees. Convert the birth dates to character data in the Month DD, YYYY format. Suppress any leading zeros.
```sql
    Select last_name, TO_CHAR(birthday,  'Month dd, YYYY') from employees 
```
2. Convert January 3, 04, to the default date format 03-Jan-2004.
```sql
    SELECT TO_DATE('January 3, 04','fxMonth dd, YYYY') AS "Date" FROM DUAL; 
```

3. Format a query from the Global Fast Foods f_promotional_menus table to print out the start_date of promotional code 110 as: The promotion began on the tenth of February 2004.
```sql

```
4. Convert today’s date to a format such as: “Today is the Twentieth of March, Two Thousand Four”
```sql
    Select TO_CHAR(SYSDATE,'"today is the" fmDay, ddthsp "of" Month, Year') From DUAL
```
6. List the ID, name, and salary for all Global Fast Foods employees. Display salary with a $ sign
and two decimal places.
```sql
    Select ID,name, TO_CHAR(salary, '$99,999.99') AS "Salary" FROM employees;
```
8. Ellen Abel is an employee who has received a $2,000 raise. Display her first name and last name,
her current salary, and her new salary. Display both salaries with a $ and two decimal places.
Label her new salary column AS New Salary.
```sql
    Select first_name,last_name, TO_CHAR(salary, '$99,999.99') AS "Salary", TO_CHAR(salary + 2000, '$99,999.99') AS "New Salary" FROM employees;
```
10. On what day of the week and date did Global Fast Foods’ promotional code 110 Valentine’s
Special begin?

11. Create one query that will convert 25-Dec-2004 into each of the following (you will have to convert
25-Dec-2004 to a date and then to character data):
December 25th, 2004
DECEMBER 25TH, 2004
25th december, 2004
```sql
    Select TO_CHAR(25-Dec-2004, 'Month ddth, YYYY') as "normal", TO_CHAR(25-Dec-2004, 'MONTH DDTH, YYYY') as "uppercase", TO_CHAR(25-Dec-2004, 'ddth month, YYYY') as "lowercase" From DUAL;
```
13. Create a query that will format the DJs on Demand d_packages columns, low-range and high-
range package costs, in the format $2500.00.
```sql
    Select ID,name, TO_CHAR(salary, '$99,999.99') AS "Salary" FROM employees;
```
15. Convert JUNE192004 to a date using the fx format model.
```sql
    Select TO_DATE('JUNE192004', 'fxMonDD,YYYY') AS "Salary" FROM DUAL;
```
17. What is the distinction between implicit and explicit datatype conversion? Give an example of each.
    - Implicit datatypes are ones that the system can automatically identify
    - Explicit is you telling the system what type it should be.
19. Why is it important from a business perspective to have datatype conversions?
    - Some cercumstances can make things more readable
    - Makes systems more flexible.
   
## 5.2

1. NVL - Converts nulls to an actual value
2. Returns the first non-null expression in the list
3. NVL2 - Examines the first expression; if the first expression is not null, it returns the second expression; if the first expression is null, it returns the third expression
4. NULLIF - Compares two expressions; if they are equal, the function returns null; if they are not equal, the function returns the first expression

1. Create a report that shows the Global Fast Foods promotional name, start date, and end date
from the f_promotional_menus table. If there is an end date, temporarily replace it with “end in two
weeks.” If there is no end date, replace it with today’s date.
```sql
    Select name, start_date, end_date from f_promotional_menus 
```

2. Not all Global Fast Foods staff members receive overtime pay. Instead of displaying a null value
for these employees, replace null with zero. Include the employee’s last name and overtime rate in
the output. Label the overtime rate as “Overtime Status”.
```sql
    Select last_name, NVL(overtime_rate, 0) as "Overtime Status" from f_staffs
```

4. The manager of Global Fast Foods has decided to give all staff who currently do not earn
overtime an overtime rate of $5.00. Construct a query that displays the last names and the
overtime rate for each staff member, substituting $5.00 for each null overtime value.

```sql
    Select last_name, NVL(overtime_rate, '$5.00') as "RATE" from f_staffs
```
5. Not all Global Fast Foods staff members have a manager. Create a query that displays the
employee last name and 9999 in the manager ID column for these employees.
```sql
    Select last_name, NVL(MANAGER_ID, 9999) as "no manager" from f_staffs
```

6. Which statement(s) below will return null if the value of v_sal is 50?
d. SELECT coalesce (v_sal, Null, 50) FROM emp;

7. What does this query on the Global Fast Foods table return?
SELECT COALESCE(last_name, to_char(manager_id)) as NAME
FROM f_staffs;
 - Displays last name and manager ID if both values are not null

8.
a. Create a report listing the first and last names and month of hire for all employees in the
EMPLOYEES table (use TO_CHAR to convert hire_date to display the month).
```sql
    Select first_name, last_name, TO_CHAR(hire_date, 'Month') from employees
```
b. Modify the report to display null if the month of hire is September. Use the NULLIF function.
```sql
    Select first_name, last_name, NULLIF(TO_CHAR(hire_date, 'Month'),'September') from employees
```

10. For all null values in the specialty column in the DJs on Demand d_partners table, substitute “No
Specialty.” Show the first name and s

```sql
    Select first_name, NVL(Specialty,"NO Specialty") from d_partners
```

## 5.3

1. DECODE - Compares an expression to each of the search values
2. CONDITIONAL - An if-then-else expression whose value depends on the truth- value of a Boolean expression.
3. CASE - Implements conditional processing within a SQL statement; it meets the ANSI standard.

1. From the DJs on Demand d_songs table, create a query that replaces the 2-minute songs with
“shortest” and the 10-minute songs with “longest”. Label the output column “Play Times”.
```sql
    Select DECODE(duration, '2-minute',"shortest", '10-minute', "longest") from d_songs
```

2. Use the Oracle database employees table and CASE expression to decode the department id.
Display the department id, last name, salary, and a column called “New Salary” whose value is
based on the following conditions:
If the department id is 10 then 1.25 * salary
If the department id is 90 then 1.5 * salary
If the department id is 130 then 1.75 * salary
Otherwise, display the old salary.
```sql
    Select last_name,
           CASE department_id
              WHEN 10 THEN salary * 1.25
              WHEN 90 THEN salary * 1.5
              WHEN 130 THEN salary * 1.75
              ELSE salary
              END AS "New Salary"
FROM employees;
```
3. Display the first name, last name, manager ID, and commission percentage of all employees in
departments 80 and 90. In a 5th column called “Review”, again display the manager ID. If they
don’t have a manager, display the commission percentage. If they don’t have a commission,
display 99999.
 ```sql
    Select DECODE(duration, '2-minute',"shortest", '10-minute', "longest") from d_songs
```





