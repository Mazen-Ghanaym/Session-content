
# SQL-TROSC

## [Session record](https://cisuezedu.sharepoint.com/:v:/s/TROSE/EY7J0tksjqBCpQLMQejPO4wBHeSwHK5boWNRHT1SG42XsQ)

## Outlines

- **[Introduction](#introduction)**
- **[Data Types](#sql-data-types)**
- **[Constraints](#constraints)**
- **[Create Table](#create-table)**
  - **[Alter Table](#alter-table)**
  - **[Insert Into](#insertion)**
- **[Select](#select)**
- **[Where](#where)**
- **[Order By](#order-by)**
- **[Group By](#group-by)**
- **[Foreign key](#foreign-key)**

-------------------------------------------------------------------------
### Introduction
In the earlier days, databases were non-existent, and organizations relied on flat-files and spreadsheets to store data. However, this approach proved inefficient, leading to increased data redundancy and a lack of data concurrency. Recognizing these challenges, the concept of databases and Relational Database Management Systems (RDBMS) was introduced. The primary goal was to minimize data redundancy and enhance the ease of data manipulation. To achieve this, the Structured Query Language (SQL) was developed, offering a powerful toolset for creating, reading, updating, and deleting data (CRUD operations)

------------------------------------------------------------------------
### SQL Data types
- Number
    1. NUMBER.
    2. NUMBER(number of digits).
    3. NUMBER(number of digits, number of digits after floating point).
- Text or Strings
    1. CHAR(number of characters)     -> Doesn't free unused allocated memory for characters.
    1. VARCHAR2(number of characters) -> free unused allocated memory.
- Date
    1. Date 
> [!NOTE]
> There are more data types, but these are the most famous for your practical exam.
--------------------------------------------------------------------------
### Constraints
- Primary key.
    - unique.
    - Not Null.
    - Numeric.
- Foreign key.
    - Used To connect two tables.
- Unique.
    - data can be Null but not Repeated.
- Check.
    - Condition -> ex: “check(age > 15)”.
- Not Null
    - Column must have data.
------------------------------------------------------------------------------
### Create Table
We create a table using the following command:
``` SQL
CREATE TABLE <table name>(
    column1 datatype constraint,
    column2 datatype constraint,
    ...
    );
```
ex:
``` SQL
CREATE TABLE dept(
    dno NUMBER PRIMARY KEY,
    dname VARCHAR2(10)
);

CREATE TABLE users(
    id NUMBER PRIMARY KEY,
    name VARCHAR2(20) NOT NULL,
    address VARCHAR2(30),
    email VARCHAR2(15) UNIQUE NOT NULL,
    age NUMBER(2) CHECK(age > 15)
);
```
Use the following command to show the table schema:
``` SQL
    DESCRIBE users;
    DESC users;
```
Use the following command to change a table's name:
``` SQL
    RENAME dept TO dept1;
```
Use the following command to delete a table:
``` SQL
    DESC dept1; --exists
    DESC dept;  -- doesn't exist
    DROP TABLE dept;
```
#### Alter Table
- ADD

        used to add a column to an exited table.  
        ex:
  ``` SQL
      CREATE TABLE dept(
        dno NUMBER PRIMARY KEY,
        dname VARCHAR2(10)
      );
      ALTER TABLE dept
      ADD location VARCHAR2(20);
  ```
      used to add constraint
  ``` SQL
      ALTER TABLE dept
      ADD PRIMARY KEY(deptno);
  ```
- MODIFY

      used to modify a column data type
      ex:
    ``` SQL
        ALTER TABLE dept
        MODIFY dname VARCHAR2(20);
    ```
> [!NOTE]
> You can increase any column's data type, but you can't decrease it if it contains data.

> [!NOTE]
> You can change a column data type if it does not contain data.
- DROP

      used to delete a column
      ex:
    ``` SQL
        ALTER TABLE dept
        DROP COLUMN location;
    ```
- RENAME
  
          rename column
    ```SQL
        ALTER TABLE dept
        RENAME COLUMN deptno to dno;
    ```
------------------------------------------------------------------
#### Insertion
- INSERT
  
    We can insert it into a table using the following command:
    ``` SQL
        INSERT INTO <table name>(columns' names) -- you can use it or not but if you don't use columns' names you must enter all columns' data
        VALUES(enter data with order of columns);
    ```
    ex:
    ``` SQL
    -- id, name, address, email, age
        INSERT INTO users 
        VALUES(1, 'mazen mohamed', 'ismailia','mazen@gmail.com', 19);
        INSERT INTO users(id, name, email, age)
        VALUES(2,'ahmed hassan', 'ahmed1@gmail.com', 16);
        INSERT INTO users
        VALUES(3,'ali ahmed', 'cairo', 'ali@gmail.com', 50);
        INSERT INTO users
        VALUES(4, 'omar ali', 'ismailia', 'omar@gmail.com', 50);
        INSERT INTO users
        VALUES(5, 'mahmoued ahmed', 'alex', 'mahmoud@gmail.com', 30);
        INSERT INTO users
        VALUES(6, 'ahmed ali', 'cairo', 'ahmed2@gmail.com', 40);
        INSERT INTO users
        VALUES(7, 'ahmed mohamed', 'sina', 'ahmed3@gmail.com', 52);
        INSERT INTO users
        VALUES(8, 'khaled sameh', 'ismailia', 'khalid@gmail.com', 25);
    ```
- UPDATE

  Use update to update a row of data
  
  ex:
``` SQL
  UPDATE users
  SET column_name = value, column_name = value, ...
  WHERE Condition;
```
> [!CAUTION]
> ``` SQL
>      UPDATE users
>      SET address = 'cairo';
> ```
``` SQL
  -- Correct
  UPDATE users
  SET address = 'cairo';
  WHERE id = 2;
```
- DELETE

  Use delete to delete a row of data

    ``` SQL
        DELETE FROM <table name>
        WHERE condition;
    ```
    ex:
    ``` SQL
        DELETE FROM users
        WHERE id = 2;
    ```
>[!CAUTION]
> ``` SQL
>     DELETE FROM users; -- will delete all table data
> ```
-------------------------------------------------
### SELECT
    We can use a select statement to show the table's data
``` SQL
    SELECT id, name, address, email FROM users;
```
   To select all table's columns
``` SQL
    SELECT * FROM users;
```
    aliases
``` SQL
    SELECT name as username FROM users;
```
``` SQL
    SELECT name username FROM users;
```
``` SQL
    SELECT name "user name" FROM users;
```
    concatenation
``` SQL
    SELECT name||email FROM users;
```
``` SQL
    SELECT name||' '||email FROM users;
```
``` SQL
    SELECT name||' '||email userdata FROM users;
```
#### WHERE
    relational operators
Operator | Name | Operation
-------------|:-----------:|----------------------------------:
=         | equals     | check whether right equals left ex: age = 15
\>         | greater than | check right greater than left ex: age > 14
\>=         | greater than or equal     | check whether right is greater than or equal to left ex: age >= 15
\<         | less than | check right less than left ex: age < 14
<=         | less than or equal     | check whether right is less than or equal to left ex: age <= 15
<> or !=   | Not equal    | check whether right doesn't equal left ex: age != 15 or age age <> 15

``` SQL
    SELECT name FROM users
    WHERE age > 20;
```
``` SQL
    SELECT name FROM users
    WHERE id = 5;
```
``` SQL
    SELECT name FROM users
    WHERE age <= 40;
```
``` SQL
    SELECT name FROM users
    WHERE age < 40;
```
``` SQL
    SELECT name FROM users
    WHERE age <> 40;
```
    Logical Operators
Operator | Operation
--------:|----------:
AND    | To conditions must be true to be true ex: age < 40 AND age > 20
OR     | at least one condition satisfied ex: age < 40 OR age > 20
NOT    |

``` SQL
    SELECT name FROM users
    WHERE age < 40 AND age > 20;
```
``` SQL
    SELECT name FROM users
    WHERE age < 40 OR age > 20;
```
    Additional
- Between
  
  used to select a range
  ``` SQL
      SELECT name FROM users
      WHERE age >= 20 AND age <= 40;
      -- equals to
      SELECT name FROM users
      WHERE age BETWEEN 20 AND 40;
  ```
- LIKE

  Undetermined data
  ``` SQL
  SELECT name FROM users
  WHERE name LIKE 'ahmed%'
  ```
  ``` SQL
  SELECT name FROM users
  WHERE name LIKE '%mohamed';
  ```
  ``` SQL
  SELECT name FROM users
  WHERE name LIKE '%en%';
  ```
  ``` SQL
  SELECT name FROM users
  WHERE name LIKE '_a%';
  ```
  ``` SQL
  SELECT name FROM users
  WHERE name LIKE '__z%';
  ```
- IN
  
  SELECT Multiple data
  ``` SQL
      SELECT name FROM users
      WHERE age = 15 OR age = 20 OR age = 40;
      -- equals to
      SELECT name FROM users
      WHERE age IN(15,20,40);
  ```
#### ORDER BY

  use order by clause to sort rows ascending or descending
  first of all, we need more data in table users
```SQL
ALTER TABLE users
ADD salary NUMBER(6,2) CHECK(salary>0);
```
``` SQL
UPDATE users
SET salary= 1000
WHERE id=1;
```
``` SQL
UPDATE users
SET salary= 2000
WHERE id=3;
```
``` SQL
UPDATE users
SET salary= 1500
WHERE id=4;
```
``` SQL
UPDATE users
SET salary= 4000
WHERE id=5;
```
``` SQL
UPDATE users
SET salary= 3800
WHERE id=6;
```
``` SQL
UPDATE users
SET salary= 8000
WHERE id=7;
```
``` SQL
UPDATE users
SET salary= 2600
WHERE id=8;
```
    Order by
   ``` SQL
   SELECT * FROM users;
   ```
   ``` SQL
   SELECT * FROM users ORDER BY salary ASC;
   ```
   ``` SQL
   SELECT * FROM users ORDER BY salary DESC;
   ```
   ``` SQL
   SELECT * FROM users
   WHERE salary BETWEEN 3000 AND 5000
   ORDER BY salary;
   ```
  #### Aggregate Function
  function | its use
  ---------:|---------:
  count( ) | count number of rows
  Avg( )   | calculate average
  Sum( )   | Returns the sum of all selected column
  Max( )   | Get Maximum number
  Min( )   | GET Minimum number

  ex:
  ``` SQL
      SELECT MAX(salary) FROM users;
  ```
  ``` SQL
      SELECT MIN(salary) FROM users;
  ```
  ``` SQL
      SELECT COUNT(salary) FROM users;
  ```
  ``` SQL
      SELECT COUNT(*) FROM users;
  ```
  ``` SQL
      SELECT AVG(salary) FROM users;
  ```
  ``` SQL
      SELECT SUM(salary) FROM users;
  ```
#### GROUP BY

    Used to group data with specific column 
     Used with aggregation functions 
``` SQL
SELECT COUNT(name), address FROM users
WHERE age > 20 AND age < 40;
GROUP BY address;
```
``` SQL
SELECT COUNT(name), address, SUM(salary) "total salary" FROM users
WHERE age > 20 AND age < 40;
GROUP BY address;
```
    Having like where but used with GROUP BY as WHERE
``` SQL
SELECT COUNT(name), address, SUM(salary) FROM users
WHERE age > 20 AND age < 40;
GROUP BY address;
HAVING SUM(salary) > 4000;
```
``` SQL
SELECT COUNT(name), address, SUM(salary) FROM users
WHERE age > 20 AND age < 40;
GROUP BY address;
HAVING SUM(salary) > 4000;
ORDER BY SUM(salary);
```

#### FOREIGN KEY
1. create table dept (department)
    ``` SQL
        CREATE TABLE dept
        deptno NUMBER PRIMARY KEY,
        deptname VARCHAR2(20) NOT NULL
    ```
1. Add column deptno to users
   ```SQL
       ALTER TABLE users
       ADD deptno NUMBER;
   ```
1. Add constraint
   ```SQL
       ALTER TABLE users
       ADD FOREIGN KEY(deptno) REFERENCES dept(deptno);
   ```
--------------------------------------------------------

  
  
