# SQL-TROSC

## [Session Record](https://cisuezedu.sharepoint.com/:v:/s/TROSE/EY7J0tksjqBCpQLMQejPO4wBHeSwHK5boWNRHT1SG42XsQ)

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
- **[Foreign Key](#foreign-key)**

---

### Introduction

Databases have evolved from early flat-file systems to sophisticated Relational Database Management Systems (RDBMS) to address inefficiencies such as data redundancy and lack of concurrency. SQL (Structured Query Language) provides the tools for creating, reading, updating, and deleting data, collectively known as CRUD operations.

---

### SQL Data Types

- **Number**
  - `NUMBER`
  - `NUMBER(number_of_digits)`
  - `NUMBER(number_of_digits, number_of_decimal_places)`
- **Text or Strings**
  - `CHAR(number_of_characters)` - Fixed size; retains unused memory.
  - `VARCHAR2(number_of_characters)` - Dynamic size; releases unused memory.
- **Date**
  - `DATE`

> **Note:** These are the most commonly used types for practical exams.

---

### Constraints

- **Primary Key**: Unique, not null, numeric.
- **Foreign Key**: Connects two tables.
- **Unique**: Ensures unique values; allows null.
- **Check**: Validates conditions (e.g., `CHECK(age > 15)`).
- **Not Null**: Ensures the column must have data.

---

### Create Table

We use the following syntax to create a table:

```sql
CREATE TABLE <table_name>(
    column1 datatype constraint,
    column2 datatype constraint,
    ...
);
```

Example:

```sql
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

- Show table schema:

```sql
DESCRIBE users;
DESC users;
```

- Rename a table:

```sql
RENAME dept TO dept1;
```

- Delete a table:

```sql
DROP TABLE dept;
```

---

#### Alter Table

- **Add a Column**:

```sql
ALTER TABLE dept
ADD location VARCHAR2(20);
```

- **Add a Constraint**:

```sql
ALTER TABLE dept
ADD PRIMARY KEY(dno);
```

- **Modify a Column**:

```sql
ALTER TABLE dept
MODIFY dname VARCHAR2(20);
```

> **Note:** You can only increase a column's data type size if it contains data.

- **Drop a Column**:

```sql
ALTER TABLE dept
DROP COLUMN location;
```

- **Rename a Column**:

```sql
ALTER TABLE dept
RENAME COLUMN dno TO deptno;
```

---

### Insertion

- **Insert Data**:

```sql
INSERT INTO <table_name>(column_names)
VALUES(values);
```

Example:

```sql
INSERT INTO users (id, name, email, age)
VALUES (2, 'Ahmed Hassan', 'ahmed1@gmail.com', 16);
```

- **Update Data**:

```sql
UPDATE users
SET column_name = value
WHERE condition;
```

Example:

```sql
UPDATE users
SET address = 'Cairo'
WHERE id = 2;
```

- **Delete Data**:

```sql
DELETE FROM users
WHERE id = 2;
```

> **Caution:**
> `DELETE FROM users;` will remove all data from the table.

---

### SELECT

- Retrieve specific columns:

```sql
SELECT id, name FROM users;
```

- Retrieve all columns:

```sql
SELECT * FROM users;
```

- Aliases:

```sql
SELECT name AS username FROM users;
```

- Concatenation:

```sql
SELECT name || ' ' || email AS userdata FROM users;
```

---

### WHERE

- Relational Operators:

| Operator | Description                          |
|----------|--------------------------------------|
| `=`      | Equals                              |
| `>`      | Greater than                        |
| `>=`     | Greater than or equal               |
| `<`      | Less than                           |
| `<=`     | Less than or equal                  |
| `<>`, `!=` | Not equal                        |

Example:

```sql
SELECT name FROM users WHERE age > 20;
```

- Logical Operators:

| Operator | Description |
|----------|-------------|
| `AND`    | Both conditions must be true |
| `OR`     | At least one condition is true |
| `NOT`    | Negates the condition |

---

### ORDER BY

- Sort rows:

```sql
SELECT * FROM users ORDER BY salary ASC;
```

---

### Aggregate Functions

| Function | Description                     |
|----------|---------------------------------|
| `COUNT`  | Counts the rows                |
| `AVG`    | Calculates the average         |
| `SUM`    | Returns the sum of the values  |
| `MAX`    | Returns the maximum value      |
| `MIN`    | Returns the minimum value      |

Example:

```sql
SELECT MAX(salary) FROM users;
```

---

### GROUP BY

- Group data and use aggregate functions:

```sql
SELECT COUNT(name), address FROM users
GROUP BY address;
```

- Use `HAVING` to filter grouped data:

```sql
SELECT address, SUM(salary) FROM users
GROUP BY address
HAVING SUM(salary) > 4000;
```

---

### Foreign Key

1. Create a department table:

```sql
CREATE TABLE dept(
    deptno NUMBER PRIMARY KEY,
    deptname VARCHAR2(20) NOT NULL
);
```

2. Add a column to the users table:

```sql
ALTER TABLE users
ADD deptno NUMBER;
```

3. Set up the foreign key:

```sql
ALTER TABLE users
ADD FOREIGN KEY(deptno) REFERENCES dept(deptno);
```

---