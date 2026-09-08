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

Write a query to display all the customers whose ID is the difference between the salesperson ID of Mc Lyon and 2001.

```
SELECT *
FROM customer
WHERE customer_id IN (
    SELECT salesman_id - 2001
    FROM salesman
    WHERE name = 'Mc Lyon'
);
```

**Output:**

<img width="1275" height="397" alt="image" src="https://github.com/user-attachments/assets/568629fc-fbf3-491b-b1fe-162ede275591" />


**Question 2**

From the following tables write a SQL query to find salespeople who had more than one customer. Return salesman_id and name.

```
SELECT s.salesman_id, s.name
FROM salesman s
JOIN customer c
ON s.salesman_id = c.salesman_id
GROUP BY s.salesman_id, s.name
HAVING COUNT(c.customer_id) > 1;
```

**Output:**

<img width="595" height="539" alt="image" src="https://github.com/user-attachments/assets/8e533ab7-5822-4495-8485-6f3e253a33c6" />


**Question 3**

Write a SQL query to retrieve all columns from the CUSTOMERS table for customers whose salary is EQUAL TO $1500.

```
SELECT *
FROM CUSTOMERS
WHERE SALARY = 1500;
```

**Output:**

<img width="1241" height="411" alt="image" src="https://github.com/user-attachments/assets/8b101a37-9535-4746-abf3-44f37a315168" />


**Question 4**

Write a SQL query to retrieve all columns from the CUSTOMERS table for customers whose salary is greater than $1500.

```
SELECT *
FROM CUSTOMERS
WHERE SALARY > 1500;
```

**Output:**

<img width="1257" height="679" alt="image" src="https://github.com/user-attachments/assets/06af3e93-efb1-4391-bafb-09bf3bd3a70f" />


**Question 5**

Write a SQL query that retrieves the all the columns from the Table Grades, where the grade is equal to the minimum grade achieved in each subject.

```
SELECT *
FROM GRADES g
WHERE grade = (
    SELECT MIN(grade)
    FROM GRADES
    WHERE subject = g.subject
);
```

**Output:**

<img width="1273" height="520" alt="image" src="https://github.com/user-attachments/assets/c92c98d4-f537-46a0-b03b-45b3d53e19ed" />


**Question 6**

From the following tables, write a SQL query to find all the orders generated in New York city. Return ord_no, purch_amt, ord_date, customer_id and salesman_id.

```
SELECT o.ord_no, o.purch_amt, o.ord_date,
       o.customer_id, o.salesman_id
FROM ORDERS o
JOIN SALESMAN s
ON o.salesman_id = s.salesman_id
WHERE s.city = 'New York';
```

**Output:**

<img width="1221" height="540" alt="image" src="https://github.com/user-attachments/assets/5305b113-e00d-4128-b48a-fbd9425eaceb" />


**Question 7**

Write a SQL query to Retrieve the medications with dosages equal to the lowest dosage

```
SELECT *
FROM Medications
WHERE dosage = (
    SELECT MIN(dosage)
    FROM Medications
);
```

**Output:**

<img width="890" height="470" alt="image" src="https://github.com/user-attachments/assets/ed24dfb8-4cfb-4442-8cc8-12c58cc749f7" />


**Question 8**

Write a SQL query to retrieve all columns from the CUSTOMERS table for customers whose Address as Delhi

```
SELECT *
FROM CUSTOMERS
WHERE ADDRESS = 'Delhi';
```

**Output:**

<img width="1237" height="401" alt="image" src="https://github.com/user-attachments/assets/91ceca49-b8bf-4367-99d5-39a63e199c04" />


**Question 9**

Write a SQL query that retrieve all the columns from the table "Grades", where the grade is equal to the maximum grade achieved in each subject.

```
SELECT *
FROM GRADES g
WHERE grade = (
    SELECT MAX(grade)
    FROM GRADES
    WHERE subject = g.subject
);
```

**Output:**

<img width="1236" height="510" alt="image" src="https://github.com/user-attachments/assets/beae0b14-faf3-41ab-8f0c-7f61d94f54a1" />


**Question 10**

From the following tables, write a SQL query to determine the commission of the salespeople in Paris. Return commission.

```
SELECT commission 
FROM salesman 
WHERE salesman_id IN (
    SELECT salesman_id 
    FROM customer 
    WHERE city = 'Paris'
);
```

**Output:**

<img width="309" height="397" alt="image" src="https://github.com/user-attachments/assets/d734485c-ea47-4dd0-a1b3-08e3fcf6ea84" />



## RESULT
Thus, the SQL queries to implement subqueries and views have been executed successfully.
