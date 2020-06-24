Objectives
	• Understand database  terminology
	• Build an SQL database
	• Insert some common data into the database
	• List various database tools in commo use
	• Compare and explain the different database structure 
	• Explain a simple relational database structure 
	
	
	We must be able to structure tables to contain the right type of information, so that we can query it.
	
	Database sections attributes used in tables to label different data. Database allows us to group data into relevant information. 
	
	
	Terminology 
	Structure set of data held in computer 
	SQL is management system data 
	Column correspond to attributes of object
	Row - one set of attributes
	Entity 
	
	Primary key should always be constant 
	The_books: reference number, author, published date and 
	
	Table_bank_account 
	Primary key:  customer number is the unique reference number 
	Foreign key: establish relationship between primary key to use existing information, rather than repeating information to reduce duplicate values. Relationship is used to quickly retrieve data
	First_name, last_name, money, money in total accounts, banking history
	
	Junction table is required to connected two values for many to many. Hence a table is one to many. 
	
	Type of database 
	Flat-file database 
	• Stores everything in one table. Good for small numbers of records related toa  single topic
	
	Relational database 
	• Gives you the ability to separate the masses of data into numerous tables
	• They are linked to each other through the use of keys
	
	Big data
	• MongoDB, Vertica etc.
	• Used for Data Analytics and Business Intelligence 
	• Digital Age and Internet of Things 
Relationships 

One-to-one relationship: occurs when there is a unique identifier to another unique identifier
One-to-many relationships: one customer can have numerous purchases, hence numerous purchase Ids  
Many-to-many relationships: Student can be assigned to a course and courses to multiple students 

1st Normal Form
A database is in First Normal form when the following conditions are satified: 
	• Make everything atomic, data must be presented as small as it can be 
	• There should be no repeating groups
For example, a table that records data on a book and its author(s) with the following columns: Book ID, Author 1, 
Author 2, Author 3 is not in 1NF because authors are repeating the same attribute 

2nd Normal Form
A Database is in Second Normal Form when the following conditions are satisfied:
	• It is in 1NF
	• All non-key attributes are fully functional dependent on the primary key 


3rd normal form
A database is in 3rd Normal Form when the following conditions are satisfied:
	• It is in 2NF
	• There is no transitive functional dependency 
i.e occurs when non-key column is functionally dependent on another non-key column, which is functionally dependent on the primary key