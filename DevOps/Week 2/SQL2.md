#   Structure Query Language 
#   Data Manipulation Language
#   Data Definition Language 
#   Data Control Language
#   Transaction Control Language  

DML
	• SELECT
	• INSERT
	• UPDATE
	• DELETE

DDL
	• CREATE 
	• ALTER
	• DROP 
	• TRUNCATE

DCL
	• GRANT
	• REVOKE

TCL
	• COMMIT 
	• ROLLBACK


Creating Database in Azure Studio

DROP Marcus_Tse_db;
CREATE DATABASE Marcus_Tse_db;

CREATE TABLE my_films
(
file_name VARCHAR (10),
film_type VARCHAR (6)
)
;

SELECT * FROM my_favourite_films; 

Data Types
	• VARCHAR - adaptable to different lengths of characters. Records Max size
	• CHAR - data must be at a fixed length. Fixed amount of space used
	• INT - Holds a whole number/integer value (see also bigint, smallint and tinyint) positive or negative
	• DATA/Time/DateTime - Store Date, Time or both date and time 

Data Types 2
	• Decimal or Numeric - Fixed Precision and scale (digits to right of decimal point) numbers
	• Binary - Use to store binary data such as an image or file
	• Float - scientific use (very large)
	• Bit - Equivalent to binary (0, 1 or NULL)


CHAR is 50% faster than VARCHAR
VARCHAR is memory efficient 
Majority of cases, use VARCHAR when using first_name, last_name 

Exercise 
-   Post Code, 6-8 characters, example: WV1 8JD, use VARCHAR(10)
-   Phone Number, 11 digits, no punctuation, example 07971781325, use CHAR(11)
-   Birth Date, dd/mm/yyyy, example 31/01/1980, use DATE
-   Weight in kg, a number with decimal place, 63.5029, DECIMAL(6,4)
-   Comments, Large block of text, more than 255 characters- because of variable length VARCHAR(1000) OR VARCHAR(2000), 
can also use VARCHAR(MAX)

SQL Code:

/*
USE Northwind
DROP DATABASE Marcus_Tse_db;
CREATE DATABASE Marcus_Tse_db;
USE Marcus_Tse_db;
*/

-- Create Statements
DROP TABLE film_table;
/* CREATING A DATABASE*/
CREATE TABLE film_table
(
    file_name VARCHAR(10),
    film_type VARCHAR(10),
    Date_of_release DATE,
    Director VARCHAR(20),
    Writer VARCHAR(10),
    STAR INT,
    Film_language CHAR(10),
    Official_Website VARCHAR(20),
    Plot_Summary VARCHAR(2000)
)
;

ALTER TABLE film_table
ADD release_date DATETIME;

ALTER TABLE film_table
ALTER COLUMN film_type VARCHAR(10) NOT NULL,
ALTER COLUMN film_name VARCHAR(10),;


INSERT INTO film_table
    (file_name, film_type, Date_of_release, Director, Writer, STAR,  Film_language, Official_Website, Plot_Summary)
VALUES
    ('ICP', 'Inception', '2017-11-05', 'Christopher Nolan', 'Marcus Tse', 5, 'English', 'IMDB', 'Good film')
;


--DROP TABLE my_films
SELECT * FROM film_table;
EXEC SP_HELP film_table;
