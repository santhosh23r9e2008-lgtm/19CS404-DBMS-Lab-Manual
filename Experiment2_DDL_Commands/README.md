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
--
-- <img width="1428" height="562" alt="image" src="https://github.com/user-attachments/assets/9fd65d2a-974d-4b97-a964-af8e91af8051" />


```sql
create table Products(
    ProductID  INTEGER,
    ProductName  TEXT,
    Price  REAL,
    Stock  INTEGER 
);
```

**Output:**

<img width="966" height="217" alt="image" src="https://github.com/user-attachments/assets/519db26b-3305-48e9-b824-1efa0264d4f1" />


**Question 2**
---
-- <img width="1335" height="361" alt="image" src="https://github.com/user-attachments/assets/904a0693-1484-4f54-af00-fa7464eb1a26" />


```sql
alter table  Student_details 
add column  MobileNumber NUMBER;
alter table Student_details
add column Address VARCHAR(100);
```

**Output:**

<img width="1069" height="262" alt="image" src="https://github.com/user-attachments/assets/b319359e-ff8a-45ff-8293-5bd91039023e" />


**Question 3**
---
-- <img width="1441" height="272" alt="image" src="https://github.com/user-attachments/assets/c7c28963-1bd0-4cc6-8873-36608f06059c" />

```sql
create table jobs(
    job_id integer,
    job_title text default ' ',
    min_salary integer default 8000,
    max_salary integer default NULL
);
```

**Output:**

<img width="1266" height="236" alt="image" src="https://github.com/user-attachments/assets/01a6f889-f8d3-445e-9c4a-92d0ade5e7d7" />

**Question 4**
---
-- <img width="1132" height="422" alt="image" src="https://github.com/user-attachments/assets/a9e09052-e023-4103-b0f7-e6161fc4b2bb" />


```sql
create table Invoices(
    InvoiceID  INTEGER  primary key,
    InvoiceDate DATE,
    DueDate  DATE CHECK (DueDate >InvoiceDate),
    Amount  REAL check (Amount> 0)
);
```

**Output:**

<img width="1219" height="262" alt="image" src="https://github.com/user-attachments/assets/bf7d1677-6c75-4231-951c-b2596331eec1" />

**Question 5**
---
-- <img width="1317" height="327" alt="image" src="https://github.com/user-attachments/assets/370925e4-8282-4f65-acd0-0751cc98dc4b" />


```sql
create table ProjectAssignments (
    AssignmentID INTEGER  primary key,
    EmployeeID INTEGER,
    ProjectID  INTEGER,
    AssignmentDate  DATE  NOT NULL,
    foreign key (EmployeeID) references Employees(EmployeeID), 
    foreign key (ProjectID) references  Projects(ProjectID) 
);
```

**Output:**

<img width="1330" height="215" alt="image" src="https://github.com/user-attachments/assets/592d28e3-c1fe-475f-bb57-6ebf66f4876f" />

**Question 6**
---
-- <img width="1122" height="292" alt="image" src="https://github.com/user-attachments/assets/f0aee5bb-2be7-49e6-b060-09a74b9c2880" />


```sql
create table Invoices(
    InvoiceID  INTEGER  primary key,
    InvoiceDate  DATE,
    Amount  REAL check (Amount>0),
    DueDate  DATE check(DueDate >InvoiceDate),
    OrderID INTEGER,
    foreign key (OrderID) references Orders(OrderID)
);  
```

**Output:**

<img width="1321" height="225" alt="image" src="https://github.com/user-attachments/assets/ef1ce4a3-fe81-4ef3-a01a-bc18d9efd221" />

**Question 7**
---
-- <img width="1275" height="269" alt="image" src="https://github.com/user-attachments/assets/c6fb8fe3-10b8-4cd6-a906-0efcb536aff5" />


```sql
insert into Customers ( CustomerID, Name, Address,City,ZipCode)
values (301,'Michael Jordan','123 Maple St','Chicago','60616');
```

**Output:**

<img width="1063" height="186" alt="image" src="https://github.com/user-attachments/assets/1540d6e7-4cdc-4c09-989a-aca4f45af4f7" />


**Question 8**
---
-- <img width="888" height="421" alt="image" src="https://github.com/user-attachments/assets/e11b542d-2275-4ea3-80e2-ec9891093f86" />


```sql
insert into Student_details (RollNo,Name,Gender,Subject,MARKS)
values (202, 'Ella King','F','Chemistry',87),
       (203,'James Bond','M','Literature',78);
```

**Output:**

<img width="1218" height="261" alt="image" src="https://github.com/user-attachments/assets/02c985cf-2693-400b-9445-adc00f6ad7e9" />


**Question 9**
---
-- <img width="1381" height="459" alt="image" src="https://github.com/user-attachments/assets/438c6d2d-bc02-4721-86a5-18dbf2a0d849" />


```sql
alter table Companies
add column designation varchar(50);
alter table Companies 
add column net_salary number;
```

**Output:**
<img width="1285" height="381" alt="image" src="https://github.com/user-attachments/assets/6d246056-ca14-4d3f-b11e-d39956da580d" />


**Question 10**
---
-- <img width="985" height="371" alt="image" src="https://github.com/user-attachments/assets/ac0e51ae-307c-4e78-914e-39ba3f21ec47" />


```sql
insert into Customers (CustomerID, Name, Address, Email)
select CustomerID, Name, Address,Email
from Old_customers;
```

**Output:**

<img width="1239" height="323" alt="image" src="https://github.com/user-attachments/assets/e85a8dc4-1a45-47a5-8d44-ef9c86482b14" />



## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.
