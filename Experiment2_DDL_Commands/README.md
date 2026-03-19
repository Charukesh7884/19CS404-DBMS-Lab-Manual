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
Create a table named Departments with the following columns:

DepartmentID as INTEGER
DepartmentName as TEXT

```sql
CREATE TABLE Departments(
DepartmentID INTEGER,
DepartmentName TEXT
);
```

**Output:**

<img width="1291" height="370" alt="image" src="https://github.com/user-attachments/assets/660b8b55-61ee-43cb-83a9-8716ec3af420" />


**Question 2**
---
Write an SQL query to add two new columns, first_name and last_name, to the table employee. Both columns should have a data type of varchar(50).


```sql
ALTER TABLE employee
ADD first_name  varchar(50);
ALTER TABLE employee
ADD last_name varchar(50);
```

**Output:**

<img width="1297" height="332" alt="image" src="https://github.com/user-attachments/assets/1f7952e4-5bd6-4607-ab88-c8e7e7ee6280" />

**Question 3**
---
Write a SQL Query  to change the name of attribute "name" to "first_name"  and add mobilenumber as number ,DOB as Date in the table Companies. 


```sql
ALTER TABLE Companies
RENAME name to first_name;
ALTER TABLE Companies
ADD mobilenumber number;
ALTER TABLE Companies
ADD DOB Date;
```

**Output:**

<img width="1288" height="389" alt="image" src="https://github.com/user-attachments/assets/822e07a7-fbe2-4689-b4e8-cad748c4f6e7" />

**Question 4**
---
Create a table named Products with the following constraints:

ProductID should be the primary key.
ProductName should be NOT NULL.
Price is of real datatype and should be greater than 0.
Stock is of integer datatype and should be greater than or equal to 0.

```sql
CREATE TABLE Products(
ProductID primary key,
ProductName NOT NULL,
Price real check(Price>0),
Stock integer check(Stock>=0)
);
```

**Output:**

<img width="1292" height="287" alt="image" src="https://github.com/user-attachments/assets/668ba8ab-7088-4d91-898c-2249a91ce96a" />

**Question 5**
---
Insert the below data into the Employee table, allowing the Department and Salary columns to take their default values.


```sql
INSERT INTO Employee(EmployeeID, Name, Position)
VALUES (4, 'Emily White', 'Analyst');
```

**Output:**

<img width="1290" height="326" alt="image" src="https://github.com/user-attachments/assets/70e676d4-a021-4f63-8b18-2572cf3eacb9" />

**Question 6**
---
Insert the below data into the Books table, allowing the Publisher and Year columns to take their default values.

```sql
INSERT INTO Books(ISBN, Title, Author)
VALUES ('978-6655443321', 'Big Data Analytics', 'Karen Adams')
```

**Output:**

<img width="1286" height="322" alt="image" src="https://github.com/user-attachments/assets/4c568936-7ed8-42a9-a3bd-ef364276a286" />

**Question 7**
---
Create a table named Orders with the following columns:

OrderID as INTEGER
OrderDate as TEXT
CustomerID as INTEGER
```sql
CREATE TABLE Orders(
OrderID INTEGER,
OrderDate TEXT,
CustomerID INTEGER
);
```

**Output:**

<img width="1299" height="385" alt="image" src="https://github.com/user-attachments/assets/e75cb4fd-69d1-4106-9928-1364e04a8dae" />

**Question 8**
---
Create a table named Department with the following constraints:
DepartmentID as INTEGER should be the primary key.
DepartmentName as TEXT should be unique and not NULL.
Location as TEXT.

```sql
Create table Department(
DepartmentID INTEGER primary key,
DepartmentName TEXT unique not NULL,
Location TEXT
);
```

**Output:**

<img width="1297" height="317" alt="image" src="https://github.com/user-attachments/assets/e9beb530-e495-4cb8-90eb-943eff00c7c1" />

**Question 9**
---
Create a table named ProjectAssignments with the following constraints:
AssignmentID as INTEGER should be the primary key.
EmployeeID as INTEGER should be a foreign key referencing Employees(EmployeeID).
ProjectID as INTEGER should be a foreign key referencing Projects(ProjectID).
AssignmentDate as DATE should be NOT NULL.

```sql
CREATE TABLE ProjectAssignments(
AssignmentID INTEGER primary key,
EmployeeID INTEGER,
ProjectID INTEGER,
AssignmentDate DATE not null,
foreign key(EmployeeID)references Employees(EmployeeID)
foreign key(ProjectID) references Projects(ProjectID)
);
```

**Output:**

<img width="1292" height="315" alt="image" src="https://github.com/user-attachments/assets/4d89df66-b5f5-4dcc-8564-1d2601a7483b" />

**Question 10**
---
Insert all students from Archived_students table into the Student_details table.

```sql
INSERT INTO Student_details(RollNo,Name,Gender,Subject,MARKS)
SELECT RollNO,Name,Gender,Subject,MARKS
FROM Archived_students;
```

**Output:**

<img width="1294" height="291" alt="image" src="https://github.com/user-attachments/assets/16605711-21e6-4db8-8c60-496422437113" />


## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.
