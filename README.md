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


















