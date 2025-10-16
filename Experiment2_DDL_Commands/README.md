# Experiment 2: DDL Commands

## AIM
To study and implement DDL commands and different types of constraints.

## THEORY

### 1. CREATE
Used to create a new relation (table).

*Syntax:*
sql
CREATE TABLE (
  field_1 data_type(size),
  field_2 data_type(size),
  ...
);

### 2. ALTER
Used to add, modify, drop, or rename fields in an existing relation.
(a) ADD
sql
ALTER TABLE std ADD (Address CHAR(10));

(b) MODIFY
sql
ALTER TABLE relation_name MODIFY (field_1 new_data_type(size));

(c) DROP
sql
ALTER TABLE relation_name DROP COLUMN field_name;

(d) RENAME
sql
ALTER TABLE relation_name RENAME COLUMN old_field_name TO new_field_name;

### 3. DROP TABLE
Used to permanently delete the structure and data of a table.
sql
DROP TABLE relation_name;

### 4. RENAME
Used to rename an existing database object.
sql
RENAME TABLE old_relation_name TO new_relation_name;

### CONSTRAINTS
Constraints are used to specify rules for the data in a table. If there is any violation between the constraint and the data action, the action is aborted by the constraint. It can be specified when the table is created (using CREATE TABLE) or after it is created (using ALTER TABLE).
### 1. NOT NULL
When a column is defined as NOT NULL, it becomes mandatory to enter a value in that column.
Syntax:
sql
CREATE TABLE Table_Name (
  column_name data_type(size) NOT NULL
);

### 2. UNIQUE
Ensures that values in a column are unique.
Syntax:
sql
CREATE TABLE Table_Name (
  column_name data_type(size) UNIQUE
);

### 3. CHECK
Specifies a condition that each row must satisfy.
Syntax:
sql
CREATE TABLE Table_Name (
  column_name data_type(size) CHECK (logical_expression)
);

### 4. PRIMARY KEY
Used to uniquely identify each record in a table.
Properties:
Must contain unique values.
Cannot be null.
Should contain minimal fields.
Syntax:
sql
CREATE TABLE Table_Name (
  column_name data_type(size) PRIMARY KEY
);

### 5. FOREIGN KEY
Used to reference the primary key of another table.
Syntax:
sql
CREATE TABLE Table_Name (
  column_name data_type(size),
  FOREIGN KEY (column_name) REFERENCES other_table(column)
);

### 6. DEFAULT
Used to insert a default value into a column if no value is specified.

Syntax:
```
sql
CREATE TABLE Table_Name (
  col_name1 data_type,
  col_name2 data_type,
  col_name3 data_type DEFAULT 'default_value'
);

```
*Question 1*
--
![image](https://github.com/user-attachments/assets/a96ca725-91db-4ea8-bcdf-dcc5eef9d6e4)

sql
CREATE TABLE contacts(
contact_id INTEGER primary key,
first_name TEXT not NULL,
last_name TEXT not NULL,
email TEXT,
phone TEXT not NULL CHECK(LENGTH(phone)>=10)
);


*Output:*

![image](https://github.com/user-attachments/assets/fe1083f2-ee2c-4a61-bbb9-17021b66ce35)

*Question 2*
---
![image](https://github.com/user-attachments/assets/1c21219d-9085-4160-a3ab-c8014620e267)

```sql
ALTER TABLE customer
ADD COLUMN email VARCHAR(100);
```

*Output:*

![image](https://github.com/user-attachments/assets/f6be8068-773c-434a-8870-89f491912717)

*Question 3*
---
![image](https://github.com/user-attachments/assets/c302ada3-d5d2-4aec-a2cd-5c8394273291)
```

sql
CREATE TABLE item(
item_id TEXT primary key,
item_desc TEXT,
rate INTEGER,
icom_id TEXT CHECK(LENGTH(icom_id)>=4),
FOREIGN KEY(icom_id) REFERENCES company(com_id) ON DELETE SET NULL ON UPDATE SET NULL
);

```
*Output:*

![image](https://github.com/user-attachments/assets/6106ba83-ee42-43f0-9d93-d514243c25b9)

*Question 4*
---
![image](https://github.com/user-attachments/assets/614f1452-0985-4672-b0fa-648618c046c0)

```
sql
INSERT INTO student_details
SELECT * FROM archived_students;
```

*Output:*

![image](https://github.com/user-attachments/assets/d66370d3-9670-4616-985b-559b310d1430)


*Question 5*
---
![image](https://github.com/user-attachments/assets/866cb6e7-3e5b-4c84-98ea-567b19b27a82)

```
sql
INSERT INTO Products(ProductID,Name,Category)
VALUES(106,'Fitness Tracker','Wearables'); 
INSERT INTO Products(ProductID,Name,Category,Price,Stock)
VALUES(107,'Laptop','Electronic',999.99,50);  
INSERT INTO Products(ProductID,Name,Category,Stock)
VALUES(108,'Wireless Earbud','Accessorie',100);  

```
*Output:*

![image](https://github.com/user-attachments/assets/c6dc79d4-d5fd-40cf-89aa-8f7b07be4b7b)


*Question 6*
---
![image](https://github.com/user-attachments/assets/b91fd14e-99ad-40a5-a589-aeac80489fbd)
```

sql
INSERT INTO Products(ProductID,Name,Category)
VALUES(104,'Tablet','Electronics');
```

*Output:*

![image](https://github.com/user-attachments/assets/9d4a20a7-cc7b-403b-9127-7dc1ad841b07)


*Question 7*
---
![image](https://github.com/user-attachments/assets/1801a0f0-45e9-455d-a190-345887e81a26)
```

sql
ALTER TABLE Student_details
ADD Mobilenumber number;
```

*Output:*

![image](https://github.com/user-attachments/assets/6f41edbb-7d0c-4510-9164-329c3975a613)


*Question 8*
---
![image](https://github.com/user-attachments/assets/eef2857b-5b37-4f85-88d1-42b37a2240dc)

```
sql
CREATE TABLE Shipments(
ShipmentID INTEGER primary key,
ShipmentDate DATE,
SupplierID INTEGER,
OrderID INTEGER,
FOREIGN KEY(SupplierID) REFERENCES Suppliers(SupplierID),
FOREIGN KEY(OrderID) REFERENCES Orders(OrderID) 
);
```

*Output:*

![image](https://github.com/user-attachments/assets/72725fdd-146e-4019-978d-cd0df2f85d12)


*Question 9*
---
![image](https://github.com/user-attachments/assets/c42ebe08-e791-4916-a457-5e5175da5db5)

```
sql
CREATE TABLE jobs(
job_id INTEGER,
job_title TEXT DEFAULT '',
min_salary INTEGER DEFAULT 8000,
max_salary INTEGER DEFAULT NULL
);

```
*Output:*

![image](https://github.com/user-attachments/assets/3b2a4157-4f6d-40c0-8579-b1d8f9e2c03f)


*Question 10*
---
![image](https://github.com/user-attachments/assets/cfc37671-01b5-43e1-b32f-f91fb5b3a89a)
```

sql
CREATE TABLE Employees(
EmployeeID INTEGER,
FirstName TEXT,
LastName TEXT,
HireDate DATE 
);

```
*Output:*

![image](https://github.com/user-attachments/assets/6f9960b2-fe33-4149-b775-dbac9f718ef4)



## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.
