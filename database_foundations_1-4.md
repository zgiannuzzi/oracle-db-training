# Database Foundations Sections 1-4

## Exercise 1-2: Identify Database Design Considerations for Given Case Scenarios

Tasks
1. ABC School District would like to create a student on-line information and registration system to capture student-related
information. The system needs to be designed as an on-line process to allow all new students to register on-line. It should also
allow existing students to update and review all information. Create a list of important data that would need to be captured and
stored in the student registration database.
   - Student-ID
   - First_Name
   - Last_Name
   - Address
   - Phone_number
   - Parent Name
   - Grade
   - Age


2. XYZ community would like to create a library management system. The objective is for the database to handle all transactions for
the library. The database needs to store all the data that is relevant to managing the books, managing customers, and the day-today activities of the library. Create a list of important data that would need to be captured and stored in the library management
database.
   - Managing Books
     - Book ID
     - Title
     - Genre
     - Author
     - Section ID
   - Managing Customers
     - First name
     - Last Name
     - Library ID
     - Address
     - Phone number
     - Email
   - Day to day
     - Book ID
     - Availabilty
     - Section ID
     - Section
     - Book type
## Exercise 1-3 Identify the Database Models

Task dentify the type of database model that has been represented in the given model snapshots:

1. Hierarchical model
2. Network model 
3. Object Oreinted model
4. Relational model
5. Flat File model

## Exercise 1-4 Buisness Requirements 

Tasks

1. LibBook is a successful digital library that rents CDs and provides access to Internet for browsing their repository of articles and
magazines. With the growing business, LibBook needs to enhance their information system to support proposed changes to the
business. LibBook attracts new members easily and the number of members is growing rapidly. The membership base is not
stable, however, which is a cause for concern. The main idea is to introduce the concept of membership at LibBook. Members will
pay a membership fee and initially, there will be three types of membership (corporate, student, individual) although more may be
introduced later. Student membership is free. Corporate and Faculty memberships incur a fee but entitle the member to privileges.
The type of membership can be changed only if sufficient justification is provided.

Buisness rules:
- 3 different Memberships(corporate, student, indivdual) with ability to expand 
- Student Member ship is free
- Members need to pay a fee for Benifits

Constraints:
- Only one account
- need justification to change membership


2. Star Care hospital is a multi-specialty hospital that caters to needs of different patients. Every doctor registered with this hospital is
assigned a unique ID that starts with the letter "DC". The hospital ensures that the doctors associated with them have a minimum
of seven years of working experience. Every patient is required to register with the hospital on their first visit. When a patient
arrives, a unique patient number starting with the letters "PT" is assigned to him/her.

Buisness rules: 
- 2 uniique identifiers (doctors, patients)
- Doctors start with "DC"
- patients start with "PT"

Constraints:
- Doctors need minimu 7 years of experience
- Patients are required to register on First Visit

## Exercise 2.1 Analyze the features of a Relational Database
Tasks
1. Identify the possible tables and associated fields from the given scenario:
Book.com is an online virtual store on the Internet where customers can browse the catalog and select products of interest.
 - Every book has a title, ISBN, year and price. The store also keeps the author and publisher for any book.
     - Book table
        - Title
        - ISBN
        - Year
        - Price
        - Author
        - Publisher
 - For authors, the database keeps the name, address and the URL of their homepage.
     - Author table
        - First_name
        - Last_name
        - Address
        - URL
 - For publishers, the database keeps the name, address, phone number and the URL of their website.
     - Publisher Table
        - First_name
        - Last_name
        - Address
        - Phone_number
        - Website   
 - The store has several warehouses, each of which has a code, address and phone number.
     - Warehouse Table
        - Warehouse_CD
        - Address
        - Phone number
        - Book_ID
        - Books_Stocked
 - The warehouse stocks several books. A book may be stocked at multiple warehouses.
 - The database records the number of copies of a book stocked at various warehouses.
 - The bookstore keeps the name, address, email-id, and phone number of its customers.
     - Customer table
        - First_name
        - Last_name
        - Address
        - Email-ID
        - Phone number 
 - A customer owns several shopping carts. A shopping cart is identified by a Shopping_Cart_ID and contains several books.
     - Shopping_Cart table
        - SHopping_cart_ID
        - Book_ID
        - Price
        - Copies of book
        - Billing_address
        - SHipping_address
        - shipping_cd
        - payment_Info
 - Some shopping carts may contain more than one copy of same book. The database records the number of copies of each
book in any shopping cart.
 - At that time, more information will be needed to complete the transaction. Usually, the customer will be asked to fill or select a
billing address, a shipping address, a shipping option, and payment information such as credit card number. An email
notification is sent to the customer as soon as the order is placed.





2. ABC Ltd plans to computerize its sales ordering and stock control system. A feasibility study has strongly suggested that a
relational database system be installed. The details of ABC's sales and stock control are as follows:
 - Customers send in orders for goods. Each order may contain requests for variable quantities of one or more products from
ABC's range. ABC keeps a stock file showing for each product the product details and the preferred supplier, the quantity in
stock, the reorder level and other details.
    - Customer table
       - Name
       - Product_ID
       - Order_ID
       - Number_of_Products
 - ABC delivers those products that it has in stock in response to the customer order and an invoice is produced for the
dispatched items. Any items that were not in stock are placed on a back order list and these items are usually re-ordered from
the preferred supplier. Occasionally items are ordered from alternative sources.
 - In response to the invoices that are sent out to ABC's customers, the customers send in payments. Sometimes a payment will
be for one invoice, sometimes for part of an invoice and sometimes for several invoices and part-invoices.

## Exercise 2.2 Conceptual and Physical Models

Tasks
1. Provide five reasons for creating a conceptual data model.
   - Address needs of Buisness
   - Identify important entitys
   - Iditifies relationship between entitys
   - Captures Functional needs of Business
   - Captures Informational needs of Business 
2. List two examples of conceptual models and physical models.
   - Conceptual Model
     - With a library data base. Identify needs and functionality for it
   - Physical models
     - Takes conceptual library Model and converts them into tables and columns.

## Exercise 2.3 Identify and draw entities as a beginning of an ERD

For your convenience, here is a summary of how the Academic Database (School Management System) works:
1. A School/University has many Departments which offer courses to students in a given academic session.
2. Each of these courses is taught by a faculty.
3. Students enroll for different courses in an academic session.
4. Besides the registration details, the parent information of the student also needs to be maintained by the University/School.
5. The Department maintains the student’s attendance details which would decide the eligibility of the student to take up the
exams for that academic session.
6. For each academic session, exams are conducted and the results are shared with the student within a stipulated period of
time.
7. The Department also maintains a log of the Faculty login and logout time for their reporting needs.
Tasks


With the information provided above, identify and create the entities for the School Management System
   - Course
   - department
   - student
   - faculty
   - Academic Session
   - Parent Information
   - Exam

Add the appropriate attributes as well as the optionality (*, °) to all the entities of the Academic Database.
 - Course
   - Course_name*
   - Course_ID*
   - Course_number*
   - Faculty_Name(Optional)
 - Department
   - Department_Name
   - Department_ID

## Exercise 2.4 Identify the Unique Identifier and corresponding Primary keys

Tasks
1. How do you find a particular song in the whole collection? What would be a unique identifier for SONG?
   - SONG_ID
3. Think about all the students in the classroom. Each student is described by several traits or attributes. Which attribute or attributes
allow you to pick a single student from the rest of the class?
   - SEX
   - Wearing Glasses
   - Color of Hair
 
 
For each entity, select the attribute that could be the unique identifier of each entity.

1. Entity: STUDENT
Attributes: student ID, first name, last name, address
 - student ID
3. Entity: MOVIE
Attributes: title, date released, producer, director
 - Title
4. Entity: LOCKER
Attributes: size, location, number
 - number


Exercise 2: Identify the Unique Identifiers and add to the ERD
Overview
In this practice, you will identify unique identifiers and add to an ERD.
Tasks
1. Use the Academic Database ERD from the previous exercises to identify the following:
a. Unique Identifiers
b. Candidate Unique Identifiers



 



 
























