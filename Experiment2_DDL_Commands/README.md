# Experiment 2: DDL Commands

## AIM
To study and implement DDL commands and different types of constraints.

## THEORY

### 1. CREATE
Used to create a new relation (table).

**Syntax:**
```sql
CREATE TABLE (
  field_1 data_type(size),
  field_2 data_type(size),
  ...
);
```
### 2. ALTER
Used to add, modify, drop, or rename fields in an existing relation.
(a) ADD
```sql
ALTER TABLE std ADD (Address CHAR(10));
```
(b) MODIFY
```sql
ALTER TABLE relation_name MODIFY (field_1 new_data_type(size));
```
(c) DROP
```sql
ALTER TABLE relation_name DROP COLUMN field_name;
```
(d) RENAME
```sql
ALTER TABLE relation_name RENAME COLUMN old_field_name TO new_field_name;
```
### 3. DROP TABLE
Used to permanently delete the structure and data of a table.
```sql
DROP TABLE relation_name;
```
### 4. RENAME
Used to rename an existing database object.
```sql
RENAME TABLE old_relation_name TO new_relation_name;
```
### CONSTRAINTS
Constraints are used to specify rules for the data in a table. If there is any violation between the constraint and the data action, the action is aborted by the constraint. It can be specified when the table is created (using CREATE TABLE) or after it is created (using ALTER TABLE).
### 1. NOT NULL
When a column is defined as NOT NULL, it becomes mandatory to enter a value in that column.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) NOT NULL
);
```
### 2. UNIQUE
Ensures that values in a column are unique.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) UNIQUE
);
```
### 3. CHECK
Specifies a condition that each row must satisfy.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) CHECK (logical_expression)
);
```
### 4. PRIMARY KEY
Used to uniquely identify each record in a table.
Properties:
Must contain unique values.
Cannot be null.
Should contain minimal fields.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) PRIMARY KEY
);
```
### 5. FOREIGN KEY
Used to reference the primary key of another table.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size),
  FOREIGN KEY (column_name) REFERENCES other_table(column)
);
```
### 6. DEFAULT
Used to insert a default value into a column if no value is specified.

Syntax:
```sql
CREATE TABLE Table_Name (
  col_name1 data_type,
  col_name2 data_type,
  col_name3 data_type DEFAULT 'default_value'
);
```

**Question 1**
--
-- Create a table named Orders with the following constraints:
OrderID as INTEGER should be the primary key.
OrderDate as DATE should be not NULL.
CustomerID as INTEGER should be a foreign key referencing Customers(CustomerID).

```sql
-- CREATE TABLE Orders(
OrderID INTEGER PRIMARY KEY,
OrderDate DATE NOT NULL,
CustomerID INTEGER ,
FOREIGN KEY (CustomerID) REFERENCES Customers(CustomerID)
);
```

**Output:**

<img width="882" height="357" alt="image" src="https://github.com/user-attachments/assets/08aace39-27e4-4459-aa6c-3608d5ee63f1" />

**Question 2**
---
-- Create a table named Employees with the following constraints:

EmployeeID should be the primary key.
FirstName and LastName should be NOT NULL.
Email should be unique.
Salary should be greater than 0.
DepartmentID should be a foreign key referencing the Departments table.

```sql
-- CREATE TABLE Employees(
EmployeeID INTEGER PRIMARY KEY,
FirstName TEXT NOT NULL,
LastName TEXT NOT NULL,
Email TEXT UNIQUE,
Salary CHECK (Salary > 0),
DepartmentID INTEGER,
FOREIGN KEY (DepartmentID) REFERENCES Departments(DepartmentID)
);
```

**Output:**

<img width="873" height="502" alt="image" src="https://github.com/user-attachments/assets/116e2d39-4393-4d32-ac1a-5b1aaaee037e" />


**Question 3**
---
-- Insert all employees from Former_employees into Employee

Table attributes are EmployeeID, Name, Department, Salary

```sql
-- INSERT INTO Employee(EmployeeID,Name,Department,Salary)
SELECT EmployeeID,Name,Department,Salary from Former_employees;
```

**Output:**

<img width="861" height="372" alt="image" src="https://github.com/user-attachments/assets/f43d3b50-73d7-43cb-a694-d68e5ce96ce6" />


**Question 4**
---
-- Create a new table named contacts with the following specifications:
contact_id as INTEGER and primary key.
first_name as TEXT and not NULL.
last_name as TEXT and not NULL.
email as TEXT.
phone as TEXT and not NULL with a check constraint to ensure the length of phone is at least 10 characters.

```sql
-- CREATE TABLE contacts(
contact_id INTEGER PRIMARY KEY,
first_name TEXT NOT NULL,
last_name TEXT NOT NULL,
email TEXT,
phone TEXT NOT NULL CHECK (LENGTH(phone) >= 10)

);
```

**Output:**

<img width="880" height="416" alt="image" src="https://github.com/user-attachments/assets/2e3326d6-f11d-4bac-82b0-2e3c24a5fd3d" />

**Question 5**
---
-- Create a table named Attendance with the following constraints:
AttendanceID as INTEGER should be the primary key.
EmployeeID as INTEGER should be a foreign key referencing Employees(EmployeeID).
AttendanceDate as DATE.
Status as TEXT should be one of 'Present', 'Absent', 'Leave'.
For example:

```sql
-- CREATE TABLE Attendance(
AttendanceID INTEGER PRIMARY KEY,
EmployeeID INTEGER,
AttendanceDate DATE,
Status TEXT CHECK (Status IN ('Present','Absent','Leave')),
FOREIGN KEY (EmployeeID) REFERENCES Employees(EmployeeID)
);
```

**Output:**

<img width="865" height="361" alt="image" src="https://github.com/user-attachments/assets/dc6e8cf8-4ce5-40e9-82cd-95ed42835f57" />


**Question 6**
---
-- Write an SQL query to add two new columns, first_name and last_name, to the table employee. Both columns should have a data type of varchar(50).

```sql
-- ALTER TABLE employee ADD first_name varchar(50);
ALTER TABLE employee ADD last_name varchar(50);
```

**Output:**

<img width="868" height="390" alt="image" src="https://github.com/user-attachments/assets/d27ba96d-0f79-4df8-986f-ec1243705c09" />


**Question 7**
---
-- Write a SQL query to Add a new ParentsNumber column  as number and Adhar_Number as Number in the Student_details table.

```sql
-- ALTER TABLE Student_details ADD ParentsNumber number;
ALTER TABLE Student_details ADD Adhar_Number number;
```

**Output:**

<img width="873" height="462" alt="image" src="https://github.com/user-attachments/assets/4fc1cb16-9d49-490f-8fd6-ccb119c40d44" />


**Question 8**
---
-- Insert all products from Discontinued_products into Products.

Table attributes are ProductID, ProductName, Price, Stock

```sql
-- INSERT INTO Products(ProductID, ProductName, Price,Stock)
SELECT ProductID,ProductName,Price,Stock from Discontinued_products
```

**Output:**

<img width="877" height="407" alt="image" src="https://github.com/user-attachments/assets/a820c186-0ae2-4d6a-92db-4d4ceaf1b300" />


**Question 9**
---
-- Insert the below data into the Employee table, allowing the Department and Salary columns to take their default values.

EmployeeID  Name         Position
----------  -----------  ----------
4           Emily White  Analyst

Note: The Department and Salary columns will use their default values.   

```sql
-- INSERT INTO Employee(EmployeeId,Name,Position) VALUES (4,'Emily White','Analyst')
```

**Output:**

<img width="882" height="432" alt="image" src="https://github.com/user-attachments/assets/fe0730ef-aeea-4c45-ac05-e17810393ecf" />


**Question 10**
---
-- Create a table named Tasks with the following columns:

TaskID as INTEGER
TaskName as TEXT
DueDate as DATE

```sql
-- CREATE TABLE Tasks(
TaskID INTEGER,
TaskName TEXT,
DueDate DATE
);
```

**Output:**


<img width="873" height="455" alt="image" src="https://github.com/user-attachments/assets/834c7a26-85ef-4400-ad48-7d80464e6008" />


## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.
