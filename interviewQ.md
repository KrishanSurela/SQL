## InterView Questions

### Question 1

### Write a query to show all First name in Capital and Last name is small letters with alias ?

```sql
Select Upper(Fname) as First_name,
Lower(Lname) as Last_name from EmployeeInfo;
```

### Question 2

### Write a Query to Show EID, First name , Last name whose first name start with "A" ?

```sql
select EID , Fname , Lname from EmployeeInfo Where Fname LIKE "A%"
```

### Question 3

### Write a query to show Fisrt name ,Last name , Department who are associated with project "p3"?

```sql
select Fname, Lname, Department from EmployeeInfo where project ='P3'
```

### Question 4

### Write a query to show all records salary is more than 200000?

```sql
select * from EmployeeInfo where salary>200000
```

### Question 5

### Write a query to show all records where salary between 50000 and 70000?

```sql
select * from EmployeeInfo where salary>=50000 and salary<=70000
```

### Question 6

### Write a query to show Firstname , Department records where city should be HYD or KRL ?

```sql
select Fname , Department from EmployeeInfo where city LIKE '%HYD%' OR city LIKE '%KRL%'
```

### Question 7

### Write a query to show EmpID, Firstname and salary where salary of an EMployee more than Average Salary ?

```sql
select EmpId , Fname , Salary from EmployeeInfo where salary >(select avg(salary) from EmployeeInfo)
```

### Question 8

### Write a query to show the 5% of increment in salary as "New_Salary" ?

```sql
select salary,salary*.05 as increment ,salary+salary*.05 as New_Salary from EmployeeInfo
```

### Question 9

### Write a query to show emp first and last name who has lowest salary in all records.

```sql
select Fname ,Lname from EmployeeInfo where salary=(select MIN(salary) from EmpoyeeInfo)

-- OR

select Top 1 Fname ,Lname from EmployeeInfo  Order by Salary
```

### Question 10

### Write a query to show records in which Department Count of employee is more than 1 ?

```sql
seletc Department,count(Department) from EmployeeInfo Group By Department Having count(Department)>1
```

### Question 11

### Write a query to find Emp Name who has more than salary from his/her reporting manager Salary? (self join)

```sql
select E.Emp_ID,E.Emp_Name,
M.Emp_Name As Manager_Name,
E.Salary AS Emp_Salary,
M.Salary AS Manager_Salary
from Emp_Manager E INNER JOIN Emp_Manager M
ON E.Manager_ID = M.Emp_ID
where
Emp_Salary>Manager_Salary
```
