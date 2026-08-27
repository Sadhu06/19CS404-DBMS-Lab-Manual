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

Write a SQL statement to Increase quantity of all products by 10% to adjust for surplus stock counted


```
UPDATE Products
SET quantity = quantity * 1.10;

```

**Output:**

<img width="1232" height="715" alt="image" src="https://github.com/user-attachments/assets/3b72c70b-13d4-4842-bbf7-b290344ce3d1" />


**Question 2**

Update the reorder level to 40 pieces for all products belonging to the 'Grocery' category in the products table.


```
UPDATE Products
SET reorder_lvl = 40
WHERE category = 'Grocery';
```

**Output:**

<img width="1232" height="493" alt="image" src="https://github.com/user-attachments/assets/7d160fe5-3365-4300-a9a3-369d3a1b6d19" />


**Question 3**

Write a SQL statement to Update the reorder level to 20 where the quantity in stock is less than 10 and product category is 'Snacks' in the products table.


```
UPDATE products
SET reorder_lvl = 20
WHERE quantity < 10
    AND category = 'Snacks';
```

**Output:**

<img width="1240" height="665" alt="image" src="https://github.com/user-attachments/assets/c11d15d8-3889-449e-b78d-d5c3886dfb68" />


**Question 4**

Write a SQL query to reduce the reorder level by 30% where cost price is more than 50 and quantity in stock is less than 100 in the products table.


```
UPDATE products
SET reorder_lvl = reorder_lvl * 0.70
WHERE cost_price > 50
    AND quantity < 100;
```

**Output:**

<img width="1243" height="552" alt="image" src="https://github.com/user-attachments/assets/851cbb1f-a39a-4528-b184-bbc7c9207fb0" />


**Question 5**

Write a SQL statement to change the first_name column of employees table with 'John' for those employees whose department_id is 80 and gets a commission_pct below 0.35.


```
UPDATE employees
SET first_name = 'John'
WHERE department_id = 80
    AND commission_pct < 0.35;
```

**Output:**

<img width="1245" height="616" alt="image" src="https://github.com/user-attachments/assets/bd0075e1-25e7-40cf-ad41-53119c993523" />


**Question 6**

Write a SQL query to Delete customers from 'customer' table where 'OPENING_AMT' is between 4000 and 6000.

Sample table: Customer

```
DELETE FROM customer
WHERE OPENING_AMT BETWEEN 4000 AND 6000;

```

**Output:**

<img width="1237" height="722" alt="image" src="https://github.com/user-attachments/assets/7716bc28-75b5-449a-9f6b-af650161e91f" />


**Question 7**

Write a SQL query to Delete a Specific Surgery which was made on 28th Feb 2024.

```
DELETE FROM surgeries
WHERE surgery_date = '2024-02-28';
```

**Output:**

<img width="1212" height="472" alt="image" src="https://github.com/user-attachments/assets/ce312a4e-47f1-4956-ad9c-e36662b26685" />


**Question 8**

Write a SQL query to Delete All Doctors with a NULL Last Name


```
DELETE FROM doctors
WHERE last_name IS NULL;
```

**Output:**

<img width="1238" height="802" alt="image" src="https://github.com/user-attachments/assets/42fc77d5-4f8b-4e50-b17f-7c2a65b77ade" />


**Question 9**

Write a SQL query to Delete customers from 'customer' table where 'WORKING_AREA' is 'New York'.

Sample table: Customer

```
DELETE FROM customer
WHERE WORKING_AREA = 'New York';
```

**Output:**

<img width="1241" height="891" alt="image" src="https://github.com/user-attachments/assets/5b8bc615-1257-4a4c-b0d0-3ab0ae329eb9" />


**Question 10**

Write a query to fetch details of employees with the address as “DELHI(DEL)” from EmployeeInfo table.

```
SELECT * FROM EmployeeInfo WHERE Address = 'Delhi(DEL)';
```

**Output:**

<img width="1225" height="357" alt="image" src="https://github.com/user-attachments/assets/446315af-c687-4973-bd35-56785ea59464" />


## RESULT
Thus, the SQL queries to implement DML commands have been executed successfully.
