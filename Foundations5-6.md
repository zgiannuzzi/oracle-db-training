# Foundations 5-6

### 6.6

1. Write a simple query to view the data inserted in the tables created for the academic database
``` sql
  select * From *
```
2. Write a query to retrieve the exam grade obtained by each student for every exam attemptep.
``` sql
  select EXAM_GRADE From AD_EXAM_RESULTS 
```
3. Write a query to check if a student is eligible to take exams based on the number of days he/she attended classes.
``` sql
  select EXAM_ELIGIBILITY From AD_STUDENT_ATTENDANCE
```
4. Display the LOGIN_DATE_TIME for each faculty member.
``` sql
  select LOGIN_DATE_TIME From AD_FACULTY_LOGIN_DETAILS
```
5. Display the name of the Head of the Department for each of the Departments.
``` sql
  select HEAD From AD_DEPARTMENTS
```
6. Retrieve the student ID and first name for each student concatenated with literal text to look like this:
720: FIRST NAME IS JACK
``` sql
  select HEAD From AD_DEPARTMENTS
```
7. Display all the distinct exam types from the AD_EXAMS table.
``` sql
  select EXAM_TYPE From AD_EXAMS
```

### 6.7

1. Display the course details for the Spring Session.
``` sql
  select * From AD_COURSES WHERE SESSION_ID = 100
```
3. Display the details of the students who have scored more than 95.
``` sql
  select * From AD_EXAM_RESULTS Where EXAM_GRADE > 95
```
5. Display the details of the students who have scored between 65 and 70.
``` sql
  select * From AD_EXAM_RESULTS Where EXAM_GRADE BETWEEN 65 AND 70
```
7. Display the students who registered after 01-Jun-2012.
``` sql
  select * From AD_STUDENTS Where REG_YEAR BETWEEN '02-Jun-2012' and CURDATE 
```
9. Display the course details for departments 10 and 30.
``` sql
  select * From AD_COURSES WHERE DEPT_ID = 10 or DEPT_ID - 30
```
11. Display the details of students whose first name begins with the letter "J".
``` sql
  select HEAD From AD_DEPARTMENTS
```
13. Display the details of students who have opted for courses 190 or 193.
``` sql
  select * From AD_COURSES WHERE DEPT_ID = 10 or DEPT_ID - 30
```
15. Display the course details offered by department 30 for the Fall Session (Session ID 200)
``` sql
  select * From AD_COURSES WHERE (DEPT_ID = 30 and SESSION_ID = 200)
```
17. Display the course details of courses not being offered in the summer and fall session (Session ID 200 and 300).
``` sql
  select * From AD_COURSES WHERE (DEPT_ID = 30 and SESSION_ID = 200)
```
19. Display the course details for department 20.
``` sql
  select * From AD_COURSES WHERE DEPT_ID = 20
```



