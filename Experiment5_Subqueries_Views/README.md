# Experiment 5: Subqueries and Views

## AIM
To study and implement subqueries and views.

## THEORY

### Subqueries
A subquery is a query inside another SQL query and is embedded in:
- WHERE clause
- HAVING clause
- FROM clause

**Types:**
- **Single-row subquery**:
  Sub queries can also return more than one value. Such results should be made use along with the operators in and any.
- **Multiple-row subquery**:
  Here more than one subquery is used. These multiple sub queries are combined by means of ‘and’ & ‘or’ keywords.
- **Correlated subquery**:
  A subquery is evaluated once for the entire parent statement whereas a correlated Sub query is evaluated once per row processed by the parent statement.

**Example:**
```sql
SELECT * FROM employees
WHERE salary > (SELECT AVG(salary) FROM employees);
```
### Views
A view is a virtual table based on the result of an SQL SELECT query.
**Create View:**
```sql
CREATE VIEW view_name AS
SELECT column1, column2 FROM table_name WHERE condition;
```
**Drop View:**
```sql
DROP VIEW view_name;
```

**Question 1**
--
-- Write a SQL query to Find employees who have an age less than the average age of employees with incomes over 1 million

Employee Table

name             type

------------   ---------------

id                    INTEGER

name              TEXT

age                 INTEGER

city                 TEXT

income           INTEGER

```sql
-- select *
from Employee
where age < (select avg(age) from Employee where income > 1000000);

```

**Output:**

<img width="1240" height="512" alt="image" src="https://github.com/user-attachments/assets/dbbb6801-3fc9-423c-a861-e6ce3711e4ee" />


**Question 2**
---
-- From the following tables, write a SQL query to find all the orders generated in New York city. Return ord_no, purch_amt, ord_date, customer_id and salesman_id.

SALESMAN TABLE

name               type
-----------        ----------
salesman_id  numeric(5)
name             varchar(30)
city                 varchar(15)
commission   decimal(5,2)

ORDERS TABLE

name            type
----------      ----------
ord_no          int
purch_amt    real
ord_date       text
customer_id  int
salesman_id  int

```sql
-- select o.ord_no,o.purch_amt,o.ord_date,o.customer_id,o.salesman_id
from ORDERS o
join salesman s on o.salesman_id=s.salesman_id
where s.city='New York';
```

**Output:**
<img width="1237" height="592" alt="image" src="https://github.com/user-attachments/assets/9d83444f-eabe-4946-8ba8-867d01c10982" />


**Question 3**
---
-- From the following tables, write a SQL query to find those salespeople who earned the maximum commission. Return ord_no, purch_amt, ord_date, and salesman_id.

salesman table

name             type
---------------  ---------------
salesman_id      numeric(5)
name                 varchar(30)
city                    varchar(15)
commission       decimal(5,2)

orders table

name             type
---------------  --------
order_no         int
purch_amt        real
order_date       text
customer_id      int
salesman_id      int

```sql
-- select ord_no,purch_amt,ord_date,salesman_id from orders
where salesman_id in (select salesman_id from salesman where commission = (select max(commission) from salesman));
```

**Output:**

<img width="1231" height="542" alt="image" src="https://github.com/user-attachments/assets/90d3def3-6641-4a8e-9d36-2178ae6d2b11" />


**Question 4**
---
-- Write a SQL query to retrieve all columns from the CUSTOMERS table for customers whose salary is greater than $4500.

Sample table: CUSTOMERS

ID          NAME        AGE         ADDRESS     SALARY
----------  ----------  ----------  ----------  ----------

1          Ramesh     32              Ahmedabad     2000
2          Khilan        25              Delhi                 1500
3          Kaushik      23              Kota                  2000
4          Chaitali       25             Mumbai            6500
5          Hardik        27              Bhopal              8500
6          Komal         22              Hyderabad       4500

7           Muffy          24              Indore            10000

```sql
-- select * from CUSTOMERS
where SALARY in (select SALARY from CUSTOMERS where SALARY > 4500);
```

**Output:**

<img width="1228" height="523" alt="image" src="https://github.com/user-attachments/assets/75cefbc6-d3e4-43c6-99c2-a3c2a133aeda" />


**Question 5**
---
-- Write a SQL query that retrieve all the columns from the table "Grades", where the grade is equal to the maximum grade achieved in each subject.

Sample table: GRADES
```sql
-- select * from GRADES g1
where grade = (select max(grade) from GRADES g2 where g1.subject=g2.subject);
```

**Output:**

<img width="1232" height="540" alt="image" src="https://github.com/user-attachments/assets/d21b5973-5568-4062-8590-33391345e0f1" />


**Question 6**
---
-- Write a SQL query to retrieve all columns from the CUSTOMERS table for customers whose AGE is LESS than $30

Sample table: CUSTOMERS

ID          NAME        AGE         ADDRESS     SALARY
----------  ----------  ----------  ----------  ----------

1          Ramesh     32              Ahmedabad     2000
2          Khilan        25              Delhi                 1500
3          Kaushik      23              Kota                  2000
4          Chaitali       25             Mumbai            6500
5          Hardik        27              Bhopal              8500
6          Komal         22              Hyderabad       4500

7           Muffy          24              Indore            10000

```sql
-- select * from CUSTOMERS
where age IN  (select age from CUSTOMERS where age<30);
```

**Output:**

<img width="1237" height="677" alt="image" src="https://github.com/user-attachments/assets/ae02cce0-bf1d-47aa-a66f-8d6b54986cb6" />


**Question 7**
---
--From the following tables, write a SQL query to find all the orders issued by the salesman 'Paul Adam'. Return ord_no, purch_amt, ord_date, customer_id and salesman_id.

```sql
-- select * from Orders
where salesman_id = (select salesman_id from Salesman where name='Paul Adam');
```

**Output:**

<img width="1228" height="502" alt="image" src="https://github.com/user-attachments/assets/dac9986f-3211-443b-a5ac-b0e298259821" />


**Question 8**
---
-- Write a SQL query to retrieve all columns from the CUSTOMERS table for customers whose salary is LESS than $2500.

Sample table: CUSTOMERS

ID          NAME        AGE         ADDRESS     SALARY
----------  ----------  ----------  ----------  ----------

1          Ramesh     32              Ahmedabad     2000
2          Khilan        25              Delhi                 1500
3          Kaushik      23              Kota                  2000
4          Chaitali       25             Mumbai            6500
5          Hardik        27              Bhopal              8500
6          Komal         22              Hyderabad       4500

7           Muffy          24              Indore            10000

```sql
-- select * from CUSTOMERS
where SALARY in (select SALARY from CUSTOMERS where SALARY < 2500);
```

**Output:**

<img width="1246" height="553" alt="image" src="https://github.com/user-attachments/assets/a39fee94-81da-47a9-94d4-9a3f79b9e060" />


**Question 9**
---
-- Write a SQL query that retrieves the names of students and their corresponding grades, where the grade is equal to the maximum grade achieved in each subject.

Sample table: GRADES

```sql
-- select student_name,grade from GRADES g1
where grade = (select max(grade) from GRADES g2 where g1.subject=g2.subject);
```

**Output:**

<img width="1242" height="523" alt="image" src="https://github.com/user-attachments/assets/aa869991-927b-4f3f-be6d-9343b859ba30" />


**Question 10**
---
-- From the following tables write a SQL query to count the number of customers with grades above the average in New York City. Return grade and count.

customer table

name         type
-----------  ----------
customer_id  int
cust_name    text
city         text
grade        int
salesman_id  int

```sql
-- select grade,COUNT(*) from customer
where grade > (select avg(grade) from customer where city='New York')
group by grade;
```

**Output:**
<img width="1253" height="442" alt="image" src="https://github.com/user-attachments/assets/e845e246-c621-4ff1-85b2-7a3b9d14fe0a" />



## RESULT
Thus, the SQL queries to implement subqueries and views have been executed successfully.
