# Experiment 6: Joins

## AIM
To study and implement different types of joins.

## THEORY

SQL Joins are used to combine records from two or more tables based on a related column.

### 1. INNER JOIN
Returns records with matching values in both tables.

**Syntax:**
```sql
SELECT columns
FROM table1
INNER JOIN table2
ON table1.column = table2.column;
```

### 2. LEFT JOIN
Returns all records from the left table, and matched records from the right.

**Syntax:**

```sql
SELECT columns
FROM table1
LEFT JOIN table2
ON table1.column = table2.column;
```
### 3. RIGHT JOIN
Returns all records from the right table, and matched records from the left.

**Syntax:**

```sql
SELECT columns
FROM table1
RIGHT JOIN table2
ON table1.column = table2.column;
```
### 4. FULL OUTER JOIN
Returns all records when there is a match in either left or right table.

**Syntax:**

```sql
SELECT columns
FROM table1
FULL OUTER JOIN table2
ON table1.column = table2.column;
```

**Question 1**

Write an SQL query to select the 'cust_name' column from the 'customer' table (aliased as 'c'), using a LEFT JOIN with the 'orders' table based on the 'customer_id' column.

```
SELECT c.cust_name
FROM customer c
LEFT JOIN orders o
ON c.customer_id = o.customer_id;
```

**Output:**

<img width="402" height="934" alt="image" src="https://github.com/user-attachments/assets/2fe83240-f465-4325-b761-1ac97bf88cc9" />


**Question 2**

Write the SQL query that achieves the selection of the "name" column from the "salesman" table (aliased as "s"), the "cust_name," "city," "grade," and "salesman_id" columns from the "customer" table (aliased as "c"), with a left join on the "salesman_id" column.

```
SELECT s.name, c.cust_name, c.city, c.grade, c.salesman_id
FROM salesman s
LEFT JOIN customer c
ON s.salesman_id = c.salesman_id;
```

**Output:**

<img width="1242" height="964" alt="image" src="https://github.com/user-attachments/assets/d2ed3295-a51d-45be-af93-ce0d5746c13c" />


**Question 3**

From the following tables write a SQL query to find those orders where the order amount exists between 500 and 2000. Return ord_no, purch_amt, cust_name, city.

```
SELECT o.ord_no, o.purch_amt, c.cust_name, c.city
FROM orders o
JOIN customer c
ON o.customer_id = c.customer_id
WHERE o.purch_amt BETWEEN 500 AND 2000;
```

**Output:**

<img width="1249" height="578" alt="image" src="https://github.com/user-attachments/assets/658ed9b2-d260-436e-9fc6-8175bb9d499c" />


**Question 4**

SQL statement to generate a report with customer name, city, order number, order date, order amount, salesperson name, and commission to determine if any of the existing customers have not placed orders or if they have placed orders through their salesman or by themselves.

```
SELECT c.cust_name, c.city, o.ord_no, o.ord_date,
       o.purch_amt AS "Order Amount",
       s.name, s.commission
FROM customer c
LEFT JOIN orders o
ON c.customer_id = o.customer_id
LEFT JOIN salesman s
ON o.salesman_id = s.salesman_id;
```

**Output:**

<img width="1256" height="948" alt="image" src="https://github.com/user-attachments/assets/a5836800-31f3-4092-b9af-834af2427847" />


**Question 5**

Write the SQL query that accomplishes the selection of all columns from the "patients" table and the first name of doctors from the "doctors" table, with an inner join on the "doctor_id" column.

```
SELECT p.*, d.first_name AS doctor_name
FROM patients p
INNER JOIN doctors d
ON p.doctor_id = d.doctor_id;
```

**Output:**

<img width="1252" height="636" alt="image" src="https://github.com/user-attachments/assets/90c79d0f-7553-4f9e-a752-382289feeb55" />


**Question 6**

From the following tables write a SQL query to locate those salespeople who do not live in the same city where their customers live and have received a commission of more than 12% from the company. Return Customer Name, customer city, Salesman, salesman city, commission. 

```
SELECT c.cust_name AS "Customer Name",
       c.city AS "city",
       s.name AS "Salesman",
       s.city AS "city",
       s.commission
FROM customer c
INNER JOIN salesman s
ON c.salesman_id = s.salesman_id
WHERE c.city <> s.city
AND s.commission > 0.12;
```

**Output:**

<img width="1255" height="717" alt="image" src="https://github.com/user-attachments/assets/8001747a-4699-40a8-b8cc-80d2bffaef5b" />


**Question 7**

Write a SQL statement to make a report with customer name, city, order number, order date, and order amount in ascending order according to the order date to determine whether any of the existing customers have placed an order or not.

```
SELECT c.cust_name, c.city, o.ord_no, o.ord_date, o.purch_amt AS 'Order Amount'
FROM customer c
LEFT JOIN orders o
ON c.customer_id = o.customer_id
ORDER BY o.ord_date ASC;
```

**Output:**

<img width="1224" height="943" alt="image" src="https://github.com/user-attachments/assets/1aeb049d-9418-4e64-bcc6-b737db7e81ae" />


**Question 8**

Write the SQL query that achieves the selection of admission dates from the "patients" table and surgery dates from the "surgeries" table, with an inner join on the "patient_id" column.

```
SELECT p.admission_date, s.surgery_date
FROM patients p
INNER JOIN surgeries s
ON p.patient_id = s.patient_id;
```

**Output:**

<img width="793" height="629" alt="image" src="https://github.com/user-attachments/assets/cea4809e-78f2-45c6-bd02-d85b0437538b" />


**Question 9**

From the following tables write a SQL query to find those customers with a grade less than 300. Return cust_name, customer city, grade, Salesman, salesmancity. The result should be ordered by ascending customer_id. 

```
SELECT c.cust_name,
       c.city,
       c.grade,
       s.name AS Salesman,
       s.city AS city
FROM customer c
INNER JOIN salesman s
ON c.salesman_id = s.salesman_id
WHERE c.grade < 300
ORDER BY c.customer_id ASC;
```

**Output:**

<img width="1244" height="855" alt="image" src="https://github.com/user-attachments/assets/941be061-727b-478b-883a-369576656335" />


**Question 10**

Write the SQL query that achieves the selection of all columns from the "patients" table (aliased as "p"), with an inner join on the "patient_id" column and a condition filtering for appointments with an appointment date between '2024-01-01' and '2024-01-31'.

```
SELECT p.*
FROM patients p
INNER JOIN appointments a
ON p.patient_id = a.patient_id
WHERE a.appointment_date BETWEEN '2024-01-01' AND '2024-01-31';
```

**Output:**

<img width="1275" height="492" alt="image" src="https://github.com/user-attachments/assets/46e5d454-4310-4372-b783-9b636164fd77" />



## RESULT
Thus, the SQL queries to implement different types of joins have been executed successfully.
