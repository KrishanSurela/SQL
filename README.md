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
INSERT INTO student VALUES (101,"KRISHAN",23),(102,"SURELA",21);
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
    CONSTRAINT age_check CHECK (age>=13 AND Followers>=100)
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
   Followers INT DEFAULT 0,
   Following INT
   CONSTRAINT age_check CHECK (age>=13 AND Followers>=100));
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
   CONSTRAINT age_check CHECK (age>=13 AND Followers>=100));
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
WHERE email IN ("k@gmail.com","kri@gmail.com");

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
SELECT * FROM Teachers WHERE age > ALL (SELECT age FROM Students);
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
SELECT * FROM Teachers WHERE age = ANY (SELECT age FROM Students);
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

- COUNT()
- MAX()
- MIN()
- SUM()
- AVG()

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


