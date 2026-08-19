# Experiment 4: Aggregate Functions, Group By and Having Clause

## AIM
To study and implement aggregate functions, GROUP BY, and HAVING clause with suitable examples.

## THEORY

### Aggregate Functions
These perform calculations on a set of values and return a single value.

- **MIN()** – Smallest value  
- **MAX()** – Largest value  
- **COUNT()** – Number of rows  
- **SUM()** – Total of values  
- **AVG()** – Average of values

**Syntax:**
```sql
SELECT AGG_FUNC(column_name) FROM table_name WHERE condition;
```
### GROUP BY
Groups records with the same values in specified columns.
**Syntax:**
```sql
SELECT column_name, AGG_FUNC(column_name)
FROM table_name
GROUP BY column_name;
```
### HAVING
Filters the grouped records based on aggregate conditions.
**Syntax:**
```sql
SELECT column_name, AGG_FUNC(column_name)
FROM table_name
GROUP BY column_name
HAVING condition;
```

**Question 1**
--
-- Create a table named Shipments with the following constraints:
ShipmentID as INTEGER should be the primary key.
ShipmentDate as DATE.
SupplierID as INTEGER should be a foreign key referencing Suppliers(SupplierID).
OrderID as INTEGER should be a foreign key referencing Orders(OrderID).

```sql
-- CREATE TABLE Shipments(
ShipmentID INTEGER PRIMary KEY,
ShipmentDate DATE,
SupplierID INTEGER,
OrderID INTEGER,
FOREIGN KEY (SupplierID) REFERENCES Suppliers(SupplierID),
FOREIGN KEY (OrderID) REFERENCES Orders(OrderID)
);
```

**Output:**

<img width="1242" height="330" alt="image" src="https://github.com/user-attachments/assets/0067c773-9b04-42fa-bc05-2ab0aa0e1825" />


**Question 2**
---
-- Create a table named Products with the following constraints:
ProductID as INTEGER should be the primary key.
ProductName as TEXT should be unique and not NULL.
Price as REAL should be greater than 0.
StockQuantity as INTEGER should be non-negative.

```sql
-- CREATE TABLE Products(
ProductID INTEGER PRIMARY KEY,
ProductName TEXT UNIQUE NOT NULL,
Price REAL CHECK (Price>0),
StockQuantity INTEGER CHECK (StockQuantity > 0)
);
```

**Output:**

<img width="1242" height="368" alt="image" src="https://github.com/user-attachments/assets/b5ecee29-a5c9-4b02-9ca2-e59c7d9b8867" />

**Question 3**
---Insert all students from Archived_students table into the Student_details table.

cid         name        type        notnull     dflt_value  pk
----------  ----------  ----------  ----------  ----------  ----------
0           RollNo      INT           0                       1
1           Name        VARCHAR(100)  0                       0
2           Gender      VARCHAR(10)   0                       0
3           Subject     VARCHAR(50)   0                       0
4           MARKS       INT           0                       0
-- 

```sql
-- INSERT INTO Student_details(RollNo,Name,Gender,Subject,Marks)
SELECT RollNo,Name,Gender,Subject,Marks from Archived_students;
```

**Output:**

<img width="1247" height="377" alt="image" src="https://github.com/user-attachments/assets/8c2eff87-2c46-452f-9180-a08c1c09b407" />


**Question 4**
---
-- Create a table named Orders with the following columns:

OrderID as INTEGER
OrderDate as TEXT
CustomerID as INTEGER

```sql
-- CREATE TABLE Orders(
OrderID INTEGER,
OrderDate TEXT,
CustomerID INTEGER
);
```

**Output:**

<img width="1241" height="468" alt="image" src="https://github.com/user-attachments/assets/88db4b30-adce-439a-85a2-5667bf2539a7" />


**Question 5**
---
-- Insert the following students into the Student_details table:
RollNo      Name        Gender      Subject     MARKS
----------  ----------  ----------  ----------  ----------
202            Ella King         F           Chemistry   87
203            James Bond   M          Literature    78

```sql
-- INSERT INTO Student_details(RollNo,Name,Gender,Subject,Marks)
VALUES(202,"Ella King","F","Chemistry",87),(203,"James Bond","M","Literature",78);
```

**Output:**
<img width="1241" height="353" alt="image" src="https://github.com/user-attachments/assets/b16ed3d3-a2c3-479a-b4b8-c20cef3d3499" />


**Question 6**
---
-- Write an SQL query to add a new column salary of type INTEGER to the Employees table, with a CHECK constraint that ensures the value in this column is greater than 0.

```sql
-- ALTER TABLE Employees ADD salary INTEGER CHECK (salary > 0);
```

**Output:**

<img width="1235" height="382" alt="image" src="https://github.com/user-attachments/assets/cacd5620-56d3-4a6e-b727-7e12e37dec88" />


**Question 7**
---
-- Create a table named Reviews with the following columns:

ReviewID as INTEGER
ProductID as INTEGER
Rating as REAL
ReviewText as TEXT

```sql
-- CREATE TABLE Reviews(
ReviewID INTEGER,
ProductID INTEGER,
Rating REAL,
ReviewText TEXT
);
```

**Output:**

<img width="1228" height="478" alt="image" src="https://github.com/user-attachments/assets/75348520-ffc9-426f-bdf6-59e23caa4976" />


**Question 8**
---
-- Create a table named Locations with the following columns:

LocationID as INTEGER
LocationName as TEXT
Address as TEXT

```sql
-- CREATE TABLE Locations(
LocationID INTEGER,
LocationName TEXT,
Address TEXT
);
```

**Output:**

<img width="1222" height="462" alt="image" src="https://github.com/user-attachments/assets/2b9d0ed9-7625-4c91-8d60-c495686019b0" />


**Question 9**
---
--INSERT INTO Products(ProductID,Name,Category,Price,Stock)
VALUES (101,"Laptop","Electronics",1500,50)

```sql
-- INSERT INTO Products(ProductID,Name,Category,Price,Stock)
VALUES (101,"Laptop","Electronics",1500,50)
```

**Output:**

<img width="1247" height="335" alt="image" src="https://github.com/user-attachments/assets/e22322f9-7c4c-4a33-b6d1-969765ab557b" />


**Question 10**
---
-- Write a SQL query to add birth_date attribute as timestamp (datatype) in the table customer 

Sample table: customer

 customer_id |   cust_name    |    city    | grade | salesman_id 
-------------+----------------+------------+-------+-------------
        3002 | Nick Rimando   | New York   |   100 |        5001
        3007 | Brad Davis     | New York   |   200 |        5001
        3005 | Graham Zusi    | California |   200 |        5002

```sql
-- ALTER TABLE customer ADD birth_date timestamp;

```

**Output:**

<img width="1231" height="436" alt="image" src="https://github.com/user-attachments/assets/0435e461-d096-41a0-8581-1e4bf110af43" />



## RESULT
Thus, the SQL queries to implement aggregate functions, GROUP BY, and HAVING clause have been executed successfully.
