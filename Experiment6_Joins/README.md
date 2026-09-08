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

<img width="413" height="948" alt="image" src="https://github.com/user-attachments/assets/ee5b0001-82bb-40ee-bb14-8a182ca7ca86" />


**Question 2**

Write the SQL query that achieves the selection of the "name" column from the "salesman" table (aliased as "s"), the "cust_name," "city," "grade," and "salesman_id" columns from the "customer" table (aliased as "c"), with a left join on the "salesman_id" column.

```
SELECT s.name, c.cust_name, c.city, c.grade, c.salesman_id
FROM salesman s
LEFT JOIN customer c
ON s.salesman_id = c.salesman_id;
```

**Output:**

<img width="1232" height="965" alt="image" src="https://github.com/user-attachments/assets/6a906379-5f8a-4272-b3ed-ca6253bf086c" />


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

<img width="1244" height="575" alt="image" src="https://github.com/user-attachments/assets/6317bf0b-41b1-4e9e-b741-2d5a4e8b2cd9" />


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

<img width="1264" height="965" alt="image" src="https://github.com/user-attachments/assets/60914fb1-5033-491d-9ecd-37004f77a117" />


**Question 5**

Write the SQL query that accomplishes the selection of all columns from the "patients" table and the first name of doctors from the "doctors" table, with an inner join on the "doctor_id" column.

```
SELECT p.*, d.first_name AS doctor_name
FROM patients p
INNER JOIN doctors d
ON p.doctor_id = d.doctor_id;
```

**Output:**

<img width="1274" height="638" alt="image" src="https://github.com/user-attachments/assets/613a1571-dc66-4123-81c5-a812caaac7f8" />


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

<img width="1274" height="714" alt="image" src="https://github.com/user-attachments/assets/2a74c875-d243-4d1c-8f3e-c6794f912731" />


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

<img width="1282" height="945" alt="image" src="https://github.com/user-attachments/assets/b4dc1f47-0e39-435d-b0d4-cedb4bf4e3c5" />


**Question 8**

Write the SQL query that achieves the selection of admission dates from the "patients" table and surgery dates from the "surgeries" table, with an inner join on the "patient_id" column.

```
SELECT p.admission_date, s.surgery_date
FROM patients p
INNER JOIN surgeries s
ON p.patient_id = s.patient_id;
```

**Output:**

<img width="874" height="608" alt="image" src="https://github.com/user-attachments/assets/c10de870-6c0a-42e0-83a5-9486bcf14094" />


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

<img width="1258" height="849" alt="image" src="https://github.com/user-attachments/assets/8321eca4-845a-4c70-bc17-30703061870c" />


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

<img width="1261" height="481" alt="image" src="https://github.com/user-attachments/assets/7c62ddab-6ed4-482e-923f-9cf976d48269" />



## RESULT
Thus, the SQL queries to implement different types of joins have been executed successfully.
