# EXP NO. 4 

## Date:

### AIM:

To study and implement aggregate functions, group by and having clause with suitable
examples.

### THEORY:

An aggregate function is a function that performs a calculation on a set of values, and returns a
single value.

Aggregate functions are often used with the GROUP BY clause of the SELECT statement. The
GROUP BY clause splits the result-set into groups of values and the aggregate function can be
used to return a single value for each group.

The most commonly used SQL aggregate functions are:

**● MIN() - returns the smallest value within the selected column**

**Syntax:**
```
SELECT MIN(column_name)
FROM table_name
WHERE condition;
```

Example: SELECT MIN (Sal) FROM emp;

**● MAX() - returns the largest value within the selected column**

**Syntax:**
```
SELECT MAX(column_name)
FROM table_name
WHERE condition;
```
Example: SELECT MAX (Sal) FROM emp;

**● COUNT() - returns the number of rows in a set**

**Syntax:**
```
SELECT COUNT(column_name)
FROM table_name
WHERE condition;
```
Example: SELECT COUNT (Sal) FROM emp;

**● SUM() - returns the total sum of a numerical column**

**Syntax:**
```
SELECT SUM(column_name)
FROM table_name
WHERE condition;
```
Example: SELECT SUM (Sal) From emp;

**● AVG() - returns the average value of a numerical column**

**Syntax:**
```
SELECT AVG(column_name)
FROM table_name
WHERE condition;
```
Example: Select AVG (10, 15, 30) FROM DUAL;

**GROUP BY:** This query is used to group all the records in a relation together for each and every
value of a specific key(s) and then display them for a selected set of fields in the relation.

**Syntax:**
```
SELECT column_name(s)
FROM table_name
WHERE condition
GROUP BY column_name(s)
ORDER BY column_name(s);
```
Example: SQL> SELECT EMPNO, SUM (SALARY) FROM EMP GROUP BY EMPNO;

**GROUP BY-HAVING:** The HAVING clause was added to SQL because the WHERE keyword
could not be used with aggregate functions. The HAVING clause must follow the GROUP BY
clause in a query and must also precede the ORDER BY clause if used.

**Syntax:**
```
SELECT column_name(s)
FROM table_name
WHERE condition
GROUP BY column_name(s)
HAVING condition
ORDER BY column_name(s);
```

## 1.How many medical records does each doctor have?

.![image](https://github.com/LOKESHKUMARARI/dbmsexp4/assets/119406110/a771b779-fcb7-4fb4-96c5-01ebf76e4e14)


  
  **ANSWER Query:**

 ```
select DoctorID, count(RecordID) as TotalRecords from MedicalRecords
group by DoctorID;

  ```


**OUTPUT:**

![image](https://github.com/LOKESHKUMARARI/dbmsexp4/assets/119406110/dbec890d-6f51-44cc-aeab-a284cfa42b6f)

## 2.What is the total number of appointments scheduled by each doctor?

![image](https://github.com/LOKESHKUMARARI/dbmsexp4/assets/119406110/a0150ebb-997f-44f7-ba8f-793140f33a98)

  
  **ANSWER Query:**

 ```
select DoctorID, count(AppointmentID) as TotalAppointments from Appointments
group by DoctorID;

  ```


**OUTPUT:**

![image](https://github.com/LOKESHKUMARARI/dbmsexp4/assets/119406110/83ad356e-da42-4539-ac08-b4c7ba88ad2d)

## 3.How many male and female doctors are there in each medical specialty?

![image](https://github.com/LOKESHKUMARARI/dbmsexp4/assets/119406110/79061d8d-b711-413d-be27-2f53ff138b1c)


  
  **ANSWER Query:**

 ```
select Specialty, Gender ,count(DoctorID) as TotalDoctors from Doctors
group by Specialty,Gender;
  ```


**OUTPUT:**

![image](https://github.com/LOKESHKUMARARI/dbmsexp4/assets/119406110/92a0f225-8880-4b66-a870-890d9fc0fdfb)

## 4.Write a SQL query to Calculate the average email length (in characters) for people who lives in Mumbai city

.![image](https://github.com/LOKESHKUMARARI/dbmsexp4/assets/119406110/a771b779-fcb7-4fb4-96c5-01ebf76e4e14)


  
  **ANSWER Query:**

 ```
select avg(length (email)) as avg_email_length_below_30 from customer
group by city
having city='Mumbai';

  ```


**OUTPUT:**

![image](https://github.com/LOKESHKUMARARI/dbmsexp4/assets/119406110/ab6d3cf6-676e-4327-a4a3-d8cf43ee150b)


## 5.Write a SQL query to find the number of employees who are having the same age removing the duplicate values.

![image](https://github.com/LOKESHKUMARARI/dbmsexp4/assets/119406110/d1bb3d0e-09b6-42d2-a2ee-f0a7f6a9aa28)

  
  **ANSWER Query:**

 ```
SELECT COUNT(distinct age) as COUNT FROM employee

  ```


**OUTPUT:**

![image](https://github.com/LOKESHKUMARARI/dbmsexp4/assets/119406110/7f43600b-ff93-4bbe-b9c0-8b52a6dc7ebb)


## 6.Write a SQL query to return the total number of rows in the 'customer' table where the city is not Noida.

![image](https://github.com/LOKESHKUMARARI/dbmsexp4/assets/119406110/b4343171-5e54-4fab-b5f2-ba3dd7225e35)



  
  **ANSWER Query:**

 ```
select count(distinct id) as COUNT from customer
where city!='Noida';

  ```


**OUTPUT:**

![image](https://github.com/LOKESHKUMARARI/dbmsexp4/assets/119406110/d24f7800-046c-4c38-8706-07a28687d90c)

## 7.Write the SQL query that accomplishes the grouping of data by joining date (jdate), calculates the average work hours for each date, and excludes dates where the average work hour is not less than 10.

![image](https://github.com/LOKESHKUMARARI/dbmsexp4/assets/119406110/394c94a9-ab24-4f6d-9f55-2d6fe8ca836d)


  **ANSWER Query:**

 ```
select jdate,AVG(workhour) from employee1
group by jdate
having AVG(workhour)<10

  ```


**OUTPUT:**

![image](https://github.com/LOKESHKUMARARI/dbmsexp4/assets/119406110/eb3f67fa-783b-4d57-b584-2fbc0efa4bb5)


## 8.Write the SQL query that achieves the grouping of data by city, calculates the average income for each city, and includes only those cities where the average income is greater than 500,000.

![image](https://github.com/LOKESHKUMARARI/dbmsexp4/assets/119406110/2f457bf0-dcdd-4d08-bdaa-e38cb4ae44eb)



  
  **ANSWER Query:**

 ```
select city,AVG(income) from employee
group by city
having AVG(income)>500000

  ```


**OUTPUT:**

![image](https://github.com/LOKESHKUMARARI/dbmsexp4/assets/119406110/8e967655-330f-43e9-b37d-f35ad9cded5c)

## 9.Write a SQL query to find the shortest email address in the customer table?

![image](https://github.com/LOKESHKUMARARI/dbmsexp4/assets/119406110/256bf5b1-55b9-4e55-a437-ed7a3c7bd0c9)


  
  **ANSWER Query:**

 ```
SELECT name, email, LENGTH(email) AS min_email_length
FROM customer
WHERE LENGTH(email) = (
    SELECT MIN(LENGTH(email))
    FROM customer
    WHERE email IS NOT NULL
)
LIMIT 1;
  ```


**OUTPUT:**

![image](https://github.com/LOKESHKUMARARI/dbmsexp4/assets/119406110/79b3891b-31b3-4641-aa3b-88550ba1e8ef)

## 10.Write a SQL query to find the total income of employees aged 40 or above.

![image](https://github.com/LOKESHKUMARARI/dbmsexp4/assets/119406110/3f079544-87fc-4299-a78c-c373901060fa)


  **ANSWER Query:**

 ```
SELECT SUM(income) AS total_income
FROM employee
WHERE age >= 40;
  ```


**OUTPUT:**

![image](https://github.com/LOKESHKUMARARI/dbmsexp4/assets/119406110/580cdcc9-141e-4a89-8789-331125a61396)

## Result:

Studying and Implementing aggregate functions, group by and having clause with suitable
examples.




