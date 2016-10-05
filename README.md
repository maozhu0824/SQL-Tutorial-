# SQL-Tutorial-
w3schools.com

# SQL SELECT Statement, the SELECT statement is used to select data from a database.
SELECT column_name,column_name
FROM table_name;

SELECT * FROM table_name;

SELECT CustomerName,City FROM Customers; 

SELECT * FROM Customers; 

# SQL SELECT DISTINCT Statement:The DISTINCT keyword can be used to return only distinct (different) values.
SELECT DISTINCT column_name,column_name
FROM table_name;

SELECT DISTINCT City FROM Customers; 


# SQL WHERE Clause
SELECT column_name,column_name
FROM table_name
WHERE column_name operator value;

SELECT * FROM Customers
WHERE Country='Mexico';

SELECT * FROM Customers
WHERE CustomerID=1;

# SQL AND & OR Operators
SELECT * FROM Customers
WHERE Country='Germany'
AND City='Berlin'; 

SELECT * FROM Customers
WHERE City='Berlin'
OR City='München'; 

SELECT * FROM Customers
WHERE Country='Germany'
AND (City='Berlin' OR City='München');

# SQL ORDER BY Keyword, default is abscend. 
SELECT column_name, column_name
FROM table_name
ORDER BY column_name ASC|DESC, column_name ASC|DESC;

SELECT * FROM Customers
ORDER BY Country; 

SELECT * FROM Customers
ORDER BY Country DESC;

SELECT * FROM Customers
ORDER BY Country, CustomerName;

SELECT * FROM Customers
ORDER BY Country ASC, CustomerName DESC;

# INSERT INTO statement is used to insert new records in a table.
INSERT INTO table_name
VALUES (value1,value2,value3,...);

INSERT INTO table_name (column1,column2,column3,...)
VALUES (value1,value2,value3,...);

INSERT INTO Customers (CustomerName, ContactName, Address, City, PostalCode, Country) #The CustomerID column is automatically updated with a unique number for each record in the table.
VALUES ('Cardinal','Tom B. Erichsen','Skagen 21','Stavanger','4006','Norway');

INSERT INTO Customers (CustomerName, City, Country)
VALUES ('Cardinal', 'Stavanger', 'Norway'); 

# SQL UPDATE Statement
UPDATE table_name
SET column1=value1,column2=value2,...
WHERE some_column=some_value;   # The WHERE clause specifies which record or records that should be updated. If you omit the WHERE clause, all records will be updated!

UPDATE Customers
SET ContactName='Alfred Schmidt', City='Hamburg'
WHERE CustomerName='Alfreds Futterkiste'; 







