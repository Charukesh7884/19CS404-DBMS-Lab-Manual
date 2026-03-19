# Experiment 3: DML Commands

## AIM
To study and implement DML (Data Manipulation Language) commands.

## THEORY

### 1. INSERT INTO
Used to add records into a relation.
These are three type of INSERT INTO queries which are as
A)Inserting a single record
**Syntax (Single Row):**
```sql
INSERT INTO table_name (field_1, field_2, ...) VALUES (value_1, value_2, ...);
```
**Syntax (Multiple Rows):**
```sql
INSERT INTO table_name (field_1, field_2, ...) VALUES
(value_1, value_2, ...),
(value_3, value_4, ...);
```
**Syntax (Insert from another table):**
```sql
INSERT INTO table_name SELECT * FROM other_table WHERE condition;
```
### 2. UPDATE
Used to modify records in a relation.
Syntax:
```sql
UPDATE table_name SET column1 = value1, column2 = value2 WHERE condition;
```
### 3. DELETE
Used to delete records from a relation.
**Syntax (All rows):**
```sql
DELETE FROM table_name;
```
**Syntax (Specific condition):**
```sql
DELETE FROM table_name WHERE condition;
```
### 4. SELECT
Used to retrieve records from a table.
**Syntax:**
```sql
SELECT column1, column2 FROM table_name WHERE condition;
```
**Question 1**
--
Write a SQL statement to Increase the selling price by 10% for all products in the 'Bakery' category in the products table.

Products table

---------------
product_id
product_name
category
cost_price
sell_price
reorder_lvl
quantity
supplier_id

```sql
UPDATE products
SET sell_price = sell_price * 1.10
WHERE category = 'Bakery';
```

**Output:**
<img width="1174" height="510" alt="image" src="https://github.com/user-attachments/assets/444367e0-de04-4564-8fda-3fa4fd3cd8fa" />

**Question 2**
---
Write a SQL statement to change the EMAIL and COMMISSION_PCT column of the following EMPLOYEES table with 'not available' and 0.55 for those employees whose DEPARTMENT_ID is 110.

Employees table

---------------
employee_id
first_name
last_name
email
phone_number
hire_date
job_id
salary
commission_pct
manager_id
department_id

```sql
UPDATE employees
SET email = 'not available',
    commission_pct = 0.55
WHERE department_id = 110;
```

**Output:**
<img width="1186" height="373" alt="image" src="https://github.com/user-attachments/assets/92bb5010-b407-41d4-bfbe-bcb123ab2a94" />


**Question 3**
---
Write a SQL statement to Update the product_name to 'Premium Bread' whose product ID is 5 in the products table.

Products table

---------------
product_id
product_name
category
cost_price
sell_price
reorder_lvl
quantity
supplier_id

```sql
UPDATE products
SET product_name = 'Premium Bread'
WHERE product_id = 5;
```

**Output:**
<img width="1182" height="392" alt="image" src="https://github.com/user-attachments/assets/c6e08c6f-dc01-40d3-8b0e-f2bb29d8e54f" />


**Question 4**
---
Write a SQL statement to Update the address to '58 Lakeview, Magnolia' where supplier ID is 5 in the suppliers table.

Suppliers Table 

name               type
-----------------  ---------------
supplier_id        INT
supplier_name      VARCHAR(100)
contact_person     VARCHAR(100)
phone_number       VARCHAR(20)
email              VARCHAR(100)
address            VARCHAR(250)
```sql
UPDATE suppliers
SET address = '58 Lakeview, Magnolia'
WHERE supplier_id = 5;
```

**Output:**
<img width="1182" height="393" alt="image" src="https://github.com/user-attachments/assets/74825dac-fb95-40cb-a75e-94a11f330779" />

**Question 5**
---
Write a SQL statement to Update the reorder level to 20 where the quantity in stock is less than 10 and product category is 'Snacks' in the products table.

Products table

---------------
product_id
product_name
category
cost_price
sell_price
reorder_lvl
quantity
supplier_id

```sql
UPDATE products
SET reorder_lvl = 20
WHERE quantity < 10
  AND category = 'Snacks';
```

**Output:**
<img width="1182" height="564" alt="image" src="https://github.com/user-attachments/assets/6568339b-1cda-46fa-84bd-501fccf889a7" />
**Output:**

![Output5](output.png)

**Question 6**
---
Write a SQL query to remove rows from the table 'customer' with the following condition -

1. 'cust_city' should begin with the letter 'L',

Sample table: Customer

```sql
DELETE FROM customer
WHERE cust_city LIKE'L%';
```

**Output:**

<img width="1202" height="813" alt="3(6)" src="https://github.com/user-attachments/assets/93a9f32f-5ba5-48b8-a05b-e0265e64a66c" />


**Question 7**
---
Write a SQL query to delete a doctor from Doctors table whose Specialization is 'Pediatrics' and First name is 'Michael'.

Sample table: Doctors

```sql
DELETE FROM Doctors
WHERE
specialization ='Pediatrics'AND first_name = 'Michael';
```

**Output:**

<img width="1200" height="474" alt="3(7)" src="https://github.com/user-attachments/assets/a35ed7a2-0f1a-4a3f-b360-c097f2b4323a" />


**Question 8**
---
Write a SQL query to Select all patients whose name starts with A.

Table: Patients

name                  type
--------------------  ----------
patient_id            INT
first_name            VARCHAR(50)
last_name             VARCHAR(50)
date_of_birth         DATE
admission_date        DATE
discharge_date        DATE
doctor_id             INT

```sql
SELECT * FROM Patients
WHERE first_name LIKE 'A%';
```

**Output:**

<img width="1216" height="468" alt="3(8)" src="https://github.com/user-attachments/assets/ac0d6f3d-727d-4db4-8608-eee54476ab5a" />


**Question 9**
---
Write a SQL query to categorize decimal as 'High', 'Medium', or 'Low' based on whether it is greater than 100, between 50 and 100, or less than 50 in the Calculations table

cid         name        type        notnull     dflt_value  pk
----------  ----------  ----------  ----------  ----------  ----------
0           id          INTEGER     0                       1
1           value1      REAL        0                       0
2           value2      REAL        0                       0
3           base        INTEGER     0                       0
4           exponent    INTEGER     0                       0
5           number      REAL        0                       0
6           decimal     REAL        0                       0

```sql
SELECT id,decimal,
case
    when decimal> 100 then 'High'
    when decimal BETWEEN 50 and 100  then 'Medium'
    ELSE 'Low'
    END AS category
    from Calculations;
```

**Output:**

<img width="1227" height="548" alt="3(9)" src="https://github.com/user-attachments/assets/c04a5886-bb83-47a6-bda3-9d21a0ebb9e0" />


**Question 10**
---
Write a SQL query to find customers who are either from the city 'New York' or who have a grade greater than 200. Return customer_id, cust_name, city, grade, and salesman_id.

Sample table: customer

 customer_id |   cust_name    |    city    | grade | salesman_id 
-------------+----------------+------------+-------+-------------
        3002 | Nick Rimando   | New York   |   100 |        5001
        3007 | Brad Davis     | New York   |   200 |        5001
        3005 | Graham Zusi    | California |   200 |        5002

```sql
SELECT customer_id, cust_name, city, grade,salesman_id FROM customer
WHERE City = 'New York' OR GRADE >200;
```

**Output:**

<img width="1189" height="554" alt="3(10)" src="https://github.com/user-attachments/assets/77e7adf5-1ef8-42a2-ad68-92173665cc9e" />

## RESULT
Thus, the SQL queries to implement DML commands have been executed successfully.
