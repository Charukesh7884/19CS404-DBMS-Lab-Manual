# Experiment 4: Aggregate Functions, Group By and Having Clause

## AIM
To study and implement aggregate functions, GROUP BY, and HAVING clause with suitable examples.

## THEORY

### Aggregate Functions
These perform calculations on a set of values and return a single value.

- **MIN()** – Smallest value  
- **MAX()** – Largest value  
- **COUNT()** – Number of rows  
- **SUM()** – Total of values  
- **AVG()** – Average of values

**Syntax:**
```sql
### GROUP BY
Groups records with the same values in specified columns.
**Syntax:**
```sql
SELECT column_name, AGG_FUNC(column_name)
FROM table_name
GROUP BY column_name;
```
### HAVING
Filters the grouped records based on aggregate conditions.
**Syntax:**
```sql
SELECT column_name, AGG_FUNC(column_name)
FROM table_name
GROUP BY column_name
HAVING condition;
```

**Question 1**
--
Write a SQL query to find What is the age difference between the youngest and oldest employee in the company.
```sql
SELECT MAX(age) - MIN(age) AS age_difference
FROM employee;
```

**Output:**

<img width="669" height="347" alt="image" src="https://github.com/user-attachments/assets/b9a88af5-6de8-4f38-9b65-4abf214a838d" />

**Question 2**
---
Write a SQL query to Calculate the average income of the employees with names starting with 'A': 


```sql
select avg(income)  as avg_income 
from employee
where name like 'A%';
```

**Output:**

<img width="486" height="343" alt="image" src="https://github.com/user-attachments/assets/c49dbd53-2890-448e-9fe8-71fef9b0e1af" />

**Question 3**
---
What is the count of male and female patients?


```sql
SELECT Gender, COUNT(*) AS TotalPatients
FROM Patients
GROUP BY Gender;
```

**Output:**

<img width="647" height="388" alt="image" src="https://github.com/user-attachments/assets/b7b40d76-37c1-4ca0-8fa3-8412f9343e48" />

**Question 4**
---
How many patients have expired insurance coverage for each insurance company?


```sql
SELECT InsuranceCompany,COUNT(PatientID) AS TotalExpiredPatients
FROM Insurance
GROUP BY InsuranceCompany;
```

**Output:**

<img width="863" height="722" alt="image" src="https://github.com/user-attachments/assets/cd4e2341-4d73-4921-8c2b-da04ad899652" />

**Question 5**
---
Write the SQL query that accomplishes the grouping of data by age, calculates the total income for each age group, and includes only those age groups where the total income sum is greater than 1,000,000.


```sql
select age ,SUM(income) 
from employee 
group by age 
having SUM(income)>1000000;
```

**Output:**

<img width="573" height="429" alt="image" src="https://github.com/user-attachments/assets/8c9c7ad1-7710-4531-8240-2657f3a265c1" />

**Question 6**
---
Write the SQL query that achieves the selection of category and calculates the sum of the product of price and category ID as Revenue for each category from the "products" table, and includes only those products where the total revenue is greater than 25.


```sql
select category_id,(sum(price)*category_id) as Revenue 
from products group by category_id 
having revenue > 25;
```

**Output:**

<img width="598" height="450" alt="image" src="https://github.com/user-attachments/assets/8aa02531-3932-4dd7-8df4-c75f0ac29b38" />

**Question 7**
---
Write the SQL query that accomplishes the selection of total number of products for each category from the "products" table, and includes only those products where the minimum category ID is less than 3.

```sql
SELECT category_id, count(product_name)
FROM products
GROUP BY category_id
HAVING category_id < 3
```

**Output:**

<img width="744" height="389" alt="image" src="https://github.com/user-attachments/assets/4507772b-d1b5-43de-b0ef-2c88aaca73c5" />

**Question 8**
---
Write a SQL query to find the customer with longest name?


```sql
select name     ,max(length(name)) as     length
from customer;
```

**Output:**

<img width="609" height="327" alt="image" src="https://github.com/user-attachments/assets/c1fe0add-fedf-4eaa-b541-e9ff22fe3b37" />

**Question 9**
---
Write a SQL query to find  how many employees work in California?

```sql
select count(id) as employees_in_california
from employee
where city like '%California%';
```

**Output:**

<img width="630" height="331" alt="image" src="https://github.com/user-attachments/assets/7d834d0e-2b00-462f-bafd-58b0fe5a8056" />

**Question 10**
---
Write a SQL query to find the average length of email addresses (in characters):

```sql
SELECT AVG(LENGTH(email)) AS avg_email_length
FROM customer;
```

**Output:**

<img width="603" height="330" alt="image" src="https://github.com/user-attachments/assets/41e147b2-701c-44e8-8b16-4c3e6cf41259" />


## RESULT
Thus, the SQL queries to implement aggregate functions, GROUP BY, and HAVING clause have been executed successfully.
