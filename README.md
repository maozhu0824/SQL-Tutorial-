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


# SQL DELETE Syntax
DELETE FROM table_name
WHERE some_column = some value; # Where specifies which records that should be deleted, if omitted, all records will be deleted. 

DELETE FROM Customers
WHERE CustomerName = 'Alfreds Futterkiste' AND ContactName = 'Maria Anders';

DELETE FROM table_name;

DELETE * FROM table_name;


# SQL Injection 
# SQL injection is a technique where malicious users can inject SQL commands into an SQL statement, via web page input, and injected SQL commands can alter SQL statement and compromise the security of a web application 

uName = getRequestString("UserName")
uPass = getRequestString("UserPass")
sql = "SELECT * FROM Users WHERE Name = '" + uName + "' AND Pass = '" + uPass + "'"  # SELECT * FROM Users WHERE Name = "" or "=" AND Pass = "" or ""="", it returns all rows from table Users, since WHERE ""="" is always true. 

SELET * FROM Users;
DROP TABLE Suppliers  # return all rows in Users table, delete the table called Suppliers 

# The only proven way to protect a web site from SQL injection attacks, is to use SQL parameters. SQL parameters are values that are added to an SQL query at execution time, in a controlled manner. 
txtUserId = getRequestString("UserId");
txtSQL = "SELECT * FROM Users WHERE UserId = @0"
db. Execute(txtSQL, txtUserId); 

txtNam = getRequestString("CustomerName");
txtAdd = getRequestString("Address"); 
txtCit = getRequestString("City"); 
txtSQL = "INSERT INTO Customers (CustomerName, Address, City) Values (@0, @1, @2)"; 
db. Execute(txtSQL, txtNam, txtAdd, txtCit); 

# How to build parameterized queries in some common web languages: 
# SELECT STATEMENT IN ASP.NET
txtUserId = getRequestString("UserId");
sql = "SELECT * FROM Customers WHERE CustomerId = @0"; 
command = new SqlCommand(sql); 
command.Parameters.AddWithValue("@0", txtUserID); 
command.ExecuteReader(); 

# INSERT INTO STATEMENT IN ASP.NET: 
txtNam = getRequestString("CustomerName");
txtAdd = getRequestString("Address");
txtCit = getRequestString("City");
txtSQL = "INSERT INTO Customers (CustomerName,Address,City) Values(@0,@1,@2)";
command = new SqlCommand(txtSQL);
command.Parameters.AddWithValue("@0",txtNam);
command.Parameters.AddWithValue("@1",txtAdd);
command.Parameters.AddWithValue("@2",txtCit);
command.ExecuteNonQuery();

# INSERT INTO STATEMENT IN PHP: 
$stmt = $dbh->prepare("INSERT INTO Customers (CustomerName,Address,City) 
VALUES (:nam, :add, :cit)");
$stmt->bindParam(':nam', $txtNam);
$stmt->bindParam(':add', $txtAdd);
$stmt->bindParam(':cit', $txtCit);
$stmt->execute();

# SQL SELECT TOP Clause: specify the number of records to return. 
# SQL Server and MS Access 
SELECT TOP number/percent column_name(s)
FROM table_name; 

SELECT TOP 50 PERCENT * FROM Customers; 
SELECT TOP 2 * FROM Customers; 

# MySQL 
SELECT Column_name(s)
FROM table_name
LIMIT number; 

SELECT * FROM Persons
LIMIT 5; 

# Oracle 
SELECT * FROM Persons
WHERE ROWNUM <= 5; 


# SQL Like Operator: used to search for a specified pattern in a column. 
SELECT column_name(s)
FROM table_name
WHERE column_name LIKE pattern; 

SELECT * FROM Customers
WHERE City LIKE 's%';   # select all customers with a city starting with the letter "s"

SELECT * FROM Customers
WHERE City LIKE '%s';   # selects all customers with a City ending with the letter "s" 

SELECT * FROM Customers
WHERE Country LIKE '%land%';  # selects all customers with a Country containing the pattern "land" 

SELECT * FROM Customers
WHERE Country NOT LIKE '%land%';  # selects all customers with Country NOT containing the pattern "land" 


# SQL Wildcard Characters 
# % A substitute for zero or more characters 
# _ A substitute for a single character
# [charlist] Sets and ranges of characters to match 
# [^charlist] Matches only a character not specified within the brackets 
# [!charlist] 
SELECT * FROM Customers
WHERE City LIKE 'ber%';  # selects all customers with a City starting with "ber" 

SELECT * FROM Customers
WHERE City LIKE '%es%'  # selects all customers with a City containing the pattern "es" 

SELECT * FROM Customers
WHERE City LIKE '_erlin';  # selects all customers with a City starting with any character, followed by "erlin" 

SELECT * FROM Customers
WHERE City LIKE 'L_n_on';  # selects all customers with a City starting with "L", followed by any character, followed by "n", followed by any character, followed by "on" 

SELECT * FROM Customers
WHERE City LIKE '[bsp]%';  # selects all customers with a City starting with "b", "s", or "p" 

SELECT * FROM Customers
WHERE City LIKE '[a-c]%';  # selects all customers with a City starting with "a", "b", or "c" 

SELECT * FROM Customers
WHERE City LIKE '[!bsp]%';   # selects all customers with a City NOT starting with "b", "s", or "p" 

SELECT * FROM Customers
WHERE City NOT LIKE '[bsp]%';   # selects all customers with a City NOT starting with "b", "s", or "p" 


# IN operator: allows you to specify multiple values in a WHERE clause.
SELECT column_name(s)
FROM table_name
WHERE column_name IN (value1,value2,...);

SELECT * FROM Customers
WHERE City in ('Paris','London'); 

# SQL BETWEEN Operator: BETWEEN operator selects values within a range. The values can be numbers, text, or dates.
SELECT column_name(s)
FROM table_name
WHERE column_name BETWEEN value1 AND value2;

SELECT * FROM Products
WHERE Price BETWEEN 10 AND 20; 

# SQL Aliases: SQL aliases are used to temporarily rename a table or a column heading.SQL aliases are used to give a database table, or a column in a table, a temporary name. Basically aliases are created to make column names more readable.
SELECT column_name AS alias_name
FROM table_name;

SELECT column_name(s)
FROM table_name AS alias_name; 

SELECT CustomerName AS Customer, ContactName AS [Contact Person]
FROM Customers;

SELECT CustomerName, Address+', '+City+', '+PostalCode+', '+Country AS Address
FROM Customers;

# Mysql 
SELECT CustomerName, CONCAT(Address,', ',City,', ',PostalCode,', ',Country) AS Address
FROM Customers;

# The following SQL statement selects all the orders from the customer with CustomerID=4 (Around the Horn). We use the "Customers" and "Orders" tables, and give them the table aliases of "c" and "o" respectively (Here we have used aliases to make the SQL shorter):

SELECT o.OrderID, o.OrderDate, c.CustomerName
FROM Customers AS c, Orders AS o
WHERE c.CustomerName="Around the Horn" AND c.CustomerID=o.CustomerID; 


# SQL joins are used to combine rows from two or more tables.
SELECT Orders.OrderID, Customers.CustomerName, Orders.OrderDate
FROM Orders
INNER JOIN Customers
ON Orders.CustomerID=Customers.CustomerID;

# INNER JOIN: Returns all rows when there is at least one match in BOTH tables
SELECT column_name(s)
FROM table1
INNER JOIN table2
ON table1.column_name=table2.column_name;

SELECT column_name(s)
FROM table1
JOIN table2
ON table1.column_name=table2.column_name;

SELECT Customers.CustomerName, Orders.OrderID
FROM Customers
INNER JOIN Orders
ON Customers.CustomerID=Orders.CustomerID
ORDER BY Customers.CustomerName;
# Note: The INNER JOIN keyword selects all rows from both tables as long as there is a match between the columns. If there are rows in the "Customers" table that do not have matches in "Orders", these customers will NOT be listed.


# LEFT JOIN: Return all rows from the left table, and the matched rows from the right table
# The LEFT JOIN keyword returns all rows from the left table (table1), with the matching rows in the right table (table2). The result is NULL in the right side when there is no match.
SELECT column_name(s)
FROM table1
LEFT JOIN table2
ON table1.column_name=table2.column_name;

SELECT column_name(s)
FROM table1
LEFT OUTER JOIN table2
ON table1.column_name=table2.column_name;

SELECT Customers.CustomerName, Orders.OrderID
FROM Customers
LEFT JOIN Orders
ON Customers.CustomerID=Orders.CustomerID
ORDER BY Customers.CustomerName;  #Customer Name all show up, if Orders ID not found, then leave blank. The LEFT JOIN keyword returns all the rows from the left table (Customers), even if there are no matches in the right table (Orders).


# RIGHT JOIN: Return all rows from the right table, and the matched rows from the left table
# The RIGHT JOIN keyword returns all rows from the right table (table2), with the matching rows in the left table (table1). The result is NULL in the left side when there is no match.
SELECT column_name(s)
FROM table1
RIGHT JOIN table2
ON table1.column_name=table2.column_name;

SELECT column_name(s)
FROM table1
RIGHT OUTER JOIN table2
ON table1.column_name=table2.column_name;

SELECT Orders.OrderID, Employees.FirstName
FROM Orders
RIGHT JOIN Employees
ON Orders.EmployeeID=Employees.EmployeeID
ORDER BY Orders.OrderID;   #The RIGHT JOIN keyword returns all the rows from the right table (Employees), even if there are no matches in the left table (Orders).


# FULL JOIN: Return all rows when there is a match in ONE of the tables
# The FULL OUTER JOIN keyword combines the result of both LEFT and RIGHT joins.
SELECT column_name(s)
FROM table1
FULL OUTER JOIN table2
ON table1.column_name=table2.column_name;

SELECT Customers.CustomerName, Orders.OrderID
FROM Customers
FULL OUTER JOIN Orders
ON Customers.CustomerID=Orders.CustomerID
ORDER BY Customers.CustomerName; # The FULL OUTER JOIN keyword returns all the rows from the left table (Customers), and all the rows from the right table (Orders). If there are rows in "Customers" that do not have matches in "Orders", or if there are rows in "Orders" that do not have matches in "Customers", those rows will be listed as well.


# SQL UNION operator combines the result of two or more SELECT statements.
# Notice that each SELECT statement within the UNION must have the same number of columns. The columns must also have similar data types. Also, the columns in each SELECT statement must be in the same order.
SELECT column_name(s) FROM table1
UNION
SELECT column_name(s) FROM table2;
# Note: The UNION operator selects only distinct values by default. To allow duplicate values, use the ALL keyword with UNION. PS: The column names in the result-set of a UNION are usually equal to the column names in the first SELECT statement in the UNION.
SELECT column_name(s) FROM table1
UNION ALL
SELECT column_name(s) FROM table2;

SELECT City FROM Customers
UNION
SELECT City FROM Suppliers
ORDER BY City; 

# UNION cannot be used to list ALL cities from the two tables. If several customers and suppliers share the same city, each city will only be listed once. UNION selects only distinct values. Use UNION ALL to also select duplicate values!
SELECT City FROM Customers
UNION ALL
SELECT City FROM Suppliers
ORDER BY City; 


















