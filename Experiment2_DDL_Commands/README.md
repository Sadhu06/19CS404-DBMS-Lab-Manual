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

Create a table named ProjectAssignments with the following constraints:
AssignmentID as INTEGER should be the primary key.
EmployeeID as INTEGER should be a foreign key referencing Employees(EmployeeID).
ProjectID as INTEGER should be a foreign key referencing Projects(ProjectID).
AssignmentDate as DATE should be NOT NULL.

```
CREATE TABLE ProjectAssignments (
      AssignmentID INTEGER PRIMARY KEY, 
      EmployeeID INTEGER, 
      ProjectID INTEGER, 
      AssignmentDate DATE NOT NULL, 
      FOREIGN KEY (EmployeeID) REFERENCES Employees(EmployeeID), 
      FOREIGN KEY (ProjectID) REFERENCES Projects(ProjectID)

);
```

**Output:**

<img width="1233" height="368" alt="image" src="https://github.com/user-attachments/assets/a1623c30-9dd1-478f-8a5c-feab3f3c215d" />


**Question 2**

Insert all employees from Former_employees into Employee

Table attributes are EmployeeID, Name, Department, Salary

```
INSERT INTO Employee (EmployeeID, Name, Department, Salary)
SELECT EmployeeID, Name, Department, Salary
FROM Former_employees;
```

**Output:**

<img width="1217" height="356" alt="image" src="https://github.com/user-attachments/assets/17e75ec0-4bd0-4574-b9f9-dd740607f71c" />


**Question 3**

Write a SQL query to modify the Student_details table by adding a new column Email of type VARCHAR(50) and updating the column MARKS to have a default value of 0.

```
ALTER TABLE Student_details 
ADD Column Email VARCHAR(50);

ALTER TABLE Student_details
ADD COLUMN MARKS INTEGER DEFAULT 0;

```

**Output:**

<img width="1231" height="325" alt="image" src="https://github.com/user-attachments/assets/cffc0aec-0cbd-42b0-b3f0-335a43d3f391" />


**Question 4**

Insert a customer with CustomerID 301, Name Michael Jordan, Address 123 Maple St, City Chicago, and ZipCode 60616 into the Customers table.

```
INSERT INTO Customers (CustomerID, Name, Address, City, ZipCode)
VALUES (301, 'Michael Jordan', '123 Maple St', 'Chicago' , 60616);
```

**Output:**

<img width="1197" height="316" alt="image" src="https://github.com/user-attachments/assets/d06126c0-85c2-43d0-9a78-28a0d31b4276" />


**Question 5**

Write an SQL query to add two new columns, department_id and manager_id, to the table employee with datatype of INTEGER. The manager_id column should have a default value of NULL.

```
ALTER TABLE employee
ADD COLUMN department_id INTEGER;

ALTER TABLE employee
ADD COLUMN manager_id INTEGER DEFAULT NULL;
```

**Output:**

<img width="1236" height="392" alt="image" src="https://github.com/user-attachments/assets/488be966-49fb-40f1-94ea-a36a731d0266" />


**Question 6**

Create a table named Reviews with the following columns:

ReviewID as INTEGER
ProductID as INTEGER
Rating as REAL
ReviewText as TEXT

```
CREATE TABLE Reviews (
     ReviewID INTEGER, 
     ProductID INTEGER, 
     Rating REAL, 
     ReviewText TEXT
);
```

**Output:**

<img width="1226" height="497" alt="image" src="https://github.com/user-attachments/assets/d32ca600-e09e-43d9-bf03-21453762deed" />


**Question 7**

Insert the following employees into the Employee table:

EmployeeID  Name        Position    Department  Salary
----------  ----------  ----------  ----------  ----------
2           John Smith  Developer   IT          75000
3           Anna Bell   Designer    Marketing   68000

```
INSERT INTO Employee (EmployeeID, Name, Position, Department, Salary)
VALUES
(2, 'John Smith' , 'Developer', 'IT', 75000),
(3, 'Anna Bell' , 'Designer', 'Marketing', 68000);
```

**Output:**

<img width="1198" height="432" alt="image" src="https://github.com/user-attachments/assets/0a53dcaa-47c9-4d7f-901f-80f1db43f79e" />


**Question 8**

Create a new table named products with the following specifications:
product_id as INTEGER and primary key.
product_name as TEXT and not NULL.
list_price as DECIMAL (10, 2) and not NULL.
discount as DECIMAL (10, 2) with a default value of 0 and not NULL.
A CHECK constraint at the table level to ensure:
list_price is greater than or equal to discount
discount is greater than or equal to 0
list_price is greater than or equal to 0

```
CREATE TABLE products (
      product_id INTEGER PRIMARY KEY, 
      product_name TEXT NOT NULL, 
      list_price DECIMAL(10,2) NOT NULL, 
      discount DECIMAL(10,2) NOT NULL DEFAULT 0, 
      CHECK (
           list_price >= discount
           AND discount >= 0
           AND list_price >= 0
      )
);
```

**Output:**

<img width="1222" height="377" alt="image" src="https://github.com/user-attachments/assets/d03b9816-30d9-4807-9a6d-cbf60d0cef21" />


**Question 9**

Create a table named Orders with the following constraints:
OrderID as INTEGER should be the primary key.
OrderDate as DATE should be not NULL.
CustomerID as INTEGER should be a foreign key referencing Customers(CustomerID).

```
CREATE TABLE Orders (
     OrderID INTEGER PRIMARY KEY, 
     OrderDate DATE NOT NULL, 
     CustomerID INTEGER, 
     FOREIGN KEY (CustomerID) REFERENCES Customers(CustomerID)
);
```

**Output:**

<img width="1217" height="360" alt="image" src="https://github.com/user-attachments/assets/d86d450f-403c-4c09-80e4-b9ccdc4185ef" />


**Question 10**

Create a table named Invoices with the following constraints:

InvoiceID as INTEGER should be the primary key.
InvoiceDate as DATE.
DueDate as DATE should be greater than the InvoiceDate.
Amount as REAL should be greater than 0.

```
CREATE TABLE Invoices (
      InvoiceID INTEGER PRIMARY KEY, 
      InvoiceDate DATE, 
      DueDate DATE, 
      Amount REAL, 
      CHECK (DueDate > InvoiceDate), 
      CHECK (Amount > 0)
);
```

**Output:**

<img width="1235" height="375" alt="image" src="https://github.com/user-attachments/assets/9e793c18-d598-4244-891f-74baf02d1733" />



## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.
