# SQL DISTINCT 

By: Keisla Medina, Anthony Pellegrino, and George Toutoungi

## Description

Put our skills to the test and utilized SQL and minimal python to work together to create a datawarehouse to answer a multitude of
questions that administrators, deans, and teachers will find useful.

* Fairfield University course registration data
* Analyzed the source data
  * Academic Calendar
  * Catalogs
  * Terms : Each term folder consisted of mulptiple data source. A courses.csv, course_meetings.csv, course_offerings.csv, etc. 
* Created an ERD 
* Created a database that consisted off all our tables in our ERD and then input data into them
* Tested our database for integrity
* Utilized our database to create a datawarehouse that would be able to quickly answer an admins. questions through simple queries

## Getting Started

1. Analyzed the data
   * Primarily focused on three documents to grasp a general understanding of the data:
      * CourseCatalog files
      * Course Meetings
      * Course Offerings
      * Courses
2. Created an ERD 
   * ERD demonstrates how we normalized the data
   * [Database Design](Database_ERD.pdf)

## Creating the Database
1. Using the template from the ERD, we created a new database called: *CourseData.db*
2. Created 6 unique tables
    * Courses
    * Course Offerings
    * Course Meetings
    * Programs
    * Instructors
    * Locations
3. Embedded python to connect our source data to our new *Course Data Database*
4. Uploaded data from the temporary tables we created into our *Course Data Database tables* using select queries
5. [Database Tables](Create_Tables.ipynb)


## Testing Database Integrity
1. Created various queries to test the integrity of our database to ensure that the tables were functional and that there were no referential integrity errors
2. Examples of some of the questions our queries answered:
    * How many seats remain in each of Professor Bloch's classes for the Spring 2018 semester?
    * How does enroll capacity compare to actual enrollment for a class in the Fall 2018 semester?
    * Which classrooms are the most utilized in the Dolan School?
    * How many classes has each professor taught?
    * How many courses are in each program?
3. [Course Data Tests](CourseDataTests.ipynb)

## Creating Datawarehouse
1. Decided what are some questions that might be most useful to teachers, deans, Office of the Provost, etc. 
2. Created a new ERD that displays a fact table with multiple dimensions
3. Tables
    * Fact Table
    * Instructors Table
    * Programs Table
    * Time Slices Table
    * Calendar Dates Table
    * Locations Table
4. After creating these various tables, we constructed SELECT queries to input data from our database into the datawarehouse 
5. [Data Warehouse](CourseDataWarehouse.ipynb)

## Testing Datawarehouse Integrity
1. Just as we did with the database, we constructed multiple queries to verify the accuracy and functionality of our datawarehouse
2. Examples of some of the questions the queries answered:
    * How many courses are offered in 2018? (Join Course_Facts on Calendar_Dates and select CatalogID, Term, and Year and we count Catalog_ID with Term)
    * How many courses are offered in Bannow (Joing Course_Facts on Locations and select CatalogID and Room_ID where Room_ID Like '%BNW%'
    * How many courses has an instructor taught? (Join Course_Facts on InstructorID and select CatalogID, Term, and InstructorName and count Catalog_ID)
    * How many courses are in each program? (Joing Course_Facts on Programs and select ProgramName and Count (CatalogID)
    * On Thursdays how many classes are offered at lunchtime? (Join Course_Facts on Time_Slices select Day and Start Time and count (Catalog_ID) and use where (Day = R and Start = 12:30)
3. [Datawarehouse Integrity Tests](DataWarehouse_Test.ipynb)

## Results
1. To see the datawarehouse in use, we constructed sample questions that would be useful to adminstrators and individuals who will be utilizing the datawarehouse
2. Questions that individuals may ask in regards to the datawarehouse:
   * Do we need to increase the number of Intro to Accounting Courses offered due to the increase in student enrollment?
    * Should we offer more classes on Monday's during a particular time code?
    * How are rooms utilized in the Dolan School of Business?
    * Which departments are in need of more professors to help advise students?
    * What are the least popular classes? Should we consider removing them from the catalog? 
3. [Demo Questions](Demo_Questions.ipynb)

## Thank you! Any Questions?
