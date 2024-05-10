# EXP No.6                                                                                                                                                      

## Date:


### AIM:

To study and implement different types of joins
 
### THEORY:

The SQL Joins clause is used to combine records from two or more tables in a database. A JOIN
is a means for combining fields from two tables by using values common to each.The join is
actually performed by the ‘where’ clause which combines specified rows of tables.

**Syntax:**

```SELECT column 1, column 2, column 3...
FROM table_name1, table_name2
WHERE table_name1.column name = table_name2.columnname;
```

**Types of Joins:**

● Inner Join

● Left (Outer) Join

● Right (Outer) Join

● Full (Outer) Join

**INNER JOIN**

The INNER JOIN keyword selects records that have matching values in both tables.

**Syntax:**
```
SELECT column_name(s)
FROM table1
INNER JOIN table2
ON table1.column_name = table2.column_name;
```

**LEFT JOIN**

The LEFT JOIN keyword returns all records from the left table (table1), and the matching
records from the right table (table2). The result is 0 records from the right side, if there is no
match.

**Syntax:**
```
SELECT column_name(s)
FROM table1
LEFT JOIN table2
ON table1.column_name = table2.column_name;
```

**RIGHT JOIN**

The RIGHT JOIN keyword returns all records from the right table (table2), and the matching
records from the left table (table1). The result is 0 records from the left side, if there is no match.

**Syntax:**
```
SELECT column_name(s)
FROM table1
RIGHT JOIN table2
ON table1.column_name = table2.column_name;
```

**FULL OUTER JOIN**

The FULL OUTER JOIN keyword returns all records when there is a match in left (table1) or
right (table2) table records.
FULL OUTER JOIN and FULL JOIN are the same.

**Syntax:**
```
SELECT column_name(s)
FROM table1
FULL OUTER JOIN table2
ON table1.column_name = table2.column_name
WHERE condition;
```

## 1.Write the SQL query that achieves the selection of all columns from the "patients" table (aliased as "p"), with an inner join on the "patient_id" column and conditions filtering for test results with the test names 'Blood Test' or 'Blood Pressure' and results not containing the substring 'Normal'.

  ![image](https://github.com/LOKESHKUMARARI/dbmsexp6/assets/119406110/b86c0267-b242-4c74-9be2-afb3fa7e1a5f)

  **ANSWER Query:**

 ```
SELECT p.*
FROM patients AS p
JOIN test_results AS tr ON p.patient_id = tr.patient_id
WHERE tr.test_name IN ('Blood Test', 'Blood Pressure')
AND tr.result NOT LIKE '%Normal%';
 
  ```


**OUTPUT:**

![image](https://github.com/LOKESHKUMARARI/dbmsexp6/assets/119406110/c12ebb99-4638-4e16-aaed-1b792c57d2a5)

## 2.Write the SQL query that achieves the selection of the first name from the "patients" table, with an inner join on the "patient_id" column and a condition filtering for surgeries with a surgery date of '2024-01-15'.:

  ![image](https://github.com/LOKESHKUMARARI/dbmsexp6/assets/119406110/a4afd216-a3c1-4e51-a28c-9c646f441751)

  **ANSWER Query:**

 ```
SELECT p.first_name
FROM patients p
INNER JOIN surgeries s ON p.patient_id = s.patient_id
WHERE s.surgery_date = '2024-01-15';

 
  ```


**OUTPUT:**

![image](https://github.com/LOKESHKUMARARI/dbmsexp6/assets/119406110/5fc712f2-e5d8-4129-9eed-fbdc77319a41)

## 3.Write the SQL query that achieves the selection of the "name" column from the "salesman" table (aliased as "s"), with a left join on the "salesman_id" column and a condition filtering for customers in the city 'New York'.

 ![image](https://github.com/LOKESHKUMARARI/dbmsexp6/assets/119406110/aaa8cfea-ad26-4e10-9cc4-a8ea391cf61f)


  **ANSWER Query:**

 ```
SELECT 
    s.name
FROM 
    salesman s
LEFT JOIN 
    customer c ON s.salesman_id = c.salesman_id
WHERE 
    c.city = 'New York' OR c.city IS NULL;
  ```


**OUTPUT:**

![image](https://github.com/LOKESHKUMARARI/dbmsexp6/assets/119406110/7753440b-759d-4b45-b554-96bf9d1135ce)

## 4.From the following tables write a SQL query to find those orders where the order amount exists between 500 and 2000. Return ord_no, purch_amt, cust_name, city.

![image](https://github.com/LOKESHKUMARARI/dbmsexp6/assets/119406110/563ef77e-7871-4a32-9885-8a1960fa6bb3)


  **ANSWER Query:**

 ```
SELECT o.ord_no, o.purch_amt, c.cust_name, c.city
FROM orders o
JOIN customer c ON o.customer_id = c.customer_id
WHERE o.purch_amt BETWEEN 500 AND 2000;

  ```


**OUTPUT:**

![image](https://github.com/LOKESHKUMARARI/dbmsexp6/assets/119406110/52083ce5-bfb5-4217-b10a-2def1e1bcd04)


## 5.From the following tables write a SQL query to locate those salespeople who do not live in the same city where their customers live and have received a commission of more than 12% from the company. Return Customer Name, customer city, Salesman, salesman city, commission.  

 ![image](https://github.com/LOKESHKUMARARI/dbmsexp6/assets/119406110/f3af9909-f463-48b5-8e23-bf563324bbf2)


  **ANSWER Query:**

 ```
SELECT c.cust_name AS "Customer Name", c.city AS "city", 
       s.name AS "Salesman", s.city AS "city ", s.commission AS "commission"
FROM customer c
JOIN salesman s ON c.salesman_id = s.salesman_id
WHERE c.city <> s.city AND s.commission > 0.12;

  ```


**OUTPUT:**

![image](https://github.com/LOKESHKUMARARI/dbmsexp6/assets/119406110/ccfbeb22-6c07-4603-8001-a53e8a5e8198)


## 6. From the following tables write a SQL query to find salespeople who received commissions of more than 12 percent from the company. Return Customer Name, customer city, Salesman, commission.  

![image](https://github.com/LOKESHKUMARARI/dbmsexp6/assets/119406110/c0fbde36-6e46-47fb-a103-fe01f055ab6a)


  **ANSWER Query:**

 ```
SELECT c.cust_name AS "Customer Name", c.city AS "city",
       s.name AS "Salesman", s.commission AS "commission"
FROM customer c
JOIN salesman s ON c.salesman_id = s.salesman_id
WHERE s.commission > 0.12;
  ```


**OUTPUT:**

![image](https://github.com/LOKESHKUMARARI/dbmsexp6/assets/119406110/f0920d77-68ff-4f72-ae35-849b793d8d91)


## 7.Write the SQL query that achieves the selection of admission dates from the "patients" table and surgery dates from the "surgeries" table, with an inner join on the "patient_id" column.

![image](https://github.com/LOKESHKUMARARI/dbmsexp6/assets/119406110/0b339282-324b-4296-b909-90bb4c3bd227)


  **ANSWER Query:**

 ```
SELECT p.admission_date, s.surgery_date
FROM patients p
INNER JOIN surgeries s ON p.patient_id = s.patient_id;

  ```


**OUTPUT:**

![image](https://github.com/LOKESHKUMARARI/dbmsexp6/assets/119406110/678e6f4a-b7c3-4ff2-b7f4-69ef26f22c55)


## 8. From the following tables write a SQL query to find the salesperson(s) and the customer(s) he represents. Return Customer Name, city, Salesman, commission.

![image](https://github.com/LOKESHKUMARARI/dbmsexp6/assets/119406110/e7e6fc1e-c235-4dd9-a628-dad02c2f74c2)



  **ANSWER Query:**

 ```
SELECT 
    c.cust_name AS "Customer Name",
    c.city AS "city",
    s.name AS "Salesman",
    s.commission AS "commission"
FROM 
    customer c
JOIN 
    salesman s ON c.salesman_id = s.salesman_id;

  ```


**OUTPUT:**

![image](https://github.com/LOKESHKUMARARI/dbmsexp6/assets/119406110/0efc0f99-ee8f-45aa-9d67-7373a5c61d81)

## 9.From the following tables write a SQL query to find the details of an order. Return ord_no, ord_date, purch_amt, Customer Name, grade, Salesman, commission. 

![image](https://github.com/LOKESHKUMARARI/dbmsexp6/assets/119406110/e118e65c-7b2e-4737-9185-07b78fdc293c)


  **ANSWER Query:**

 ```
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


**OUTPUT:**

![image](https://github.com/LOKESHKUMARARI/dbmsexp6/assets/119406110/698d4ce2-98c1-4f14-a690-b3fdf62f2b3c)


## 10.Write the SQL query that achieves the selection of the "cust_name" column from the "customer" table (aliased as "c"), with a left join on the "customer_id" column and a condition filtering for orders with a purchase amount less than 100.

 ![image](https://github.com/LOKESHKUMARARI/dbmsexp6/assets/119406110/eaec66f7-6fbb-4e7f-ae15-f144a6126d49)


  **ANSWER Query:**

 ```
SELECT 
    c.cust_name
FROM 
    customer c
LEFT JOIN 
    orders o ON c.customer_id = o.customer_id
WHERE 
    o.purch_amt < 100 OR o.purch_amt IS NULL;

  ```


**OUTPUT:**

![image](https://github.com/LOKESHKUMARARI/dbmsexp6/assets/119406110/1cf0510f-431b-4176-84fb-6ed701e8350d)


## Result:

Studying and Implementing of different types of joins is done successfully.











