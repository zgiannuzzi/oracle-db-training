# Foundations 5-6
### 5.1
#### EXERCISE 1
Create Glossary 
![Image of Glossary](https://github.com/zgiannuzzi/oracle-db-training/blob/main/db_Glossary.PNG)


#### EXERCISE 2
1.
![Image of Glossary](https://github.com/zgiannuzzi/oracle-db-training/blob/main/db_glossary_3.PNG)

2.
![Image of Glossary](https://github.com/zgiannuzzi/oracle-db-training/blob/main/db_glossary_3.PNG)
![Image of Glossary](https://github.com/zgiannuzzi/oracle-db-training/blob/main/db_glossary_2.PNG)

### 5.2 

#### Exercise 1/2 
1. Tried to confirm foreign, unique, and primary keys.
2. Set up CSV file

#### Exercise 3
![Image of Glossary](https://github.com/zgiannuzzi/oracle-db-training/blob/main/dd_templates.PNG)

#### Exercise 4
![Image of Glossary](https://github.com/zgiannuzzi/oracle-db-training/blob/main/db_abbreviation.PNG)

#### Exercise 5
![Image of Glossary](https://github.com/zgiannuzzi/oracle-db-training/blob/main/db_subtypes.PNG)

### 6.1/6.2 
- Reviewed features of Oracle express/Apex
- Had to create own account for the tables 
- Clicked on help Icon and reviewed sections and topics

## The following sections were completed at different times. The first 3 sections are what i attempted in my own. THe sections after used answer key for the query questions.
### 6.3 
#### EXERCISE 1
``` sql
CREATE TABLE STUDENT(
student_id NUMBER(6) NOT NULL,
first_name varchar2(100) NOT NULL,
last_name VARCHAR2(100) NOT NULL,
reg_year Date NOT NULL,
email varchar2(200) NOT NULL,
parent_id NUMBER(6) NOT NULL
);


CREATE TABLE PARENT_INFO(
parent_id NUMBER(6) NOT NULL,
first_name1 varchar2(100) NOT NULL,
last_name1 VARCHAR2(100) NOT NULL,
first_name2 varchar2(100) NOT NULL,
last_name2 VARCHAR2(100) NOT NULL
);



CREATE TABLE STUDENT_COURSE_DET(
grade NUMBER(6) NOT NULL
);

CREATE TABLE STUDENT_ATTENDANCE(
number_of_work_days NUMBER(6) NOT NULL,
number_of_days_off NUMBER(6) NOT NULL,
elligibility VARCHAR2(100)
);

CREATE TABLE ACADEMIC_SESSION(
academic_ses_id NUMBER(6) NOT NULL,
academic_name VARCHAR2(100) NOT NULL
);

CREATE TABLE COURSE(
course_id NUMBER(6) NOT NULL,
course_name VARCHAR2(100) NOT NULL
);

CREATE TABLE EXAM_RESULT(
grade NUMBER(6) NOT NUll
);

CREATE TABLE DEPARTMENT(
department_id NUMBER(6) NOT NULL,
department_name VARCHAR2(100) NOT NULL,
department_head VARCHAR(100) NOT NULL
);

CREATE TABLE EXAM(
exam_id NUMBER(6) NOT NULL,
start_date VARCHAR2(100) 
);

CREATE TABLE EXAM_TYPE(
type_id NUMBER(6) NOT NULL,
start_date VARCHAR2(100),
exam_description VARCHAR2(100)
);

CREATE TABLE FACULTY_COURSE_DETAIL(
contact_hours varchar(100) NOT NUll
);


CREATE TABLE FACULTY_LOGIN_DETAIL(
login_date_time timestamp NOT NUll
);

CREATE TABLE FACULTY(
faculty_id NUMBER(6) NOT NULL,
first_name varchar2(100) NOT NULL,
last_name VARCHAR2(100) NOT NULL,
email varchar2(100) NOT NULL,
salary number(8),
insurance varchar2(100),
hourly_rate number(6)
dept_ID number(6)
);


```
#### EXERCISE 2
``` sql
alter table STUDENT add contraint student_pk primary key (student_id);
alter table PARENT_INFO add contraint parent_pk primary key (parent_id);
alter table ACADEMIC_SESSION add contraint academic_ses_pk primary key (academic_ses_id);
alter table COURSE add contraint course_pk primary key (course_id);
alter table DEPARTMENT add contraint department_pk primary key (department_id);
alter table EXAM add contraint exam_pk primary key (exam_id);
alter table EXAM_TYPE add contraint type_pk primary key (type_id);
alter table FACULTY add contraint faculty_pk primary key (faculty_id);

```

#### EXERCISE 3
1.
``` sql
CREATE TABLE DEPT(
dept_id NUMBER(8) ,
dept_name varchar2(30) ,
loc_id NUMBER(4)
);

ALTER TABLE DEPT ADD CONSTRAINT DEPT_PK PRIMARY KEY (dept_id, dept_name);
```
2.
``` sql
CREATE TABLE SUPPLIERS(
sup_id NUMBER(15),
sup_name varchar2(30),
contact_name NUMBER(4) 
);

ALTER TABLE SUPPLIERS ADD CONSTRAINT SUP_PK PRIMARY KEY (sup_id, sup_name);

CREATE TABLE PRODUCT(
product_id NUMBER(10) ,
sup_id NUMBER(15) NOT NULL,
contact_name varchar2(30) NOT NULL
);

ALTER TABLE PRODUCT ADD CONSTRAINT PRODUCT_PK PRIMARY KEY product_id;
ALTER TABLE PRODUCT ADD CONSTRAINT PRODUCT_FK FOREIGN KEY (sup_id,sup_name) REFERENCES SUPPLIERS (sup_id,sup_name) ;

```
3.
``` sql
CREATE TABLE DEPT_SAMPLE(
dept_id NUMBER(8) ,
dept_name varchar2(30) ,
loc_id NUMBER(4)
);

ALTER TABLE DEPT_SAMPLE ADD CONSTRAINT unq_dept_det UNIQUE (dept_id, dept_name);
```
### 6.4
``` sql
INSERT INTO ACADEMIC_SESSION VALUES (100, 'SPRING SESSION');
INSERT INTO ACADEMIC_SESSION VALUES (200, 'FALL SESSION');
INSERT INTO ACADEMIC_SESSION VALUES (300, 'SUMMER SESSION');

INSERT INTO DEPARTMENT VALUES(10, 'ACCOUNTING', 'MARK SMITH');
INSERT INTO DEPARTMENT VALUES(20, 'BIOLOGY', 'DAVE GOLD');
INSERT INTO DEPARTMENT VALUES(30, 'COMPUTER SCIENCE', 'LINDA BROWN');
INSERT INTO DEPARTMENT VALUES(40, 'LITERATURE', 'ANITA TAYLOR');

INSERT INTO PARENT_INFO VALUES(600,'NEIL', 'SMITH','DORIS', 'SMITH');
INSERT INTO PARENT_INFO VALUES(610,'WILLIAM', 'BEN','NITA', 'BEN');
INSERT INTO PARENT_INFO VALUES(620,'SEAN', 'TAYLOR','RHEA', 'TAYLOR');
INSERT INTO PARENT_INFO VALUES(630,'DAVE', 'CARMEN','CATHY', 'CARMEN');
INSERT INTO PARENT_INFO VALUES(640,'JOHN', 'AUDRY','JANE', 'AUDRY');

INSERT INTO STUDENT VALUES(720, 'JACK','SMITH', TO_DATE('01-Jan-2012','DD-Mon-YYYY'),'JSMITH@SCHOOL.EDU', 600);
INSERT INTO STUDENT VALUES(730, 'NOAH', 'AUDRY', TO_DATE('01-Jan-2012','DD-Mon-YYYY'),'NAUDRY@SCHOOL.EDU', 640);
INSERT INTO STUDENT VALUES(740, 'RHONDA','TAYLOR', TO_DATE('01-Sep-2012','DD-Mon-YYYY'),'RTAYLOR@SCHOOL.EDU', 620);
INSERT INTO STUDENT VALUES(750, 'ROBERT','BEN', TO_DATE('01-Mar-2012','DD-Mon-YYYY'),'RBEN@SCHOOL.EDU', 610);
INSERT INTO STUDENT VALUES(760, 'JEANNE','BEN', TO_DATE('01-Mar-2012','DD-Mon-YYYY'),'JBEN@SCHOOL.EDU', 610);
INSERT INTO STUDENT VALUES(770, 'MILLS','CARMEN', TO_DATE('01-Apr-2013','DD-Mon-YYYY'),'MCARMEN@SCHOOL.EDU', 630);

INSERT INTO COURSE VALUES (190, 'PRINCIPLES OF ACCOUNTING', 100, 10,NULL,NULL,'BUILDING A','101','MWF 12-1');
INSERT INTO COURSE VALUES (191, 'INTRODUCTION TO BUSINESS LAW', 100, 10,NULL,NULL,'BUILDING B','201','THUR 2-4');
INSERT INTO COURSE VALUES (192, 'COST ACCOUNTING', 100, 10,NULL,NULL,'BUILDING C','301','TUES 5-7');
INSERT INTO COURSE VALUES (193, 'STRATEGIC TAX PLANNING FOR BUSINESS', 100, 10,'TAX123','PASSWORD',NULL,NULL,NULL);
INSERT INTO COURSE VALUES (194, 'GENERAL BIOLOGY', 200, 20,'BIO123','PASSWORD',NULL,NULL,NULL);
INSERT INTO COURSE VALUES (195, 'CELL BIOLOGY', 200, 20,NULL,NULL,'BUILDING D','401','MWF 9-10');

INSERT INTO FACULTY VALUES (800, 'JILL', 'MILLER','JMILL@SCHOOL.EDU',10000,'HEALTH',NULL,20);
INSERT INTO FACULTY VALUES (810, 'JAMES', 'BORG','JBORG@SCHOOL.EDU',30000,'HEALTH,DENTAL',NULL,10);
INSERT INTO FACULTY VALUES (820, 'LYNN', 'BROWN','LBROWN@SCHOOL.EDU',NULL,NULL,50,30);
INSERT INTO FACULTY VALUES (830, 'ARTHUR', 'SMITH','ASMITH@SCHOOL.EDU',NULL,NULL,40,10);
INSERT INTO FACULTY VALUES (840, 'SALLY', 'JONES','SJONES@SCHOOL.EDU',50000,'HEALTH,DENTAL,VISION',NULL,40);

INSERT INTO EXAM_TYPE VALUES('MCE','Multiple Choice Exams','CHOOSE MORE THAN ONE ANSWER');
INSERT INTO EXAM_TYPE VALUES('TF','TRUE AND FALSE Exams','CHOOSE EITHER TRUE OR FALSE');
INSERT INTO EXAM_TYPE VALUES('FIB','FILL IN THE BLANKS Exams','TYPE IN THE CORRECT ANSWER');
INSERT INTO EXAM_TYPE VALUES('ESS','ESSAY Exams','WRITE PARAGRAPHS');
INSERT INTO EXAM_TYPE VALUES('SA','SHORT ANSWER Exams','WRITE SHORT ANSWERS');

INSERT INTO EXAM VALUES(500, TO_DATE('12-Sep-2013','DD-Mon-YYYY'),'MCE',190);
INSERT INTO EXAM VALUES(510, TO_DATE('15-Sep-2013','DD-Mon-YYYY'),'SA', 191);
INSERT INTO EXAM VALUES(520, TO_DATE('18-Sep-2013','DD-Mon -YYYY'),'FIB', 192);
INSERT INTO EXAM VALUES(530, TO_DATE('21-Mar-2014','DD-Mon -YYYY'),'ESS', 193);
INSERT INTO EXAM VALUES(540, TO_DATE('02-Apr-2014','DD-Mon-YYYY'),'TF', 194);

INSERT INTO EXAM_RESULT VALUES(720,190,500,91);
INSERT INTO EXAM_RESULT VALUES(720,193,520,97);
INSERT INTO EXAM_RESULT VALUES(730,195,540,87);
INSERT INTO EXAM_RESULT VALUES(730,194,530,85);
INSERT INTO EXAM_RESULT VALUES(750,192,500,60);
INSERT INTO EXAM_RESULT VALUES(750,195,510,97);
INSERT INTO EXAM_RESULT VALUES(750,191,520,78);
INSERT INTO EXAM_RESULT VALUES(760,192,540,65);
INSERT INTO EXAM_RESULT VALUES(760,191,530,60);
INSERT INTO EXAM_RESULT VALUES(760,192,510,70);

INSERT INTO STUDENT_ATTENDANCE VALUES( 720,100, 180, 21,'Y');
INSERT INTO STUDENT_ATTENDANCE VALUES( 730,200, 180, 11,'Y');
INSERT INTO STUDENT_ATTENDANCE VALUES( 740,300, 180, 12,'Y');
INSERT INTO STUDENT_ATTENDANCE VALUES( 750,100, 180, 14,'Y');
INSERT INTO STUDENT_ATTENDANCE VALUES( 760,200, 180, 15,'Y');
INSERT INTO STUDENT_ATTENDANCE VALUES( 770,300, 180, 13,'Y');

INSERT INTO STUDENT_COURSE_DET VALUES(720,190,'A');
INSERT INTO STUDENT_COURSE_DET VALUES(720,193,'B');
INSERT INTO STUDENT_COURSE_DET VALUES(730,191,'C');
INSERT INTO STUDENT_COURSE_DET VALUES(740,195,'F');
INSERT INTO STUDENT_COURSE_DET VALUES(750,192,'A');
INSERT INTO STUDENT_COURSE_DET VALUES(760,190,'B');
INSERT INTO STUDENT_COURSE_DET VALUES(760,192,'C');
INSERT INTO STUDENT_COURSE_DET VALUES(770,192,'D');
INSERT INTO STUDENT_COURSE_DET VALUES(770,193,'F');
INSERT INTO STUDENT_COURSE_DET VALUES(770,194,'A');

INSERT INTO FACULTY_COURSE_DETAIL VALUES (800, 192,3);
INSERT INTO FACULTY_COURSE_DETAIL VALUES (800, 193,4);
INSERT INTO FACULTY_COURSE_DETAIL VALUES (800, 190,5);
INSERT INTO FACULTY_COURSE_DETAIL VALUES (800, 191,3);
INSERT INTO FACULTY_COURSE_DETAIL VALUES (810, 194,4);
INSERT INTO FACULTY_COURSE_DETAIL VALUES (810, 195,5);

INSERT INTO FACULTY_LOGIN_DETAIL VALUES(800, CURRENT_TIMESTAMP);
INSERT INTO FACULTY_LOGIN_DETAIL VALUES(810, CURRENT_TIMESTAMP);
INSERT INTO FACULTY_LOGIN_DETAIL VALUES(840, CURRENT_TIMESTAMP);
INSERT INTO FACULTY_LOGIN_DETAIL VALUES(820, CURRENT_TIMESTAMP);
INSERT INTO FACULTY_LOGIN_DETAIL VALUES(830, CURRENT_TIMESTAMP);



```
#### Exercise 2
``` sql
ALTER TABLE FACULTY_LOGIN_DETAIL ADD  DETAILS  VARCHAR2(50);
UPDATE FACULTY_LOGIN_DETAIL
SET DETAILS = 'this is a test'
Where FACULTY_LOGIN_DETAIL.ID = 810

UPDATE FACULTY_LOGIN_DETAIL
SET DETAILS = 'HELLO WORLD'
Where FACULTY_LOGIN_DETAIL.ID = 820

```
### 6.5 
1. Yes
2.
  - 3 records in the table 
  - Rollback would go back to the state where there were 4 records in the table.
## Sections 6.6 - 6.9 Used the answer key answers create the tables to ensure correctness of tables.
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
2. Display the details of the students who have scored more than 95.
``` sql
  select * From AD_EXAM_RESULTS Where EXAM_GRADE > 95
```
3. Display the details of the students who have scored between 65 and 70.
``` sql
  select * From AD_EXAM_RESULTS Where EXAM_GRADE BETWEEN 65 AND 70
```
4. Display the students who registered after 01-Jun-2012.
``` sql
  select * From AD_STUDENTS Where REG_YEAR BETWEEN '02-Jun-2012' and CURDATE 
```
5. Display the course details for departments 10 and 30.
``` sql
  select * From AD_COURSES WHERE DEPT_ID = 10 or DEPT_ID - 30
```
6. Display the details of students whose first name begins with the letter "J".
``` sql
  select HEAD From AD_DEPARTMENTS
```
7. Display the details of students who have opted for courses 190 or 193.
``` sql
  select * From AD_COURSES WHERE DEPT_ID = 10 or DEPT_ID - 30
```
8. Display the course details offered by department 30 for the Fall Session (Session ID 200)
``` sql
  select * From AD_COURSES WHERE (DEPT_ID = 30 and SESSION_ID = 200)
```
9. Display the course details of courses not being offered in the summer and fall session (Session ID 200 and 300).
``` sql
  select * From AD_COURSES WHERE (DEPT_ID = 30 and SESSION_ID = 200)
```
10. Display the course details for department 20.
``` sql
  select * From AD_COURSES WHERE DEPT_ID = 20
```

### 6.8

1. Display all fields for each of the records in ascending order for the following tables:
  - AD_STUDENTS ordered by REG_YEAR
    ``` sql
      select * From AD_STUDENTS ORDER BY REG_YEAR
    ```
  - AD_EXAM_RESULTS ordered by STUDENT_ID and COURSE_ID
    ``` sql
      select * From AD_EXAM_RESULTS ORDER BY (STUDENT_ID, COURSE_ID)
    ```
  - AD_STUDENT_ATTENDANCE ordered by STUDENT_ID
    ``` sql
      select * From AD_STUDENT_ATTENDANCE ORDER BY STUDENT_ID 
    ```
  - AD_DEPARTMENTS ordered by the department ID
    ``` sql
      select * From AD_DEPARTMENTS ORDER BY DEPT_ID
    ```
2. Display the percentage of days students have taken days off and sort the records based on the percentage calculated.
   ``` sql
      select * From AD_DEPARTMENTS ORDER BY DEPT_ID
    ```
3. Display the top 5 students based on exam grade results.
   ``` sql
      select * From AD_EXAM_RESULTS ORDER BY EXAM_RESULTS DESC MAX REC 5
    ```
4. Display the parent details ordered by the parent ID.
    ``` sql
      select * From AD_PARENT_INFORMATION ORDER BY PARENT_ID
    ```
### 6.9

1. Display the different courses offered by the departments in the school.
    ``` sql
      select NAME From AD_COURSES JOIN AD_DEPARTMENTS ON (AD_COURSES.DEPT_ID = AD_DEPARTMENTS.ID)
    ```
2. Display the courses offered in the Fall session.
    ``` sql
     select NAME
      From AD_COURSES JOIN AD_ACADEMIC_SESSIONS
      ON (AD_COURSES.SESSION_ID = AD_ACADEMIC_SESSIONS.ID)
      WHERE AD_ACADEMIC_SESSIONS.ID = 200
    ```
3. Display the course details, the department that offers the courses and students who have enrolled for those courses.
    ``` sql
      select * From AD_PARENT_INFORMATION ORDER BY PARENT_ID
    ```
4. Display the course details, the department that offers the courses and students who have enrolled for those courses for
department 20.
    ``` sql
      select * From AD_PARENT_INFORMATION ORDER BY PARENT_ID
    ```
5. Write a query to display the details of the exam grades obtained by students who have opted for the course with COURSE_ID in
the range of 190 to 192.
    ``` sql
      select *
       From AD_EXAM_RESULTS JOIN AD_STUDENTS
       ON (AD_EXAM_RESULTS.STUDENT_ID = AD_STUDENTS.ID)
       WHERE AD_EXAM_RESULTS.COURSE_ID BETWEEN 190 and 192
    ```
6. Retrieve the rows from the AD_EXAM_RESULTS table even if there are no matching records in the AD_COURSES table
    ``` sql
       select *
       From AD_EXAM_RESULTS FUll OUTER JOIN AD_COURSES
       ON (AD_EXAM_RESULTS.COURSE_ID = AD_COURSES.ID)
    ```

