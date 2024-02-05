# SQL (Structured Query Language)

-   SQL is not Database , It is a Query Based language.
-   MySQL is DataBase , and We read SQL for use MySQL database

# What is a Database ?

## It is Collection of data in a format that can be easily accessed.

### Why DataBases ?

-   can store large data
-   features like security ,scalability etc.
-   Easier to insert , update or delete data

## Types of databases

### SQL v/s NoSQL

#### SQL ->

-   It is Relational dataBase , We can Store data in the form of table.
-   eg. MySQL, Oracle, PostgreSQL etc,

#### NoSQL ->

-   It is non relational database in which we can store data in the form of document/key-val pair / graphs etc.
-   eg. MongoDB , Cassandra, Neo4j etc.

## SQL (Structured Query Language) - Definition

-   SQL is a programming language used to interact with relational databases like mySQL,PostgreSQL

### What is Table ?

-   There is 2 component ->
-   (i) Columns(Design of table) or Schema
-   (ii) Rows or Taple (it has imformation of single entity)

## MySQL is case in-sensitive database platform.

## Query For Create DataBase

```sql
CREATE DATABASE database_name;
```

## Query For Drop DataBase

```sql
DROP DATABASE database_name;
```

-   This SQL command only use when database already created

## Query for create table in existing Database

```sql
USE existing_database_name;
CREATE TABLE student{
    rollno INT,
    name VARCHAR(40),
    age INT
};
```

## Query for insert data into existing table

```sql
INSERT INTO student
VALUES (101,"KRISHAN",23),(102,"SURELA",21);
```

## Query for Retrive all Data from Table

```sql
SELECT * FROM student;
```

## Database create if not exist

```sql
CREATE DATABASE IF NOT EXISTS college;
```

-   There is no error if database is already created. Warning but not create database

## Query for Drop Database if exists

```sql
DROP DATABASE IF EXISTS instagram;
```

## Display all databases information

```sql
SHOW DATABASES;
```

## Display all the Tables from a single Database

```sql
USE database_name;
SHOW TABLES;
```

# Table Queries

-   ### Create
-   ### Insert
-   ### Update
-   ### Alter
-   ### Truncate
-   ### Delete

## 1. Create Command

-   To create a table we write create command

-   It defined a schema or columns in a table

```sql
CREATE TABLE user(
    id INT,
    Name VARCHAR(40),
    Email VARCHAR(25),
    Followers INT (10)
    Following INT (10)
);
```

## Constraints

### Rules for the data in the table

-   #### NOT NULL = > (Columns cannot have a null value)

-   #### UNIQUE = > (All values in column are different)

-   #### DEFAULT = > (Sets the default value of a column)

-   #### CHECK = > ( It can limit the values allowed in column)

```sql
CREATE TABLE user(
    id INT,
    age INT,
    Name VARCHAR(30) NOT NULL,
    Email VARCHAR(30) UNIQUE,
    Followers INT DEFAULT 0,
    Following INT
    CONSTRAINT age_check
    CHECK (age>=13 AND Followers>=100)
);
```

## Other important Constrainst

### PRIMARY KEY

-   #### It makes a column unique & not null but used only for one
-   #### It is a column (or set of columns) in a table that uniquely identifies each row. There is only 1 PRIMARY KEY and it should be not null

```sql
CREATE TABLE user(
   id INT,
   age INT,
   Name VARCHAR(30) NOT NULL,
   Email VARCHAR(30) UNIQUE,
   Followers INT,
   Following INT,
   CONSTRAINT age_check
   CHECK (age>=13 AND Followers>=100));
   PRIMARY KEY(id)
);

   //OR

CREATE TABLE user(
   id INT PRIMARY KEY,
   age INT,
   Name VARCHAR(30) NOT NULL,
   Email VARCHAR(30) UNIQUE,
   Followers INT,
   Following INT,
   CONSTRAINT age_check
   CHECK (age>=13 AND Followers>=100));
);

```

### FOREIGN KEY

-   #### It prevent actions that would destroy links between tables

-   #### A foreign key is a column(or set of columns) in a table that refer to the primary key in another table.

-   #### FOREIGN KEY have duplicate and null values.

-   #### There can be multiple FOREIGN KEY

```sql

USE college;

CREATE TABLE user(
    id INT,
    age INT,
    Name VARCHAR(30) NOT NULL,
    Email VARCHAR(30) UNIQUE,
    Followers INT DEFAULT 0,
    Following INT,
    CONSTRAINT age_check CHECK (age>=13),
    PRIMARY KEY(id)
);

CREATE TABLE post (
	id INT PRIMARY KEY,
	content VARCHAR(100),
	user_id INT,
	FOREIGN KEY (user_id) REFERENCES user(id)
);
```

## 2. Insert Command

```sql
INSERT INTO user
(id, age, name,email,followers,following)
VALUES
(1,14,"Krishan","k@gmail.com",300,360),
(2,14,"Kumar","kr@gmail.com",310,370),
(3,14,"Surela","kri@gmail.com",360,520),
(4,14,"Bansur","k@gmail.com",330,160),
```

## 3. Select Cammand

### Selects & show data from the table in DB

```sql
=>SELECT id,name,email FROM user;

=>SELECT * FROM user;

```

### Select unique data in order to column from table

```sql
=> SELECT DISTINCT age FROM user
```

### Where Clause

-   To define some condition

```sql
=> SELECT col1,col2
FROM table_name
WHERE conditions;

=> SELECT name ,followers
FROM user
WHERE age >=10;

```

### Where Clause Operators

#### Arithmetic Operators

-   +, - , \* , / , %

##### FIND THE USER WHO ARE GOING TO BE 18 YEAR OLD NEXT YEAR

```SQL
SELECT name,age
FROM user
WHERE age+1=18;
```

##### FIND THE USER WHO WAS ALREADY 18 YEAR OLD PREVIOUS YEAR

```SQL
SELECT name,age
FROM user
WHERE age-1=18;
```

#### Comparison Operators

-   = , != , > , < , >= , <=

```sql
SELECT name ,followers
FROM user
WHERE age >=10;
```

#### Logical Operators

##### AND => ( To check for both conditions to be true)

```sql
SELECT name,age
FROM user
WHERE age>15 AND followers>200;
```

##### OR => ( To check for of of the condition to be true)

```sql
SELECT name,age
FROM user
WHERE age>15 OR followers>200;
```

##### NOT => (To negate the given condition)

```sql
SELECT name,age,email
FROM user
WHERE age NOT IN (14,16);
```

##### IN => (Matches any value in the GIVEN list)

```sql
=> SELECT name,age
FROM user
WHERE email
IN ("k@gmail.com","kri@gmail.com");

=> SELECT name,age,email
FROM user
WHERE age IN (14,16);
```

##### BETWEEN => (Selects for given range )

```sql
SELECT name,age
FROM user
WHERE age BETWEEN 14 AND 18;
```

#### ALL =>It used to compare a value to all values in a list or returned by a subquery.

##### Here’s an example where we want to find teachers whose age is greater than all students:

```sql
SELECT * FROM Teachers
WHERE age > ALL
(SELECT age FROM Students);
```

#### LIKE => The LIKE operator is used in a WHERE clause to search for a specified pattern in a column.

#### Here’s an example where we want to find all customers that name start with “a” and are at least 3 characters in length:

-   Name start with “a” and are at least 3 characters in length:

```sql
SELECT * FROM Customers
WHERE CustomerName
LIKE 'a__%';
```

-   Starts With a

```sql
SELECT * FROM Customers
WHERE CustomerName
LIKE 'a%';
```

-   Ends With a

```sql
SELECT * FROM Customers
WHERE CustomerName
LIKE '%a';
```

-   Contains a phrase 'or' in Customer Name

```sql
SELECT * FROM Customers
WHERE CustomerName
LIKE '%or%';
```

-   Specific Position: The _ wildcard represents a single character. It can be any character or number, but each _ represents one, and only one, character. For example, to return all user from a name column that starts with ‘P’ followed by one wildcard character, then ‘am’ and then two wildcard characters

```sql
SELECT * FROM user
WHERE name
LIKE 'P_am__';
```

-   Multiple Values: We can use the LIKE operator with multiple string patterns using the OR operator. For example, to return all customers that start with ‘a’ or start with ‘b’

```sql
SELECT * FROM Customers
WHERE
CustomerName LIKE 'a%'
OR
CustomerName LIKE 'b%';
```

#### ANY => The ANY operator is used to compare a value to any applicable value in a list or returned by a subquery.

-   Here’s an example where we want to find teachers whose age is similar to any of the student’s age

```sql
SELECT * FROM Teachers
WHERE age = ANY
(SELECT age FROM Students);
```

### Bitwise Operators

-   & (Bitwise AND) , | (Bitwise OR)

### LIMIT Clause =>

#### It sets upper limit on number of row (tuples) to be returned

```sql
=> SELECT name,age
FROM user
WHERE age>=14
LIMIT 2;

=> SELECT name,age
FROM user
LIMIT 2;
```

#### With OFFSET: To skip the first 5 rows and then return the next 10 rows

```sql
=> SELECT * FROM employees
 LIMIT 10 OFFSET 5;

//OR

=> SELECT * FROM employees
 LIMIT 5, 10;
```

### Questions :

#### To get the name with 2nd highest followers

```sql
SELECT name FROM user
ORDER BY followers DESC LIMIT 1,1;
```

#### To get the name with 3rd highest followers

```sql
SELECT name FROM user
ORDER BY followers DESC LIMIT 2,1;
```

### ORDER BY Clause =>

#### To sort the data in Ascending(ASC) or Descending(DESC) Order

#### Order By (Defaultly Ascending Order)

```sql
=> SELECT col1,col2
FROM table_name
ORDER BY col_name(s) ASC;

=> SELECT name,age
FROM user
ORDER BY age DESC
LIMIT 3;

=>
SELECT name,age
FROM user
ORDER BY age ASC;

=> SELECT name,age
FROM user
ORDER BY age;
```

### Aggregate Functions =>

#### Aggregate functions are predefined function in SQL , It perfoms a calculation on a set of values , and return a single value.

-   COUNT()
-   MAX()
-   MIN()
-   SUM()
-   AVG()

#### Example :

```sql
=> SELECT MAX(age)
FROM user;

=> SELECT COUNT(age)
FROM user
WHERE age =14;

=> SELECT MIN(age)
FROM user;

=> SELECT AVG(age)
FROM user;

=> SELECT SUM(Followers)
FROM user;
```

### Group By Clause =>

#### Groups rows that have the same values into summary rows.

#### It collects data from multiple records and groups the result by one or more column

#### \* Generally we use group by with some aggregation function

```sql
SELECT age,COUNT(id)
FROM user
GROUP BY age;
```

#### Output :

```sql
 Age      COUNT(id)
  14          2
  15          1
  17          1
  19          2
```

#### Maximum Followers Group :

```sql
SELECT age,MAX(Followers)
FROM user
GROUP BY age;
```

#### Output : Here maximum followers are 360 in the 14 year age group and so on...

```sql
 Age      COUNT(Followers)
  14          360
  15          310
  17          330
  19          350
```

#### We can not write this type of query

#### \* The field we are going to select outside of Aggregation function should be same according to column that is using in group by clause.

```sql
SELECT name,age,MAX(Followers)
FROM user
GROUP BY age;
```

### HAVING Clause

#### Similiar to Where clause i.e. applies some condition on rows

#### But it is used when we want to apply any condition after grouping.

#### \* WHERE is for the table, HAVING is for group

#### \* Grouping is necessary for HAVING

```sql
SELECT age , MAX(Followers)
FROM user
GROUP BY age
HAVING MAX(Followers)>320;
```

### GENERAL ORDER FOR Clauses

```sql
SELECT column(s)
FROM table_name
WHERE condition
GROUP BY column(s)
HAVING condition
ORDER BY column(s) ASC;
```

### Table Query : -

-   Update (To update existing rows)

```sql
UPDATE user
SET Followers=600
WHERE age =15;
SET SQL_SAFE_UPDATE=0;
```

-   Delete ( To delete existing rows or tuples)

```sql
DELETE FROM user
WHERE age=14;
```

#### Error : when we delete parent table rows - Means Primary key is in parent table. which is using as a foreign key in another table So we dont able to delete rows from parent table.

-   Error Code: 1451. Cannot delete or update a parent row: a foreign key constraint fails (`college`.`post`, CONSTRAINT `post_ibfk_1` FOREIGN KEY (`user_id`) REFERENCES `user` (`id`)) 0.000 sec

#### Solution :

```sql
DELETE FROM post WHERE
user_id=2;

DELETE FROM user WHERE
id= 2;
```

## ALTER Query : -

-   To change the schema or column

#### ADD Column

```sql
ALTER TABLE user
ADD COLUMN city
VARCHAR(30) NOT NULL
```

#### DROP Column

```sql
ALTER TABLE user
DROP COLUMN city
```

#### MODIFY Column Datatype

-   We can change the data type and constraints of an existing column

```sql
ALTER TABLE post
MODIFY COLUMN id VARCHAR(20);
```

#### RENAME Table

```sql
ALTER TABLE post
RENAME TO student ;
```

#### RENAME Column (To change column name)

-   The RENAME keyword is used to change the name of a table or a column. Not for change the datatypes and constraints

```sql
ALTER TABLE post
RENAME COLUMN
content TO fullname;
```

#### CHANGE Column ( To change column name and its datatypes / constraints)

```sql
ALTER TABLE user
CHANGE COLUMN Followers Subscribers
INT DEFAULT 0;
```

#### TRUNCATE

-   To Delete table's data
-   Primary and Foreign key issue So we drop post table first.

```sql

DROP table post;

TRUNCATE TABLE user;
```

### Candidate Key:

#### The minimal set of attributes that can uniquely identify a tuple is known as a candidate key. For example, STUD_NO in the STUDENT relation is a candidate key. It is a minimal super key. Here’s an example:

```sql
CREATE TABLE STUDENT (
    STUD_NO INT PRIMARY KEY,
    SNAME VARCHAR(100),
    ADDRESS VARCHAR(100),
    PHONE VARCHAR(10)
);
```

-   In this table, STUD_NO is a candidate key because it can uniquely identify each student.

### Super Key:

#### The set of attributes that can uniquely identify a tuple is known as a super key. For example, STUD_NO, (STUD_NO, SNAME), etc. are super keys. A super key is a group of single or multiple keys that identifies rows in a table. Here’s an example:

```sql
CREATE TABLE STUDENT (
    STUD_NO INT,
    SNAME VARCHAR(100),
    ADDRESS VARCHAR(100),
    PHONE VARCHAR(10),
    UNIQUE (STUD_NO, PHONE)
);
```

-   In this table, (STUD_NO, PHONE) is a super key because the combination of STUD_NO and PHONE can uniquely identify each student.

-   Remember, every candidate key is a super key, but not every super key is a candidate key.

### Alternate Key:

#### An alternate key is a candidate key that is not the primary key. It has all the properties to become a primary key and so is an alternate option. For example, consider a Customer table with Customer ID, Pan Number, and Email Address as unique attributes.

-   If Customer ID is chosen as the primary key, then Pan Number and Email Address will be alternate keys.

```sql
CREATE TABLE Customer (
    Customer_ID INT PRIMARY KEY,
    Pan_Number VARCHAR(10) UNIQUE,
    Email_Address VARCHAR(100) UNIQUE
);
```

## INSERT INTO SELECT Statement:-

#### The INSERT INTO SELECT statement copies data from one table and inserts it into another table.

#### The INSERT INTO SELECT statement requires that the data types in source and target tables match.

-   Note: The existing records in the target table are unaffected.

```sql
INSERT INTO Customers (CustomerName, City,Country)
SELECT SupplierName,City,Country FROM Suppliers;
```

## Create Table and copy all column in it from another table

```sql
CREATE TABLE customersbackup2025 AS SELECT * FROM Customers;
```

### IFNULL : -

```sql
SELECT IFNULL(Address,'Address is not given')
FROM Suppliers ;
```

### CASE Expression :-

```sql

=> SELECT OrderID, Quantity,
CASE
    WHEN Quantity > 30 THEN 'The quantity is greater than 30'
    WHEN Quantity = 30 THEN 'The quantity is 30'
    ELSE 'The quantity is under 30'
END AS QuantityText
FROM OrderDetails;
```

## Aliases : -

### SQL aliases are used to give a temporary name to a table, or a column in a table,

### Aliases are often used to make column names more readable.

### An alias only exists for the duration of that query.

### An alias is created with the AS keyword.

### Alias on column

-   To change Column name (CustomerID to ID ) from table---

```sql
=> SELECT column_name AS alias_name
FROM table_name;

=> SELECT CustomerID AS ID
FROM Customers;
```

-   AS is Optional
    Actually, in most database languages, you can skip the AS keyword and get the same result:

```sql
  SELECT CustomerID ID
FROM Customers;
```

### Alias on Table

```sql
SELECT column_name(s)
FROM table_name AS alias_name;
```

### Using [square brackets] for aliases with space characters:

```sql
=> SELECT ProductName AS [My Great Products]
FROM Products;

=> SELECT ProductName AS "My Great Products"
FROM Products;
```

## UNION : -

### The UNION operator is used to combine the result-set of two or more SELECT statements.

-   Every SELECT statement within UNION must have the same number of columns
-   The columns must also have similar data types
-   The columns in every SELECT statement must also be in the same order

```sql
SELECT column_name(s) FROM table1
UNION
SELECT column_name(s) FROM table2;
```

## UNION ALL : -

### The UNION operator selects only distinct values by default. To allow duplicate values, use UNION ALL.

```sql
SELECT column_name(s) FROM table1
UNION ALL
SELECT column_name(s) FROM table2;
```

## UNION With WHERE Clause : -

```sql
SELECT City, Country FROM Customers
WHERE Country='Germany'
UNION
SELECT City, Country FROM Suppliers
WHERE Country='Germany'
ORDER BY City;
```

## JOIN : -

### A JOIN clause is used to combine rows from two or more tables, based on a related column between them.

-   Atleast one Related Column name should be same in both table

## INNER JOIN : -

### Returns records that have matching values in both tables (RETURN COMMON DATA FROM Table)

```sql
=> SELECT Orders.OrderID,
Customers.CustomerName,
Orders.OrderDate
FROM Orders
INNER JOIN Customers ON
Orders.CustomerID=Customers.CustomerID;


=> SELECT Customers.Address,
 Suppliers.PostalCode
FROM Suppliers
INNER JOIN Customers
ON Suppliers.City=Customers.City;

=> INSERT INTO Products
(ProductId,ProductName,CategoryId,Price)
VALUES
(1,"Chais",1,18),
(2,"Chang",	1,19),
(3,"Aniseed Syrup",2,10);

=> INSERT INTO Categories
(CategoryId,CategoryName,Description)
VALUES
(1,"TOYS","children toy"),
(2,"byke","Motor byke"),
(3,"car","Honda car");

=> SELECT  *
FROM Products AS P
INNER JOIN Categories AS C
ON  P.CategoryId=C.CategoryId;

ProductId  ProductName  CategoryId      Price CategoryID     CategoryName   Description
'2',      'Chang',         '1',         '19',   '1',            'TOYS',     'children toy'
'1',      'Chais',         '1',         '18',   '1',            'TOYS',     'children toy'
'3',      'Aniseed Syrup', '2',         '10',   '2',            'byke',     'Motor byke'

```

## LEFT JOIN : -

### Returns all records from the left table, and the matched(comman) records from the right table

```sql
SELECT  *
FROM Products AS P
LEFT JOIN Categories AS C
ON  P.CategoryId=C.CategoryId;


ProductId  ProductName  CategoryId      Price CategoryID     CategoryName   Description
'2',      'Chang',         '1',         '19',   '1',            'TOYS',     'children toy'
'1',      'Chais',         '1',         '18',   '1',            'TOYS',     'children toy'
'3',      'Aniseed Syrup', '2',         '10',   '2',            'byke',     'Motor byke'
```

## RIGHT JOIN

### Returns all records from the right table, and the matched(comman) records from the left table

```sql
SELECT  *
FROM Products AS P
right JOIN Categories AS C
ON  P.CategoryId=C.CategoryId;

ProductId  ProductName  CategoryId      Price CategoryID     CategoryName   Description
'2',       'Chang',         '1',         '19',   '1',            'TOYS',     'children toy'
'1',       'Chais',         '1',         '18',   '1',            'TOYS',     'children toy'
'3',       'Aniseed Syrup', '2',         '10',   '2',            'byke',     'Motor byke'
NULL,       NULL,           NULL,        NULL,   '3',            'car',      'Honda car'
```

## FULL OUTER JOIN

### Returns all records when there is a match in either left or right table

#### The error encountering is because MySQL does not support the FULL OUTER JOIN syntax. However, we can emulate a FULL OUTER JOIN in MySQL using a combination of LEFT JOIN and RIGHT JOIN with a UNION

```sql
SELECT *
FROM Products AS P
LEFT JOIN Categories AS C
ON P.CategoryId = C.CategoryId

UNION

SELECT *
FROM Products AS P
RIGHT JOIN Categories AS C
ON P.CategoryId = C.CategoryId

ProductId  ProductName  CategoryId      Price CategoryID     CategoryName   Description
'2',       'Chang',         '1',         '19',   '1',            'TOYS',     'children toy'
'1',       'Chais',         '1',         '18',   '1',            'TOYS',     'children toy'
'3',       'Aniseed Syrup', '2',         '10',   '2',            'byke',     'Motor byke'
NULL,       NULL,           NULL,        NULL,   '3',            'car',      'Honda car'
```

## SELF JOIN

### A Self join is a regular join in which a table is joined to itself.

### Self Joins are powerful for comparing value of columns with the same table

```sql
=> SELECT column_name(s)
FROM Table AS T1
JOIN Table AS T2
ON T1.col_name = T2.other_col_name;

=> SELECT
T1.empname AS employee_name ,
T2.empname AS manager_name
FROM emp AS T1
JOIN emp AS T2
ON T2.empid = T1.manager_id;
```
