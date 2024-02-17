## Rank()

```sql
select * ,
Rank() OVER (order by salary ASC) as rank
from Employee

-- OR
select
Rank() OVER (order by salary ASC) as rank
from Employee

output :

salary      rank
10000        1
20000        2
20000        2
30000        4
.
.
.
```

## Dence_Rank()

```sql
select * ,
Dense_Rank() OVER (order by salary ASC) as rank
from Employee

-- OR
select
Dense_Rank() OVER (order by salary ASC) as rank
from Employee

output :

salary      rank
10000        1
20000        2
20000        2
30000        3
.
.
.
```

## Row_Number()

```sql
select * ,
Row_Number() OVER (order by salary ASC) as rank
from Employee

-- OR
select
Row_Number() OVER (order by salary ASC) as rank
from Employee

output :

salary      rank
10000        1
20000        2
20000        3
30000        4
.
.
.
```

## Question

### Write a SQL query for third Highest Salary.

```sql
select
Dense_Rank() OVER (order by salary ASC) as rank
from Employee limit 2,1
```
