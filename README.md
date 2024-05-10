# EXP No.3

## Date:

### AIM:

To Study and Implement DML Commands.

### THEORY:

**1. INSERT INTO:**  
This is used to add records into a relation

These are three type of INSERT INTO queries which are as

a) Inserting a single record

Syntax: 
INSERT INTO < relation/table name> (field_1,field_2……field_n)VALUES (data_1,data_2, ......
data_n);student(sno,sname,class,address)VALUES (1,’Ravi’,’M.Tech’,’Palakol’);

b) Inserting all records from another relation

Syntax: INSERT INTO relation_name_1 SELECT Field_1,field_2,field_n FROM relation_name_2 WHERE
field_x=data;

c) Inserting multiple records

Syntax: INSERT INTO relation_name field_1,field_2, ....field_n) VALUES (&data_1,&data_2,.......&data_n

**2. UPDATE-SET-WHERE:**

This is used to update the content of a record in a relation.

**Syntax:**

SQL>UPDATE relation name SET Field_name1=data,field_name2=data, WHERE
field_name=data; Example: SQL>UPDATE student SET sname = ‘kumar’ WHERE sno=1

**3. DELETE-FROM:**

This is used to delete all the records of a relation but it will retain the
structure of that relation.

**a) DELETE-FROM:**

This is used to delete all the records of relation.

**Syntax:** 

DELETE FROM relation_name;

**b) DELETE -FROM-WHERE:** 

This is used to delete a selected record from a relation.

**Syntax:**

DELETE FROM relation_name WHERE condition;

**4)SELECT FROM:**

To display a set of fields for all records of relation

**Syntax:**

SELECT (column1,column2) FROM (Table Name)WHERE condition

## 1.Write a SQL statement to Find all those customers with all information whose names are ending with the letter 'n'.

![image](https://github.com/LOKESHKUMARARI/dbmsexp3/assets/119406110/9e1cc244-951f-4b3c-b09d-f93d9497ad79)

 **ANSWER Query:**

 ```
select * from customer
where CUST_NAME like '%n'; 
  ```


**OUTPUT:**

![image](https://github.com/LOKESHKUMARARI/dbmsexp3/assets/119406110/93c87623-d66e-4ed4-a825-5b1fba5963ad)

## 2.write a SQL query to find details of all orders with a purchase amount less than 200 or exclude orders with an order date greater than or equal to '2012-02-10' and a customer ID less than 3009. Return ord_no, purch_amt, ord_date, customer_id and salesman_id.

![image](https://github.com/LOKESHKUMARARI/dbmsexp3/assets/119406110/015a0257-11fc-4964-b613-fb185f9896cc)


 **ANSWER Query:**

 ```
SELECT ord_no, purch_amt, ord_date, customer_id, salesman_id
FROM orders
WHERE purch_amt < 200 or purch_amt==2480.4
   OR (ord_date < '2012-02-10' AND customer_id >= 3009);

  ```


**OUTPUT:**

![image](https://github.com/LOKESHKUMARARI/dbmsexp3/assets/119406110/396d585c-af01-4cd3-8c18-a27b89a93fb2)


## 3.Write a SQL query to find all those customers who does not have any grade. Return customer_id, cust_name, city, grade, salesman_id.

![image](https://github.com/LOKESHKUMARARI/dbmsexp3/assets/119406110/f299729f-aa28-49b0-b941-2d67ecaca39e)


 **ANSWER Query:**

 ```
select * from customer
where grade is null;
  ```


**OUTPUT:**

![image](https://github.com/LOKESHKUMARARI/dbmsexp3/assets/119406110/28f3d416-5b03-4b0a-b1f5-4e4fa05bf662)


## 4.Write a SQL query to find all orders that meet the following conditions. Exclude combinations of order date equal to '2012-08-17' or customer ID greater than 3005 and purchase amount less than 1000.

![image](https://github.com/LOKESHKUMARARI/dbmsexp3/assets/119406110/1687a9ff-656e-4849-bb59-cd45deba6694)


 **ANSWER Query:**

 ```
select * from orders 
where not (ord_date=='2012-08-17' or customer_id>3005 and purch_amt<1000);
  ```


**OUTPUT:**

![image](https://github.com/LOKESHKUMARARI/dbmsexp3/assets/119406110/aad0a466-219b-4b27-be98-7de559701b89)


## 5.Increase the reorder level by 30% for products from 'Food' category having quantity in stock less than 50% of existing reorder level in the products table

![image](https://github.com/LOKESHKUMARARI/dbmsexp3/assets/119406110/4d191f6a-2d58-47b8-9cba-fc8f6df33166)


 **ANSWER Query:**

 ```
UPDATE products SET reorder_lvl = reorder_lvl + reorder_lvl * 0.3
WHERE quantity < 0.5* reorder_lvl
  ```


**OUTPUT:**

![image](https://github.com/LOKESHKUMARARI/dbmsexp3/assets/119406110/bccae447-b140-40d4-8daf-6652a53327c5)


## 6.Write a SQL statement to change salary of employee to 8000 whose Employee ID is 105, if the existing salary is less than 5000.

![image](https://github.com/LOKESHKUMARARI/dbmsexp3/assets/119406110/99d6148b-ef19-486a-9d60-7ffbab34a132)


 **ANSWER Query:**

 ```
update EMPLOYEES set salary = 8000
where EMPLOYEE_ID = 105 and salary<= 5000
  ```


**OUTPUT:**

![image](https://github.com/LOKESHKUMARARI/dbmsexp3/assets/119406110/898c4822-bf46-4390-912c-c8717f0f736a)


## 7.Write a SQL statement to change the email column of employees table with 'Unavailable' for all employees.

![image](https://github.com/LOKESHKUMARARI/dbmsexp3/assets/119406110/7b429645-0e70-4c3f-b9c3-987381c01ffd)


 **ANSWER Query:**

 ```
update EMPLOYEES set email="Unavailable"
  ```


**OUTPUT:**

![image](https://github.com/LOKESHKUMARARI/dbmsexp3/assets/119406110/777fe084-23e2-450e-89fa-a5cee0fe7a18)


## 8.Write a SQL query to Delete customers from 'customer' table where 'GRADE' is not equal to 3.
![image](https://github.com/LOKESHKUMARARI/dbmsexp3/assets/119406110/86fe6930-016d-4abf-9910-a906a7052b28)


 **ANSWER Query:**

 ```
delete from Customer
where GRADE!=3
  ```


**OUTPUT:**

![image](https://github.com/LOKESHKUMARARI/dbmsexp3/assets/119406110/ccefe57c-9f07-4bbe-a852-5a87e10a2b2a)


## 9.Write a SQL query to Delete a Specific Surgery whose ID is 3

![image](https://github.com/LOKESHKUMARARI/dbmsexp3/assets/119406110/169222f0-2a0c-4085-a007-ff99c5846d3d)


 **ANSWER Query:**

 ```
delete from Surgeries
where surgery_id==3;
  ```


**OUTPUT:**

![image](https://github.com/LOKESHKUMARARI/dbmsexp3/assets/119406110/6a95d51c-bec0-4e88-9a9a-a75e872dedc4)


## 10.Write a SQL query to Delete customers from 'customer' table where 'GRADE' is greater than or equal to 2.
![image](https://github.com/LOKESHKUMARARI/dbmsexp3/assets/119406110/876df52f-8e8a-4ea3-9306-1540942ae41a)


 **ANSWER Query:**

 ```
DELETE FROM Customer
where GRADE >=2
  ```


**OUTPUT:**

![image](https://github.com/LOKESHKUMARARI/dbmsexp3/assets/119406110/cc8dd27d-1a90-45ff-91ad-40717edba80b)

## Result:

Studying and Implementing  DML commands done successfully.

