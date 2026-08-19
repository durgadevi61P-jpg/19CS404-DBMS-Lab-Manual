# Experiment 3: DML Commands

## AIM
To study and implement DML (Data Manipulation Language) commands.

## THEORY

### 1. INSERT INTO
Used to add records into a relation.
These are three type of INSERT INTO queries which are as
A)Inserting a single record
**Syntax (Single Row):**
```sql
INSERT INTO table_name (field_1, field_2, ...) VALUES (value_1, value_2, ...);
```
**Syntax (Multiple Rows):**
```sql
INSERT INTO table_name (field_1, field_2, ...) VALUES
(value_1, value_2, ...),
(value_3, value_4, ...);
```
**Syntax (Insert from another table):**
```sql
INSERT INTO table_name SELECT * FROM other_table WHERE condition;
```
### 2. UPDATE
Used to modify records in a relation.
Syntax:
```sql
UPDATE table_name SET column1 = value1, column2 = value2 WHERE condition;
```
### 3. DELETE
Used to delete records from a relation.
**Syntax (All rows):**
```sql
DELETE FROM table_name;
```
**Syntax (Specific condition):**
```sql
DELETE FROM table_name WHERE condition;
```
### 4. SELECT
Used to retrieve records from a table.
**Syntax:**
```sql
SELECT column1, column2 FROM table_name WHERE condition;
```
**Question 1**
--
--product_id INT product_name VARCHAR(100) category VARCHAR(50) cost_price DECIMAL(10,2) sell_price DECIMAL(10,2) reorder_lvl INT quantity INT supplier_id INT

```sql
-- UPDATE products
SET sell_price = cost_price * 135/100
WHERE ((sell_price - cost_price) / sell_price) * 100 < 30;
```

**Output:**

<img width="842" height="598" alt="image" src="https://github.com/user-attachments/assets/f1cdd43f-a7a4-4fc5-8dc0-70c2d1e328de" />

**Question 2**
---
-- Write a SQL statement to Update the address to '58 Lakeview, Magnolia' where supplier ID is 5 in the suppliers table.
Suppliers Table

name type

supplier_id INT supplier_name VARCHAR(100) contact_person VARCHAR(100) phone_number VARCHAR(20) email VARCHAR(100) address VARCHAR(250)

```sql
-- UPDATE suppliers
SET address = '58 Lakeview, Magnolia'
WHERE supplier_id = 5;
```

**Output:**
<img width="831" height="600" alt="image" src="https://github.com/user-attachments/assets/d2506e89-2462-41f2-958f-07e26b6d58d6" />


**Question 3**
---
-- Write a SQL query to reduce the reorder level by 30% where cost price is more than 50 and quantity in stock is less than 100 in the products table.

Products Table

name type

product_id INT PRIMARY KEY
product_name VARCHAR(10) category VARCHAR(50) cost_price DECIMAL(10) sell_price DECIMAL(10) reorder_lvl INT
quantity INT
supplier_id INT

```sql
-- UPDATE products
SET reorder_lvl = reorder_lvl * 70 / 100
WHERE cost_price > 50
  AND quantity < 100;
```

**Output:**

<img width="808" height="597" alt="image" src="https://github.com/user-attachments/assets/5a27230b-e799-4917-bb9f-b1abfc70e3ea" />


**Question 4**
---
-- Update the reorder level to 40 pieces for all products belonging to the 'Grocery' category in the products table.

PRODUCTS TABLE

name type

product_id INT product_name VARCHAR(100) category VARCHAR(50) cost_price DECIMAL(10,2) sell_price DECIMAL(10,2) reorder_lvl INT quantity INT supplier_id INT

```sql
-- UPDATE products
SET reorder_lvl = 40
WHERE category = 'Grocery';
```

**Output:**

<img width="823" height="598" alt="image" src="https://github.com/user-attachments/assets/125f305d-a0f3-488a-ab62-e34cb05335b6" />


**Question 5**
---
-- Write a SQL statement to Increase the salary by 500 and email as 'updated' for employees with job ID 'SA_REP' and commission percentage greater than 0.15

Employees table

employee_id first_name last_name email phone_number hire_date job_id salary commission_pct manager_id department_id

```sql
-- UPDATE employees
SET salary = salary + 500,
    email = 'updated'
WHERE job_id = 'SA_REP'
  AND commission_pct > 0.15;
```

**Output:**

<img width="838" height="597" alt="image" src="https://github.com/user-attachments/assets/c33fbd4f-4b78-4770-b3ca-ed6722e0927f" />


**Question 6**
---
-- Create a table named Products with the following constraints:

ProductID should be the primary key.
ProductName should be NOT NULL.
Price is of real datatype and should be greater than 0.
Stock is of integer datatype and should be greater than or equal to 0.

```sql
-- CREATE TABLE Products(
ProductID PRIMARY KEY,
ProductName NOT NULL,
Price REAL CHECK (Price > 0),
Stock INTEGER CHECK (Stock >= 0)
);
```

**Output:**

<img width="863" height="371" alt="image" src="https://github.com/user-attachments/assets/d46269c5-87ba-4b9a-b650-af4d6f6fe798" />


**Question 7**
---
-- Insert the below data into the Customers table, allowing the City and ZipCode columns to take their default values.

CustomerID  Name          Address
----------  ------------  ----------
304         Peter Parker  Spider St      

Note: The City and ZipCode columns will use their default values

```sql
-- INSERT INTO Customers(CustomerID,Name,Address) VALUES (304,"Peter Pa
```

**Output:**
<img width="871" height="395" alt="image" src="https://github.com/user-attachments/assets/1927ed41-67ef-47d6-93d4-f44597afe572" />


**Question 8**
---
-- Write a SQL query to Add a new column Country as text in the Student_details table.

Sample table: Student_details

 cid              name             type   notnull     dflt_value  pk
---------------  ---------------  -----  ----------  ----------  ----------
0                RollNo           int    0                       1
1                Name             VARCH  1                       0
2                Gender           TEXT   1                       0
3                Subject          VARCH  0                       0
4                MARKS            INT (  0                       0

```sql
-- ALTER TABLE Student_details ADD Country TEXT;
```

**Output:**

<img width="1247" height="443" alt="image" src="https://github.com/user-attachments/assets/4bf89e6d-c143-485d-a5db-45af4e8d139a" />


**Question 9**
---
-- Create a table named ProjectAssignments with the following constraints:
AssignmentID as INTEGER should be the primary key.
EmployeeID as INTEGER should be a foreign key referencing Employees(EmployeeID).
ProjectID as INTEGER should be a foreign key referencing Projects(ProjectID).
AssignmentDate as DATE should be NOT NULL.

```sql
-- CREATE TABLE ProjectAssignments(
AssignmentID INTEGER PRIMARY KEY,
EmployeeID INTEGER ,
ProjectID INTEGER,
AssignmentDate DATE NOT NULL,
FOREIGN KEY (EmployeeID) REFERENCES Employees(EmployeeID),
FOREIGN KEY (ProjectID) REFERENCES Projects(ProjectID)
);
```

**Output:**

<img width="1212" height="367" alt="image" src="https://github.com/user-attachments/assets/1e0b1b93-0f4d-484f-ad26-d1d816214caa" />



**Question 10**
---
-- Insert the following products into the Products table:

Name        Category     Price       Stock
----------  -----------  ----------  ----------
Smartphone  Electronics  800         150
Headphones  Accessories  200         300

```sql
-- INSERT INTO Products(Name,Category,Price,Stock) VALUES("Smartphone","Electronics",800,150),("Headphones","Accessories",200,300);
```

**Output:**

<img width="880" height="450" alt="image" src="https://github.com/user-attachments/assets/b82bf907-93bc-46db-904e-c96467c9f421" />


## RESULT
Thus, the SQL queries to implement DML commands have been executed successfully.
