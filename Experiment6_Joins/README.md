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
--
![image](https://github.com/user-attachments/assets/94e38e85-6384-422e-907c-556ac53853c3)


```sql
SELECT 
    c.cust_name AS "Customer Name",
    c.city AS "city",
    s.name AS "Salesman",
    s.city AS "city",
    s.commission
FROM 
    customer c
JOIN 
    salesman s
ON 
    c.salesman_id = s.salesman_id
WHERE 
    c.city <> s.city 
    AND s.commission > 0.12;

```

**Output:**

![image](https://github.com/user-attachments/assets/7f9ed3a0-6892-47e0-b8cf-04fcfbb82c8b)


**Question 2**
---
![image](https://github.com/user-attachments/assets/145cba30-cb85-4396-80f2-7932b11a112c)


```sql
SELECT 
    p.*, 
    d.specialization AS doctor_specialization
FROM 
    patients p
INNER JOIN 
    doctors d
ON 
    p.doctor_id = d.doctor_id;

```

**Output:**

![image](https://github.com/user-attachments/assets/aaf69763-4e12-431a-b3d4-e14ee04d5954)


**Question 3**
---
![image](https://github.com/user-attachments/assets/1e34e160-2a67-4f04-afb0-f3282bcb57d4)


```sql
SELECT 
    o.ord_no, 
    o.purch_amt, 
    c.cust_name, 
    c.city
FROM 
    orders o
INNER JOIN 
    customer c
ON 
    o.customer_id = c.customer_id
WHERE 
    o.purch_amt BETWEEN 500 AND 2000;

```

**Output:**

![image](https://github.com/user-attachments/assets/6d3f2678-32d5-47d2-a789-b0d9b2b19efc)


**Question 4**
---
![image](https://github.com/user-attachments/assets/85a2a453-a10f-4e58-9563-a43054bc4570)


```sql
SELECT 
    c.cust_name, 
    c.city AS "city", 
    c.grade, 
    s.name AS "Salesman", 
    s.city AS "city"
FROM 
    customer c
INNER JOIN 
    salesman s
ON 
    c.salesman_id = s.salesman_id
WHERE 
    c.grade < 300
ORDER BY 
    c.customer_id ASC;

```

**Output:**

![image](https://github.com/user-attachments/assets/708673aa-b8d6-4330-8103-4d0e0ec0868f)


**Question 5**
---
![image](https://github.com/user-attachments/assets/28662afc-6061-4e7f-bd80-5533d58a2156)


```sql
SELECT 
    p.date_of_birth, 
    a.*
FROM 
    patients p
INNER JOIN 
    appointments a
ON 
    p.patient_id = a.patient_id
WHERE 
    p.first_name = 'Alice';

```

**Output:**

![image](https://github.com/user-attachments/assets/6f93af7c-f2c0-4242-8f78-b44d45a6f87c)


**Question 6**
---
![image](https://github.com/user-attachments/assets/9fee672a-0e71-4088-9cad-de1764a7e9f0)


```sql
SELECT 
    c.cust_name AS "Customer Name", 
    c.city AS "city", 
    s.name AS "Salesman", 
    s.commission
FROM 
    customer c
INNER JOIN 
    salesman s
ON 
    c.salesman_id = s.salesman_id
WHERE 
    s.commission > 0.12;

```

**Output:**

![image](https://github.com/user-attachments/assets/4018d389-c25c-44a0-92b8-a9032f8257be)


**Question 7**
---
![image](https://github.com/user-attachments/assets/0dfc9d87-5f4d-4e25-b1a0-ed50c992c851)


```sql
SELECT 
    p.*
FROM 
    patients p
INNER JOIN 
    appointments a
ON 
    p.patient_id = a.patient_id
WHERE 
    a.appointment_date BETWEEN '2024-01-01' AND '2024-01-31';

```

**Output:**

![image](https://github.com/user-attachments/assets/ed4113f1-74b3-48fb-9621-b70d504f75c2)


**Question 8**
---
![image](https://github.com/user-attachments/assets/dd40ec02-9d90-4de7-9cd3-d2ab75cbb1ad)


```sql
SELECT 
    c.cust_name, 
    s.commission
FROM 
    customer c
LEFT JOIN 
    salesman s
ON 
    c.salesman_id = s.salesman_id;

```

**Output:**

![image](https://github.com/user-attachments/assets/bd946187-cfeb-4157-8369-0e3f4ae54e14)


**Question 9**
---
![image](https://github.com/user-attachments/assets/4de97196-984b-47ea-9ce6-68796fbd91f0)


```sql
SELECT 
    o.ord_no, 
    o.ord_date, 
    o.purch_amt, 
    c.cust_name AS "Customer Name", 
    c.grade, 
    s.name AS "Salesman", 
    s.commission
FROM 
    orders o
JOIN 
    customer c ON o.customer_id = c.customer_id
JOIN 
    salesman s ON o.salesman_id = s.salesman_id;

```

**Output:**

![image](https://github.com/user-attachments/assets/e8474ab5-83ef-4466-9de2-38a2b52e5676)


**Question 10**
---
![image](https://github.com/user-attachments/assets/43b25eb1-c61f-4c5a-b2f4-33dd3c957a37)

```sql
SELECT 
    c.*
FROM 
    customer c
LEFT JOIN 
    salesman s ON c.salesman_id = s.salesman_id
WHERE 
    s.name = 'Mc Lyon';

```

**Output:**

![image](https://github.com/user-attachments/assets/c94c4489-693f-4371-b8ae-4955a6f51a1e)


## RESULT
Thus, the SQL queries to implement different types of joins have been executed successfully.
