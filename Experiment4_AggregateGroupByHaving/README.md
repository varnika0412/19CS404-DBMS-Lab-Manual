# Experiment 4: Aggregate Functions, Group By and Having Clause

## AIM
To study and implement aggregate functions, GROUP BY, and HAVING clause with suitable examples.

## THEORY

### Aggregate Functions
These perform calculations on a set of values and return a single value.

- *MIN()* – Smallest value  
- *MAX()* – Largest value  
- *COUNT()* – Number of rows  
- *SUM()* – Total of values  
- *AVG()* – Average of values

*Syntax:*
sql
SELECT AGG_FUNC(column_name) FROM table_name WHERE condition;

### GROUP BY
Groups records with the same values in specified columns.
*Syntax:*
sql
SELECT column_name, AGG_FUNC(column_name)
FROM table_name
GROUP BY column_name;

### HAVING
Filters the grouped records based on aggregate conditions.
*Syntax:*
sql
SELECT column_name, AGG_FUNC(column_name)
FROM table_name
GROUP BY column_name
HAVING condition;


*Question 1*
--
![image](https://github.com/user-attachments/assets/b3fb1aa8-d1e7-4413-9612-0bf0f2ef0d66)


sql
```
SELECT InsuranceCompany,COUNT(*) AS TotalPatients 
FROM Insurance 
GROUP BY InsuranceCompany;
```

*Output:*

![image](https://github.com/user-attachments/assets/59d35cdd-6414-4d95-8875-4b14bab63713)


*Question 2*
---
![image](https://github.com/user-attachments/assets/e75bfb67-2d4c-46a8-83af-95547b6c5e48)


sql
```
SELECT PatientID,COUNT(*) AS TotalRecords
FROM MedicalRecords
GROUP BY PatientID;
```

*Output:*

![image](https://github.com/user-attachments/assets/4089742d-18cb-48d8-bd35-daf452bf74ff)


*Question 3*
---
![image](https://github.com/user-attachments/assets/3ab69dea-8d40-4533-b9a3-916826ae4a5e)


sql
```
SELECT Medication,COUNT(*) AS TotalPrescriptions
FROM Prescriptions
GROUP BY Medication;
```

*Output:*

![image](https://github.com/user-attachments/assets/2123be36-65dd-4217-a4ee-08719a534fad)


*Question 4*
---
![image](https://github.com/user-attachments/assets/0d71496a-7b81-40e6-9bcb-942d0ae1e91b)


sql
```
SELECT AVG(LENGTH(email)) AS avg_email_length 
FROM customer;
```

*Output:*

![image](https://github.com/user-attachments/assets/2372ff22-0182-4723-b125-6e44aaa0566c)


*Question 5*
---
![image](https://github.com/user-attachments/assets/913d7fcd-24c7-4c92-aa16-f1af2a52e2ef)


sql
```
SELECT SUM(purch_amt) AS TOTAL
FROM orders;
```

*Output:*

![image](https://github.com/user-attachments/assets/f30ada70-8038-4977-b936-a4d0812ecda4)


*Question 6*
---
![image](https://github.com/user-attachments/assets/c8060d77-8198-45b0-bb23-a9270c7d1a2b)


sql
```
SELECT MAX(price)-MIN(price) AS price_diff
FROM fruits;

```
*Output:*

![image](https://github.com/user-attachments/assets/aca7c661-fb23-4d0a-a799-5720e5844a3c)


*Question 7*
---
![image](https://github.com/user-attachments/assets/4fdb7c36-2f11-4ec6-9c1d-65c8e5971b8e)


sql
```
SELECT AVG(income) AS avg_income
FROM employee
WHERE name LIKE 'A%';

```
*Output:*

![image](https://github.com/user-attachments/assets/346b8ed8-58d3-45ed-99cc-688d8505145a)


*Question 8*
---
![image](https://github.com/user-attachments/assets/d834451a-6b56-4edc-9015-fc36933f450e)


sql
```
SELECT (age/5)*5 AS age_group,MAX(salary)
FROM customer1
GROUP BY (age/5)*5
HAVING MAX(salary)>8000;
```

*Output:*

![image](https://github.com/user-attachments/assets/9fd9b191-400f-4218-b3d3-7c555e3a8e84)


*Question 9*
---
![image](https://github.com/user-attachments/assets/e185bbe1-ec90-4c34-b8d7-8e8a4ceabe20)


sql
```
SELECT occupation,MIN(workhour) 
FROM employee1
GROUP BY occupation HAVING MIN(workhour)>8;
```

*Output:*

![image](https://github.com/user-attachments/assets/d1be45fb-587f-442c-b200-bce0eceae56b)


*Question 10*
---
![image](https://github.com/user-attachments/assets/62937514-85ad-40ea-8ce3-bbd1450bdf3b)


sql
```
SELECT city,SUM(Income) AS Income 
FROM employee 
GROUP BY city
HAVING SUM(Income)>200000;
```

*Output:*

![image](https://github.com/user-attachments/assets/467bdf7f-0407-47d4-8c64-8ed2287f6288)



## RESULT
Thus, the SQL queries to implement aggregate functions, GROUP BY, and HAVING clause have been executed successfully.
