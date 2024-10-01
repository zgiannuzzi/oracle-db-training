## 4.1 
#### Vocabulary 
- DUAL: Dummy table used to view results from functions and calculations
- Format:The arrangement of data for storage or display.
- ININCAP: Converts alpha character values to uppercase for the first letter of each word, all other letters in lowercase.
- Character: Functions that accept character data as input and can return both character and numeric values.
- TRIM: Removes all specified characters from either the beginning or the ending of a string.
- Experssion: A symbol that represents a quantity or a relationship between quantities
- Single-row: Functions that operate on single rows only and return one resultper row
- UPPER: Converts alpha characters to upper case
- Input: Raw data entered into the computer
- CONCAT: Concatenates the first character value to the second character value; equivalent to concatenation operator (||).
- Data that is processed into information
- LOWER: Converts alpha character values to lowercase.
- LPAD: Pads the left side of a character, resulting in a right-justified value
- SUBSTR: Returns specific characters from character value starting at a Specific character position and going specified character positions long
- REPLACE: Replaces a sequence of characters in a string with another set of characters.
- INSTR: Returns the numeric position of a named string.
- LENGTH: Returns the number of characters in the expression
- RPAD: Pads the right-hand side of a character, resulting in a left- justified value.

1. Using the three separate words “Oracle,” “Internet,” and “Academy,” use one command to produce the following output: The Best Class Oracle Internet Academy
   ```sql
      Select ('Oracle' || 'Internet' || 'Academy') as "The Best Class"
      from DUAL;
   ```
2. Use the string “Oracle Internet Academy” to produce the following output: The Net net
   ```sql
      Select SUBSTR('Oracle Internet Academy',13,3) as "The Net"
      from DUAL;
   ```
3. What is the length of the string “Oracle Internet Academy”?
   ```sql
      Select LENGTH('Oracle Internet Academy') 
      from DUAL;
   ```
   - length = 23
4. What’s the position of “I” in “Oracle Internet Academy”?
   ```sql
      Select INSTR('Oracle Internet Academy',I) 
      from DUAL;
   ```
   - I = 8
5. Starting with the string “Oracle Internet Academy”, pad the string to create "****Oracle****Internet****Academy****"
   ```sql
      Select LPAD('Oracle
      from DUAL;
   ```
6. Starting with the string “Oracle Internet Academy”, pad the string to produce: "Oracle$$$Internet$$$Academy"
   - Used the answer key answer 5 to help with 6
   ```sql
      Select RPAD('Oracle',9,'$') || RPAD('Internet',11,'$')|| 'Academy'
      from DUAL;
   ```
7. Using the string ‘Oracle Internet Academy’, produce the output shown using the REPLACE function. The Best Class Oracle 2013-2014 Academy
   ```sql
      Select REPLACE('Oracle Internet Academy','Internet','2013-2014') as "The Best Class
      from DUAL;
   ```
8. List the order date and the order total from the Global Fast Foods F_ORDERS table. Name the order total as TOTAL, and fill in the empty spaces to the left of the order total with $.
   ```sql
      Select order_date, LPAD(ORDER_TOTAL,10,'$') as "TOTAL" from f_orders;
   ```
9. Write a query that will output a column called “ADDRESS” which has the following information: ZOE TWEE 1009 OLIVER AVENUE BOSTON, MA 12889. Use the Global Fast Foods F_CUSTOMERS table.
   ```sql
   Select UPPER(first_name) ||' '|| UPPER(last_name) ||' '|| UPPER(address)||' ' ||UPPER(city) ||' ' ||UPPER(state)||' '||zip AS "ADDRESS" from f_customers WHERE id = 456;
   ```
10. Write a query to return the first character of the first name concatenated to the last_name, the
salary, and the department id for employees working in department 20. Give the first expression
an alias of Name. Use the EMPLOYEES table. Change the query to use a substitution variable
instead of the hard coded value 20 for department id. Run the query for department 30 and 50
without changing the original where-clause in your statement.

  ```sql
   Select SUBSTR(first_name,1,1) || last_name as "NAME", salary, department_id from employees where department_ID = 20
  ```
  ```sql
   Select SUBSTR(first_name,1,1) || last_name as "NAME", salary, department_id from employees where department_ID = :dept_id
  ```
11. Using a substitution variable for the department name, write a query listing department id,
department name, and location id for departments located in the_department_of_your_choice.
Use the DEPARTMENTS table. Note: All substitution variables in OAE are treated as character
strings, so no quotes (‘ ‘) are needed


## 4.2

1. TRUNC - Used to terminate the column, expression, or value to a specified number of decimal places
2. Number - These functions accept numeric input and return numeric values.
3. MOD - Returns the remainder of a division.
4. ROUND - Rounds the column, expression, or value to a set number of decimal places


1. Display Oracle database employee last_name and salary for employee_ids between 100 and 102.
Include a third column that divides each salary by 1.55 and rounds the result to two decimal
places

   ```sql
      Select last_name, salary, ROUND(salary/1.55,2) as "Salary divided by 1.55" from employee where emplyee_id BETWEEN 100 AND 102;
   ```
2. Display employee last_name and salary for those employees who work in department 80. Give
each of them a raise of 5.333% and truncate the result to two decimal places.
   ```sql
      Select last_name, salary, TRUNC(salary * 1.05333,2) as "Salary Raise" from employee where emplyee_id = 80 ;
   ```
3. Use a MOD number function to determine whether 38873 is an even number or an odd number.
   ```sql
      Select MOD(38873,2) from DUAL;
   ```
4. Use the DUAL table to process the following numbers:
   - 845.553 - round to one decimal place
     ```sql
      Select ROUND(845.553,1) from DUAL;
     ```
   - 30695.348 - round to two decimal places
     ```sql
      Select ROUND(30695.348,2) from DUAL;
     ```
   - 30695.348 - round to -2 decimal places
     ```sql
      Select ROUND(30695.348,-2) from DUAL;
     ```
   - 2.3454 - truncate the 454 from the decimal place
      ```sql
      Select ROUND(2.3454,1) from DUAL;
      ```
5. Divide each employee’s salary by 3. Display only those employees’ last names and salaries who
earn a salary that is a multiple of 3.
   
   ```sql
      Select last_name, salary/3 as "Employess salaries that can be divided by 3" from employee where MOD(salary,3) = 0;
   ```
6. Divide 34 by 8. Show only the remainder of the division. Name the output as EXAMPLE.
   ```sql
      Select MOD(34/8) as "EXAMPLE" from DUAL;
   ```
7. How would you like your paycheck – rounded or truncated? What if your paycheck was calculated
to be $565.784 for the week, but you noticed that it was issued for $565.78. The loss of .004 cent
would probably make very little difference to you. However, what if this was done to a thousand
people, a 100,000 people, or a million people! Would it make a difference then? How much
difference?


## 4.3 

1. SYSDATE - A function that returns the current date and time of the database server.
2. ADD_MONTHS - Add calendar months to date
3. LAST_DAY - Last day of the month
4. NEXT_DAY - Next day of the date specified
5. MONTHS_BETWEEN - Number of months between due dates

1. For DJs on Demand, display the number of months between the event_date of the Vigil wedding
and today’s date. Round to the nearest month.
   ```sql
      Select ROUND(MONTHS_BETWEEN(SYSDATE,event_date)) as "months" from d_events where ID = 105;
   ```
2. Display the days between the start of last summer’s school vacation break and the day school
started this year. Assume 30.5 days per month. Name the output “Days.”
   ```sql
      Select ROUND(MONTHS_BETWEEN('last day of summer vac','day school started')30.5) as "Days" from DUAL;
   ```
3. Display the days between January 1 and December 31
  ```sql
      Select ROUND(MONTHS_BETWEEN('31-DEC-2024','01-JAN-2024')30.5) as "Days" from DUAL;
  ```
4. Using one statement, round today's date to the nearest month and nearest year and truncate it to
the nearest month and nearest year. Use an alias for each column.


5. What is the last day of the month for June 2005? Use an alias for the output
   ```sql
      Select LAST_DAY(01-JUN-2005') as "last day of  June" from DUAL
   ```
6. Display the number of years between the Global Fast Foods employee Bob Miller’s birthday and
today. Round to the nearest year.
   ```sql
      Select MONTHS_BETWEEN(SYSDATE,birthdate)/12 as "number of years" from employee where employee_id = 9
   ```
7. Your next appointment with the dentist is six months from today. On what day will you go to the
dentist? Name the output, “Appointment.”
   ```sql
      Select ADD_MONTHS(SYSDATE,6) as "Appoinment" from DUAL
   ```
8. The teacher said you have until the last day of this month to turn in your research paper. What day
will this be? Name the output, “Deadline.”
   ```sql
      Select LAST_DAY(SYSDATE) as "Deadline" from DUAL
   ```
9. How many months between your birthday this year and January 1 next year
   ```sql
      Select MONTHS_BETWEEN('1-JAN-2025',19-JUN-2024) as "Months between Birthday" from DUAL
   ```
10.  What’s the date of the next Friday after your birthday this year
   ```sql
      Select NEXT_DAY('19-JUN-2024','FRIDAY') as "Next Friday" from DUAL
   ```
11. Name a date function that will return a number
    - MONTHS_BETWEEN

12. Name a date function that will return a date
    - NEXT_DAY
    - LAST_DAY
    - ADD_MONTHS

13. Give one example of why it is important for businesses to be able to manipulate date data
    - Note the date of when a medication is ordered. 

### Extension exercises

1. Using DUAL, write a statement that will convert 86.678 to 86.68
   ```sql
      Select ROUND(86.678,2) from DUAL;
   ```
2. Write a statement that will display the DJs on Demand CD titles for cd_numbers 90 and 91 in
uppercase in a column headed “DJs on Demand Collections.
   ```sql
      Select UPPER(title) as “DJs on Demand Collections" from d_cds where (cd_number = 90 or cd_number = 91);
   ```
3. Write a statement that will create computer usernames for the DJs on Demand partners. The
usernames will be the lowercase letters of the last name + the uppercase first letter in the first
name. Title the column “User Passwords.” For example, Mary Smythers would be smythersM.

4. Write a statement that will convert “It’s a small world” to “HELLO WORLD.”
   ```sql
      Select UPPER(CONCAT('hello',SUBSTR('Its a small world',13,18))) from DUAL;
   ```
5. Write a statement that will remove the “fiddle” from “fiddledeedee” and the “dum” from
“fiddledeedum.” Display the result “fiddledeedeedee” in a column with the heading “Nonsense.”

6. Replace every i in Mississippi with $.
   ```sql
      Select REPLACE('Mississippi','i','$') from DUAL 
   ```
7. Using DUAL, convert 5332.342 to 5300.
   ```sql
      Select ROUND(5332.342,-2) from DUAL 
   ```
8. Using DUAL, convert 3.14159 to 3.14.
   ```sql
      Select ROUND(3.14159,2) from DUAL 
   ```
9. Using DUAL, convert 73.892 to 73.8
   ```sql
      Select ROUND(73.892,1) from DUAL 
   ```
10. What is the next Friday six months from now? Label the column “Future.”
   ```sql
      Select NEXT_DAY(ADD_MONTHS(SYSDATE,6),'FRIDAY') as "FRIDAY 6 Months" from DUAL
   ```
11. What is the date 10 years from now
  - 12 * 10 = 120
   ```sql
      Select ADD_MONTHS(SYSDATE,120) from DUAL
   ```
12. Leap years occur every four years. Remember, 2004 was a leap year. Now create a function that
will show the date of the next leap year as 29-Feb-2008. Label the column “Future.”

13. Write a statement that will find any of the DJs on Demand CD themes that have an “ie” in their
names.
   ```sql
      Select description from d_themes where description LIKE '%ie%';
   ```
14. Write a statement that will return only the DJs on Demand CDs with years greater than 2000 but
less than 2003. Display both the title and year.
   ```sql
     select title, year from d_cds where year > 2000 AND year < 2003
   ```
15. Write a statement that will return the Oracle database employee’s employee ID and their starting
hire dates between January 1, 1997 and today. Display the result ordered from most recently
hired to the oldest.
   ```sql
     select employee_id, start_date from job_history where start_date between '01-Jan-1997'AND SYSDATE ORDER BY start_date DESC
   ```













   
