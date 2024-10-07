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













