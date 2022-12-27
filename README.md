# BootcampSQL
Courseworks
/*Core Learning 1 Tasks */
/*Creating a table using SQL and adding records
Create a table which must have a primary key and the correct datatypes.

Include a minimum of 5 fields.
View and show table structures.
Enter 10 records into your table and view them. 
Update a record.
Delete a record.*/
***************************************************************************
CREATE TABLE EMPLOYEE(
  ID INT(10),
  Name varchar(25),
  Surname varchar(25),
  Joining_Date INT(10),
  Location varchar(25),
  Primary Key (ID)
);

/* Insert data into the Employee Table*/

INSERT INTO Employee (ID, Name, Surname, Joining_date, Location)
VALUES
  (1, 'Jack', 'Sparrow', 2020, 'Bristol'),
  (2, 'Dark','Vader',2019,'Liverpool'),
  (3, 'Hannibal', 'Lecter', 2021, 'York'),
  (4, 'Vito', 'Corleone' ,2016 , 'Oxford'),
  (5, 'Iron', 'Man', 2018, 'Bath'),
  (6, 'Baby' ,'Groot' ,2017, 'Exeter'),
  (7, 'Han', 'Solo',2011, 'Derby'),
  (8, 'James', 'Bond', 2017, 'Leeds'),
  (9, 'Elle', 'Woods', 2019, 'Belfast'),
  (10, 'Tomb', 'Raider', 2020, 'Coventry');
  
/*Table 2 WAGES where ID is going to be FK*/

CREATE TABLE Wages(
ID int (10),
Hourly_Rate int(10),
Call_out varchar(25));

/*Insert data into WAGES table*/

INSERT INTO WAGES (ID, Hourly_Rate, Call_out)
values
(1, 200, 'YES'),
(2, 200, 'NO'),
(3, 250, 'YES'),
(4, 250, 'NO'),
(5, 100, 'YES'),
(6, 150, 'NO'),
(7, 200, 'NO'),
(8, 300, 'NO'),
(9, 250,'YES'),
(10,200,'NO');

/*View and Show Table Structures */

Select *
From Employee;
/* OR */
Select *
From Wages ;


/* DATA MODIFICATION UPDATE RECORDS */

Update Wages
SET Hourly_Rate = 205
Where ID = 2;


/* DELETE RECORDS*/

Delete FROM Wages
Where ID =2;


COURSEWORKS 2 /*Core Learning 2 -Data fetching using comparison operators
database link:   https://replit.com/@benkarounjessic/SQL-Uni-database#main.sql

/*CORE LEARNING 2 DATA FETCHING ANSWERS*/

/*1.Selecting all info on the students NOT ATTENTING the COURSE 1*/


Select *
From student
Where CourseID between 2 and 12;

/* 2. Obtain the first name,surname and DOB for the student with the email adress vol.bolger@example.com */



Select Forenames, Surname, DateOfBirth 
From Student
Where EmailAddress  = 'val.bolger@example.com'
;

/* 3.Obtain a list of modules which has the subject Economics */

Select *
from Module
Where Subject = 'Economics';

/*4.Obtain a list of courses 'applied for' and 'their application dates' which are scheduled BEFORE the '21 September 2020'.

Select CourseAppliedFor,Forenames,DateOfApplication
from Application
Where DateofApplication <= '2020-09-21';

/*COURSEWORK 3 Data fetching and calculations USING THE SAME EXAMPLE DATABASE LINK*/

/* 1. COUNT how many students are enrolled overall */
/* If we count applicationID it will give us how many students areenrolled */

/*Count Function*/
Select Count (applicationID)
From Application;
/* Answer is 185 */

/*2.Calculate the sum of full time fees for every full time course */

/* Sum function*/
Select Sum(FullTimeFee)
From Fees;
/*Answer is 101000*/

/* 3.Identify the cost of the least and most expensive courses */

/* Minumum Full Time Course Fee */
Select Min(FullTimeFee)
From Fees;

/*Answer is 4000 */

/* Minumum Part Time Course Fee */
Select Min(PartTimeFee)
From Fees;

/*2800*/

/* Max Full time fee */

Select Max(FullTimeFee)
From Fees;

/* Max Part time fee */
Select Max(PartTimeFee)
From Fees;

/*Answer is 8400 */

/* 4. Calculate the AVG cost of all PART TIME COURSES*/

Select AVG(PartTimeFee)
From Fees;

/*Answer is 5950 */

/*5.Calculate the fee of the each full time course after applying(subtracting)the scholarship discount */


Select FeeID, FullTimeFee, ScholarshipDiscount, (FullTimeFee - ScholarshipDiscount)
From Fees;


COURSEWORK 4 (OPTIONAL)
/*1.Write a select statement to obtain all of the student information for successful applications made for Course 11 which do not relate to current students*/

Select applicationID,CourseAppliedFor, accepted, studentID 
From Application
Where CourseAppliedFor = 11 and accepted = 1 and StudentID = 0;


/*Answer is 4 Students with following application IDs;122,132,141,163*/

/*2.Modify the select statement from the previous example into an insert statement and insert the data into the student table*/


Insert into Student
	(CourseID, Forenames,Surname,EmailAddress)
    Values
    (11, 'Josh', 'Keene','josh.keene@example.com'),
    (11, 'Patrick','Hoyer', 'patrick.hoyer@example.com'),
    (11,'Crystal', 'Harris', 'crystal.harris@example.com'),
    (11,'Steph','Davidson', 'steph.davidson@example.com')
   ;
   
   
/* 3.Write a select statement to obtain all the information for the unsuccessful applications made for Course 11*/



DELETE FROM Application
Where  CourseAppliedFor = 11 and accepted = 0;
