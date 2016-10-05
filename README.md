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

