# EXP No.2                                                                                                                                                       

## Date:


### AIM:

To study and implement DDL commands and different types of constraints.

### THEORY:

**1. CREATE:**

This is used to create a new relation (table)

**Syntax:**

CREATE TABLE (field_1 data_type(size),field_2 data_type(size), .. . );

**2. ALTER:**

This is used to add some extra fields into existing relation.

**Syntax:**

ALTER TABLE relation_name ADD (new field_1 data_type(size) );
(a)ALTER TABLE ...ADD...:
ALTER TABLE std ADD (Address CHAR(10));
(b )ALTER TABLE...MODIFY...:
ALTER TABLE relation_name MODIFY (field_1 newdata_type(Size)
( c) ALTER TABLE..DROP....
ALTER TABLE relation_name DROP COLUMN (field_name);
(d)ALTER TABLE..RENAME...:
ALTER TABLE relation_name RENAME COLUMN (OLD field_name) to (NEW field_name);

**3. DROP TABLE:**

This is used to delete the structure of a relation. It permanently deletes the records in the table.

**Syntax:**

DROP TABLE relation_name;

**4.RENAME:**

It is used to modify the name of the existing database object.

**Syntax:**

RENAME TABLE old_relation_name TO new_relation_name;

**CONSTRAINTS:**

Constraints are used to specify rules for the data in a table. If there is any
violation between the constraint and the data action, the action is aborted by the constraint. It can
be specified when the table is created (using CREATE TABLE statement) or after the table is
created (using ALTER TABLE statement).

**1. NOT NULL:** When a column is defined as NOTNULL, then that column becomes a
mandatory column. It implies that a value must be entered into the column if the record is to be
accepted for storage in the table.
Syntax: CREATE TABLE Table_Name (column_name data_type (size) NOT NULL, );

**2. UNIQUE:** The purpose of a unique key is to ensure that information in the column(s) is unique
i.e. a value entered in column(s) defined in the unique constraint must not be repeated across the
column(s). A table may have many unique keys.
Syntax: CREATE TABLE Table_Name(column_name data_type(size) UNIQUE, ….);

**3. CHECK:**
Specifies a condition that each row in the table must satisfy. To satisfy the constraint,
each row in the table must make the condition either TRUE or unknown (due to a null).
Syntax: CREATE TABLE Table_Name(column_name data_type(size) CHECK(logical
expression), ….);

**4. PRIMARY KEY:**
A field which is used to identify a record uniquely. A column or
combination of columns can be created as primary key, which can be used as a reference from
other tables. A table contains primary key is known as Master Table.
● It must uniquely identify each record in a table.
● It must contain unique values.
● It cannot be a null field.
● It cannot be a multi port field.
● It should contain a minimum number of fields necessary to be called unique.
Syntax: CREATE TABLE Table_Name(column_name data_type(size) PRIMARY KEY, ….);

**5. FOREIGN KEY:**
It is a table level constraint. We cannot add this at column level. To reference
any primary key column from other table this constraint can be used. The table in which the
foreign key is defined is called a detail table. The table that defines the primary key and is
referenced by the foreign key is called the master table.
Syntax: CREATE TABLE Table_Name(column_name data_type(size) FOREIGN
KEY(column_name) REFERENCES table_name);

**6. DEFAULT : **
The DEFAULT constraint is used to insert a default value into a column. The
default value will be added to all new records, if no other value is specified.
Syntax: CREATE TABLE Table_Name(col_name1,col_name2,col_name3 DEFAULT ‘’);

## 1.Create a table name as "Employee" with the following attributes

  ![image](https://github.com/LOKESHKUMARARI/dbmsexp2/assets/119406110/8c89272e-b81e-4224-95e9-9a7e0e1eb9b8)

  **ANSWER Query:**

 ```
CREATE TABLE Employee(
eid INTEGER PRIMARY KEY AUTOINCREMENT,
name VARCHAR(50),
desig VARCHAR(50),
dob DATE,
doj DATE) 
  ```


**OUTPUT:**

![image](https://github.com/LOKESHKUMARARI/dbmsexp2/assets/119406110/18f1c931-90d7-4fb7-af43-75642670ba62)


## 2.Write a SQL query for creating a table named "Orders" with the following attributes:

![image](https://github.com/LOKESHKUMARARI/dbmsexp2/assets/119406110/e1b633ed-2bf0-443f-bdba-ec07e3ac1cc2)


  
  **ANSWER Query:**

 ```
CREATE TABLE Orders(
OrderID INTEGER NOT NULL PRIMARY KEY AUTOINCREMENT,
ProductName Varchar(50),
Manufacturename varchar(50),
PersonID INTEGER  not null ,
FOREIGN KEY (PersonID )
REFERENCES Persons(PersonID))
  ```


**OUTPUT:**

![image](https://github.com/LOKESHKUMARARI/dbmsexp2/assets/119406110/8eae6231-b765-4d7d-bfc5-2374df82e528)


## 3.Write a SQL query for creating a table named "Orders" with the following attributes:

![image](https://github.com/LOKESHKUMARARI/dbmsexp2/assets/119406110/8f9905c6-2136-45a1-82f3-d697ae918afc)



  
  **ANSWER Query:**

 ```
CREATE TABLE Orders(
OrderID INTEGER NOT NULL PRIMARY KEY,
 OrderNumber  INTEGER,

PersonID INTEGER  not null ,
FOREIGN KEY (PersonID )
REFERENCES Persons(PersonID))
  ```


**OUTPUT:**

![image](https://github.com/LOKESHKUMARARI/dbmsexp2/assets/119406110/cdfdeab9-5d77-4fdd-81d6-80d56326c226)


## 4.Write a SQL Query for creating a table "Students" which already exists so use proper keyword in order to avoid error message

![image](https://github.com/LOKESHKUMARARI/dbmsexp2/assets/119406110/d0e33bd0-4d73-40d4-b350-9738f2781110)


  
  **ANSWER Query:**

 ```
CREATE TABLE IF NOT EXISTS Students (
    id NUMBER,
    grade VARCHAR(50),
    year INTEGER DEFAULT 2
);

  ```


**OUTPUT:**

![image](https://github.com/LOKESHKUMARARI/dbmsexp2/assets/119406110/20f8df99-89ea-4af1-90ee-f7cfd893cf42)


## 5.Write a SQL Query to Rename attribute "id" to employee_id  in the table employee

![image](https://github.com/LOKESHKUMARARI/dbmsexp2/assets/119406110/01efda62-71b5-45e4-8abb-d33eecc0489c)



  
  **ANSWER Query:**

 ```
ALTER TABLE employee
RENAME COLUMN id to employee_id;

  ```


**OUTPUT:**

![image](https://github.com/LOKESHKUMARARI/dbmsexp2/assets/119406110/ea6b6666-90e8-419c-8cf4-8a30b43d1204)



## 6.Write a SQL query for adding a new column named "email" with the datatype VARCHAR(100) to the  table "customer" 

![image](https://github.com/LOKESHKUMARARI/dbmsexp2/assets/119406110/9dbf48f0-6a25-4a8d-883c-8b72e34cc423)



  
  **ANSWER Query:**

 ```
Alter table customer
add column email VARCHAR(100);
);

  ```


**OUTPUT:**

![image](https://github.com/LOKESHKUMARARI/dbmsexp2/assets/119406110/5e6c1a07-c2f3-4b8a-bbb5-909f155df53d)




## 7.Write a SQL Query to Add attribute "mobilenumber"  in the table Companies 

![image](https://github.com/LOKESHKUMARARI/dbmsexp2/assets/119406110/e1cc8427-218e-4dba-87ff-32dadc5b8547)



  
  **ANSWER Query:**

 ```
ALTER TABLE Companies
ADD COLUMN mobilenumber number;

);

  ```


**OUTPUT:**

![image](https://github.com/LOKESHKUMARARI/dbmsexp2/assets/119406110/3a261dd1-b201-4d4e-be91-f4a4aad35b31)



## 8.Write a SQL Query for inserting the below values as multiple row format in the table "Student"

![image](https://github.com/LOKESHKUMARARI/dbmsexp2/assets/119406110/1a0f031a-43a9-4274-a972-87a492f27a86)


  
  **ANSWER Query:**

 ```
INSERT INTO Student(RollNo, NAME, Gender, Subject, MARKS,year)
VALUES(3,'Jeni','Female','English',96,3),
(4,'Bob Johnson','Male','History',90,3),
(5,'Sharvesh', 'Male','Botany', 97,3),
(6 ,'Mathew', 'Male','Science',85,3);

  ```


**OUTPUT:**

![image](https://github.com/LOKESHKUMARARI/dbmsexp2/assets/119406110/7ab9d596-24a5-454a-a543-a34a5b64926f)



## 9.Write a SQL Query for inserting the below values in the table "Student" with out multiple rows options

![image](https://github.com/LOKESHKUMARARI/dbmsexp2/assets/119406110/cf011741-cef2-4bd3-bd82-da5b3aa31549)



  
  **ANSWER Query:**

 ```
INSERT INTO Student(RollNo, NAME, Gender, Subject, MARKS,year)
VALUES(3,'Jeni','Female','English',96,1),
(4,'Bob Johnson','Male','History',90,1),
(5,'Sharvesh', 'Male','Botany', 97,1),
(6 ,'Mathew', 'Male','Science',85,1);
);

  ```


**OUTPUT:**

![image](https://github.com/LOKESHKUMARARI/dbmsexp2/assets/119406110/d8d4c0ba-10a8-4308-a78f-709fbb3486ea)



## 10.Write a SQL query for inserting new customer details (customer_id, name, email) from the 'old_customers' table into the 'new_customers' table with the subquery. Ensure that only customer email as "---@gmail.com"are included in the transfer.

![image](https://github.com/LOKESHKUMARARI/dbmsexp2/assets/119406110/94a2d925-252d-4aed-a633-38a7784c3e33)



  
  **ANSWER Query:**

 ```
INSERT INTO new_customers (customer_id, name, email)
SELECT customer_id, name, email
FROM old_customers
WHERE email LIKE '%@gmail.com';

  ```


**OUTPUT:**

![image](https://github.com/LOKESHKUMARARI/dbmsexp2/assets/119406110/ecbe08eb-7655-4e4c-a9e7-6a438b8c6f41) 

## Result:

Studying and Implementing  DDL commands and different types of constraint is done successfully.













