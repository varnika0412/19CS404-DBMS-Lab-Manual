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
![image](https://github.com/user-attachments/assets/c46e6a5e-5e49-4487-beef-21542c5a200c)


```sql
SELECT * 
FROM CUSTOMERS 
WHERE SALARY > 1500;

```

**Output:**

![image](https://github.com/user-attachments/assets/53e9374c-8124-4174-b76f-7fc256d87942)


**Question 2**
---
![image](https://github.com/user-attachments/assets/5ff22452-bef8-4ae6-9631-7e10ecf3adfb)


```sql
SELECT ord_no, purch_amt, ord_date, customer_id, salesman_id
FROM orders
WHERE salesman_id IN (
    SELECT salesman_id
    FROM orders
    WHERE customer_id = 3007
);

```

**Output:**

![image](https://github.com/user-attachments/assets/26b34baf-4624-404c-a11b-2d4905c71d85)


**Question 3**
---
![image](https://github.com/user-attachments/assets/c737709e-0e66-405b-ad36-6eb02f2aba3d)


```sql
SELECT name, city
FROM customer
WHERE city IN (
    SELECT city
    FROM customer
    WHERE id IN (3, 7)
);

```

**Output:**

![image](https://github.com/user-attachments/assets/c060afeb-38c6-4d02-b13d-d6f309b26ccc)


**Question 4**
---
![image](https://github.com/user-attachments/assets/27216858-206a-4b80-acb8-1af15d7796f5)


```sql
SELECT ord_no, purch_amt, ord_date, customer_id, salesman_id
FROM orders
WHERE salesman_id = (
    SELECT salesman_id
    FROM salesman
    WHERE name = 'Paul Adam'
);

```

**Output:**

![image](https://github.com/user-attachments/assets/82827e55-cb08-4f62-b55f-b33bdbfc5138)


**Question 5**
---
![image](https://github.com/user-attachments/assets/65f77fa0-5417-4199-8ac2-6c8398b97101)


```sql
SELECT * 
FROM CUSTOMERS 
WHERE ADDRESS = 'Delhi';

```

**Output:**

![image](https://github.com/user-attachments/assets/de253260-2bf2-4225-9f16-6afbdf9159cd)

**Question 6**
---
![image](https://github.com/user-attachments/assets/71a74e55-4b0d-45bd-a356-83d96d716735)


```sql
SELECT ord_no, purch_amt, ord_date, customer_id, salesman_id
FROM orders
WHERE salesman_id IN (
    SELECT salesman_id
    FROM salesman
    WHERE city = 'London'
);

```

**Output:**

![image](https://github.com/user-attachments/assets/c0457728-2932-4ba6-807f-55a2939f9193)


**Question 7**
---
![image](https://github.com/user-attachments/assets/ee059c24-f7b9-4305-bcdf-e5d45c4844a0)


```sql
SELECT *
FROM customer
WHERE customer_id = (
    SELECT salesman_id - 2001
    FROM salesman
    WHERE name = 'Mc Lyon'
);

```

**Output:**

![image](https://github.com/user-attachments/assets/99b6204c-7ced-4114-9cc5-892ff9a80db1)


**Question 8**
---
![image](https://github.com/user-attachments/assets/67f5a42b-865a-4122-9aa0-ccf8e8762692)


```sql
SELECT * 
FROM CUSTOMERS 
WHERE SALARY < 2500;

```

**Output:**

![image](https://github.com/user-attachments/assets/1eb0847e-b288-4885-91b0-e2603f15195c)


**Question 9**
---
![image](https://github.com/user-attachments/assets/da27ae06-5429-4dc5-ad20-0da9a8af3149)


```sql
SELECT s.salesman_id, s.name
FROM salesman s
JOIN customer c ON s.salesman_id = c.salesman_id
GROUP BY s.salesman_id, s.name
HAVING COUNT(c.customer_id) > 1;

```

**Output:**

![image](https://github.com/user-attachments/assets/edc3d09f-7db2-4cd2-a7a0-8c0863fb11d4)


**Question 10**
---
![image](https://github.com/user-attachments/assets/be1a0ab1-7e7d-4986-af30-4fd475e92477)


```sql
SELECT * 
FROM CUSTOMERS 
WHERE ADDRESS = 'Delhi' 
AND AGE < 30
ORDER BY ID;

```

**Output:**

![image](https://github.com/user-attachments/assets/f637a9d0-0829-471f-ae25-1a2a14352e82)


## RESULT
Thus, the SQL queries to implement subqueries and views have been executed successfully.
