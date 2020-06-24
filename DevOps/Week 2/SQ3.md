#   DDL (30% of exam)

Wednesday 24th June 2020

Standup
SQL fundamentals of DML, DDL. 60% practical. I learn through practice to go over and over.
Blocker was me, I fell behind at the end on the last parts of code.
Drop cascade
Go through last parts
Mock Test Friday: Daily Standup 

#   DDL Focus
#   saved code

USE Northwind
DROP DATABASE Marcus_Tse_db;
CREATE DATABASE Marcus_Tse_db;
USE Marcus_Tse_db;

-- Create Statements
DROP TABLE film_table;
/* CREATING A DATABASE*/
--Identity(1,1)--->1, 1+1=2,3,4

CREATE TABLE film_table
(
    film_name VARCHAR(11),
    film_type VARCHAR(10),
    Date_of_release DATE,
    Director VARCHAR(20),
    Writer VARCHAR(10),
    STAR INT,
    Film_language CHAR(10),
    Official_Website VARCHAR(20),
    Plot_Summary VARCHAR(2000),
)
;

--film_id INT IDENTITY(1,1) PRIMARY KEY,
ALTER TABLE film_table
ADD film_id INT IDENTITY(1,5) PRIMARY KEY;


INSERT INTO film_table
    (film_name, film_type, Date_of_release, Director, Writer, STAR, Film_language, Official_Website, Plot_Summary)
VALUES
    ('Inception', 'Sci-fi', '2017-11-05', 'Christopher Nolan', 'Marcus Tse', 5, 'English', 'IMDB', 'Good film')
;

INSERT INTO film_table
    (film_name, film_type)
VALUES
    ('Star Wars', 'Sci-fi'),
    ('Star Trek', 'Sci-fi');

/*
CREATE TABLE film_table(
    film_id INT IDENTITY(1,1) PRIMARY KEY,
    film_name VARCHAR(50) NOT NULL,
    film_type VARCHAR(50)
)
*/

DROP TABLE director
CREATE TABLE director
(
    director_id INT IDENTITY(1,1),
    director_name VARCHAR(50),
    city VARCHAR(20) DEFAULT 'LONDON',
    film_id INT,
    PRIMARY KEY(director_id),
    FOREIGN KEY(film_id) REFERENCES film_table(film_id)
)


INSERT INTO director
    (director_name, film_id)
VALUES
    ('Steve', 1),
    ('Tom', 6)

INSERT INTO director
    (director_name, film_id)
VALUES
    ('Bob', 11)

SELECT * FROM director;
SELECT * FROM film_table;


UPDATE director SET director_name='Jamie' WHERE film_id=1
*/
--foreign key is a primary key as a reference
/*old code
ALTER TABLE director
ALTER film_id INT 
FOREIGN KEY 
REFERENCES film_table (film_id) ON DELETE CASCADE;
*/

-- constraint key = foreign

ALTER TABLE director
DROP CONSTRAINT film_id

-- One to many relationship one film_id and many film_id in director
ALTER TABLE director
ADD CONSTRAINT foreign_key_onFilmId FOREIGN KEY (film_id) 
REFERENCES film_table (film_id) ON DELETE CASCADE;

--Drop cascade
DELETE FROM film_table WHERE film_id=6;


#   Wednesday 24th June 2020 
#   Azure Studio exercises:
/* WHERE clause-filter the data */
SELECT * FROM Customers WHERE City = 'Paris'


1.  SELECT COUNT(*) AS "Number of Employees in London" FROM Employees
WHERE City='London'
SELECT * FROM Employees WHERE City = 'London';

2.  SELECT COUNT(*) AS "Number of Employees with Title Doctor" FROM Employees
SELECT * FROM Employees WHERE TitleOfCourtesy = 'Dr.';

3.  SELECT COUNT(*) AS "Number of products that are discontinued" FROM Products
WHERE Discontinued = 1
SELECT * FROM Products WHERE Discontinued = 1;

--Exercise Two
--Apostrophe --> ''
-- SELECT * FROM Products WHERE ProductName Like '%''%'

SELECT c.companyName, c.City, c.Country, c.Region
FROM Customers c 
WHERE c.Region='BC'


/*TOP*/
SELECT COUNT(*) FROM Customers
SELECT TOP 10 c.companyName, c.city 
FROM Customers c
WHERE c.Country = 'France';

/*AND/OR*/
--AND -all the criteria need to be fulfilled
-- OR either of the criteria 

SELECT  p.ProductName, p.UnitPrice
FROM Products P 
WHERE p.CategoryID=1 AND p.Discontinued = 0;

/*
<> or != Not equal to
*/

SELECT p.ProductName, p.UnitPrice 
FROM Products P
WHERE UnitsInStock > 0 AND UnitPrice >= 30

--DISTINCT

/*DISTINCT - used to find unique characters*/

SELECT DISTINCT c.Country
FROM Customers c

SELECT DISTINCT c.Country FROM Customers WHER

/*
Wildcards

Wildcards can be used as a substitute for any other characters ina string when using the LIKE operator 
*/

SELECT DISTINCT c.Country 
FROM Customers c WHERE Country LIKE 'U%'
/* Countries ending with letter 'A'*/
SELECT DISTINCT c.Country 
FROM Customers c WHERE Country LIKE '%A'

/* Countries starting with U,ending with letter 'A'*/
SELECT DISTINCT c.Country 
FROM Customers c WHERE Country LIKE 'U%A'

/* Countries either starting with U or A*/
SELECT DISTINCT c.Country
FROM Customers c WHERE COUNTRY LIKE '[UAM]%'

/* Countries not starting with U or A or M*/
SELECT DISTINCT c.Country
FROM Customers c WHERE COUNTRY != '[UAM]%'
ORDER BY c.Country

/* Countries whose 3rd letter is A*/
SELECT DISTINCT c.Country
FROM Customers c WHERE COUNTRY LIKE '__A%'
ORDER BY c.Country


SELECT DISTINCT ProductName
FROM Products P WHERE ProductName Like 'CH%'

/* SELECT * in the customer region where the first character can be anything, but the second charatcer is A with a total length of 2*/
/* _A%- region consisting of only 2 characters and the end characters is A where the first character can be anything */

SELECT * FROM Customers WHERE Region Like '_A'


/* IN Operator-supports equation to multiple values */
SELECT  p.ProductName, p.UnitPrice
FROM Products P 
WHERE p.CategoryID=1 AND p.Discontinued = 0;

SELECT * FROM Customers WHERE Region In ('WA','SP')

SELECT * FROM Customers WHERE Region = 'WA' OR Region = 'SP'
SELECT * FROM Customers WHERE (Region = 'WA' OR Region = 'SP') 
AND Country ='Brazil';

SELECT * FROM Customers WHERE Region IN('WA','SP')
AND Country IN ('Brazil','USA');

/* Next exerise 
BETWEEN-includes values between and as well as the boundary values*/
SELECT * FROM EmployeeTerritories
WHERE TerritoryID BETWEEN 06800 AND 09999;

SELECT * FROM EmployeeTerritories
WHERE TerritoryID BETWEEN IN (06800,09999);

1. 
SELECT * FROM Products WHERE UnitPrice < 5.00;

SELECT p.ProductName, p.ProductID FROM Products p
WHERE UnitPrice < 5.00;


2.
SELECT * FROM Categories 

SELECT * 
FROM Categories AS "c"
WHERE c.CategoryName LIKE '[BS]%'

SELECT c.CategoryName, c.DESCRIPTION
FROM Categories c
WHERE c.CategoryName LIKE 'B%' OR c.CategoryName LIKE 'S%'

/* how many orders are there for employeeids 5 nad 7)*/
3. 
SELECT * FROM Orders 
WHERE EmployeeID IN ('5','7');

SELECT COUNT(*) AS "Number of Employee orders with EmployeeIDS 5 and 7" FROM Orders
WHERE EmployeeID IN (5,7);

SP_HELP Employees

SELECT COUNT(*) AS "Count of orders placed by Employees"
FROM Orders o 
Where o.EmployeeID IN (5,7)
GROUP by O.EmployeeID

/* Concatenation */
--Example
SELECT * FROM [Customers];

SELECT c.companyName AS 'Company Name',
c.City + ', ' + c.Country AS 'City'
FROM Customers c;

--Astha way
SELECT c.CompanyName AS "Company Name",
CONCAT(c.City,',',c.Country) AS "City"
FROM Customers c;

SELECT LastName FROM Employees;

SELECT e.FirstName, e.LastName, 
CONCAT(e.Firstname,' ', e.LastName) AS "Employee Name"
FROM Employees e;

/* NULL Value
IS NULL AND IT NOT NULL
 */
SELECT CompanyName AS 'Company Name', City + ', ' + Country AS 'City'
FROM Customers
WHERE REGION IS NULL

SELECT * FROM Customers;

SELECT  c.Country, c.Region
FROM Customers c
WHERE REGION IS NOT NULL;

SELECT TOP 6 C.Country, c.Region 
FROM Customers c
WHERE REGION IS != NULL;

-- MODULUS
SELECT * FROM [Order Details]
SELECT UnitPrice, Quantity, Discount, 
(UnitPrice * Quantity * (1 - discount)) AS "Gross Total"
From [Order Details];

--Apples -> price -> 2pounds, quantity =10, discount - 25% 
-- Gross Total(The cost of the apple excluding discount)
-- Net Total (The amount i pay the shopkeeper at the end)

--Gross = 2*10 =20
--Net = 20*0.75 = 15

SELECT * FROM [Order Details]

SELECT od.UnitPrice, od.Quantity, od.Discount, 
(OD.UnitPrice * od.Quantity) AS "Net total",
ROUND(od.UnitPrice * od.Quantity * (1 - od.Discount),2) AS "Gross Total"
From [Order Details] od
ORDER BY "Gross Total" DESC
--ORDER

ORDER BY "Gross Total" DESC

--ORER BY
SELECT TOP 2 od.OrderID, od.UnitPrice, od.Quantity, od.Discount, 
(OD.UnitPrice * od.Quantity) AS "Net total",
ROUND(od.UnitPrice * od.Quantity * (1 - od.Discount),2) AS "Gross Total"
From [Order Details] od
ORDER BY "Net total" DESC

SELECT PostalCode "Post Code",
Left(c.PostalCode, CHARINDEX(' ', c.PostalCode)-1) AS "Post Code Region",
CHARINDEX(' ',c.PostalCode) AS "Space Found", c.Country
From Customers c
WHERE Country = 'UK';

/* USE CHARINDEX to list only product names that contain a single 
note: colummn alias cannot be used in WHERE 
for single quote use two single quotes to escape it
*/
SELECT * FROM Products;

SELECT p.ProductName "Product Name", 
CHARINDEX('''', P.ProductName) AS "Index a Quote"
FROM Products p
WHERE CHARINDEX('''', p.ProductName) > 0 

SELECT p.ProductName 
FROM Products p 
WHERE  p.productName LIKE '%''%';
