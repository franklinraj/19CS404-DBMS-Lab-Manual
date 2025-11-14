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
-- Paste Question 1 here
Write a SQL query to Add a new ParentsNumber column  as number and Adhar_Number as Number in the Student_details table.
```sql
alter table Student_details add column ParentsNumber number;
alter table Student_details add column Adhar_Number number;
```

**Output:**
<img width="1338" height="388" alt="image" src="https://github.com/user-attachments/assets/7c4307d2-4678-4ba3-9bc7-79f32a4b5f52" />


**Question 2**
---
Write an SQL query to add two new columns, designation and net_salary, to the table Companies. The designation column should have a data type of varchar(50), and the net_salary column should have a data type of number.

```sql
alter table Companies add column designation varchar(50);
alter table Companies add column net_salary number;
```

**Output:**


**Question 3**
---
Create a table named Employees with the following constraints:

EmployeeID should be the primary key.
FirstName and LastName should be NOT NULL.
Email should be unique.
Salary should be greater than 0.
DepartmentID should be a foreign key referencing the Departments table.

```sql
create table Employees(
    EmployeeID INTEGER primary key,
    FirstName TEXT NOT NULL,
    LastName TEXT NOT NULL,
    Email  text UNIQUE,
    Salary INTEGER check(Salary>0),
    DepartmentID INTEGER,
    foreign key(DepartmentID) REFERENCES Departments
);
```

**Output:**

<img width="1231" height="505" alt="image" src="https://github.com/user-attachments/assets/ce0d3c02-68f7-4365-b0f6-1ab226318624" />


**Question 4**
---
create a table named jobs including columns job_id, job_title, min_salary and max_salary, and make sure that, the default value for job_title is blank and min_salary is 8000 and max_salary is NULL will be entered automatically at the time of insertion if no value assigned for the specified columns.

```sql
create table jobs(
    job_id integer,
    job_title text,
    min_salary integer default 8000,
    max_salary integer null
);
```

**Output:**

<img width="1233" height="411" alt="image" src="https://github.com/user-attachments/assets/243adbd8-da7a-45fe-aba8-9b78f16a4cb5" />

**Question 5**
---
Insert a student with RollNo 201, Name David Lee, Gender M, Subject Physics, and MARKS 92 into the Student_details table.

```sql
insert into Student_details(RollNo,Name,Gender,Subject,MARKS)values(201,'David Lee','M','Physics',92);
```

**Output:**

<img width="1228" height="317" alt="image" src="https://github.com/user-attachments/assets/06ce2949-5097-452e-aad8-ac3c4dcbef38" />


**Question 6**
---
Create a table named Members with the following columns:

MemberID as INTEGER
MemberName as TEXT
JoinDate as DATE

```sql
create table Members(
    MemberID INTEGER,
    MemberName TEXT,
    JoinDate DATE
);
```

**Output:**

<img width="1230" height="459" alt="image" src="https://github.com/user-attachments/assets/4879f1c3-02fb-49a0-8ef4-ebfb46fa1bce" />


**Question 7**
---
Create a table named Department with the following constraints:
DepartmentID as INTEGER should be the primary key.
DepartmentName as TEXT should be unique and not NULL.
Location as TEXT.

```sql
create table Department(
    DepartmentID INTEGER primary key,
    DepartmentName text unique not null,
    Location text
);
```

**Output:**



**Question 8**
---
Insert all books from Out_of_print_books into Books

Table attributes are ISBN, Title, Author, Publisher, YearPublished

```sql
insert into Books(ISBN,Title,Author,Publisher,YearPublished)select * from Out_of_print_books;
```

**Output:**



**Question 9**
---
Write a SQL Query for inserting the below values in the table Customers

```sql
insert into Customers(ID,NAME,AGE,ADDRESS,SALARY)VALUES
        (1,'Ramesh',32,'Ahmedabad',2000),
        (2,'Khilan',25,'Delhi',1500),
        (3,'Kaushik',23,'Kota',2000);
```

**Output:**

<img width="1212" height="354" alt="image" src="https://github.com/user-attachments/assets/263c8e6f-35ef-4f73-9ed5-9eadb0d3c934" />


**Question 10**
---
Create a table named Shipments with the following constraints:
ShipmentID as INTEGER should be the primary key.
ShipmentDate as DATE.
SupplierID as INTEGER should be a foreign key referencing Suppliers(SupplierID).
OrderID as INTEGER should be a foreign key referencing Orders(OrderID).

```sql
create table Shipments(
    ShipmentID INTEGER PRIMARY KEY,
    ShipmentDate date,
    SupplierID integer,
    OrderID integer,
    FOREIGN KEY(SupplierID) references Suppliers(supplierID),
    foreign key(OrderID) references Orders(OrderID)
);
```

**Output:**
<img width="1231" height="305" alt="image" src="https://github.com/user-attachments/assets/39d20e4f-959b-4cd6-9777-d870efd83743" />

**Completion status:**
<img width="1110" height="226" alt="image" src="https://github.com/user-attachments/assets/54c3cc25-fc6a-4a70-9102-044d2a3dd4e6" />

## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.
