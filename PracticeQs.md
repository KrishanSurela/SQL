## Practice Qs : -

### Create new database and table
```sql
CREATE DATABASE ecb;
USE  ecb;
CREATE TABLE class(
	id INT,
    name VARCHAR(30),
    subject VARCHAR(30),
    marks INT
);

```
### Modify column datatype and constraint
```sql
ALTER TABLE TEACHER
MODIFY id INT PRIMARY KEY;
```
### Insert data into table

```sql
INSERT INTO TEACHER (id,name,subject,marks) 
VALUES
(23,"AJAY MEENA","MATH",405),
(47,"BHARAT","ENGLISH",566),
(18,"CHETAN","CHEMISTRY",567),
(9,"DIVYA","PHYSICS",600);
```

### Select salary of those teacher who have salary above 3500

```sql 
SELECT * FROM TEACHER
WHERE salary>3500;
```
### Rename Column

```sql 
ALTER TABLE TEACHER
RENAME COLUMN ACHIVE_MARK TO salary;
```
### Update teacher salary


```sql 
update teacher set 
salary=50000 where id=47;

update teacher set 
salary=50000 where id=4;

```
### Increment in salary of 25%

```sql
update teacher set 
salary=salary+salary*.25;
```

### Rename table from class to teacher
```sql
ALTER TABLE class
RENAME TEACHER;
```
### Add New Column into Table
```sql
ALTER TABLE teacher
ADD COLUMN city VARCHAR(40) DEFAULT "GURGOAN";
```

### Drop column from table
```sql
ALTER TABLE teacher
DROP COLUMN city;
```
### Create table student
```sql
CREATE TABLE student(
	roll_no INT,
	name VARCHAR(20),
	city VARCHAR(40),
	marks INT
);
```
### insert data into student table
```sql
INSERT INTO student 
(roll_no,name,city,marks) 
VALUES 
(110,"adam","delhi",76),
(108,"bob","Mumbai",65),
(124,"cassy","Pune",94),
(112,"duke","Pune",80);
```
### Display data of student who have marks above 75
```sql
select * from student 
where marks>75;
``` 
### Select distinct data from table

```sql
select distinct city from student;

select city from student 
group by city;
```
### Maximum marks City wise
```sql
select city ,MAX(marks) from student 
group by city;
```
### Avarage marks of students
```sql
select avg(marks) from student;
```
### Add New Column into table
```sql
ALTER TABLE student
ADD COLUMN grade VARCHAR(10);
```
### Set the grade "O" ,"A" and "B" According to marks :-
```sql
update student 
set grade="O" 
where marks>80;

update student 
set grade="A" 
where 70<=marks AND marks<=80;

update student 
set grade="B" 
where 60<=marks AND marks<70;
```
 