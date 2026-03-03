# MySQL

---

## Day 1

### Database

> It is a structured collection of data.
>
> > That is organized so it can be easily accessed, managed, and updated.
>
> It is stored and managed using specialized software called  Database Management System (DBMS).
>
> Examples: MySQL, SQLite, etc

### DBMS

> DBMS is a software that allows us to interact with database.
> It is designed to manage large volumes of data efficiently and provide mechanisms for storing, retrieving, updating, and managing the data.
> Examples: Postgres, Oracle, etc

### SQL

> SQL (Structured Query Language) is a standarized language for managing relational database.
> Used to interact with various database system in order to  
> **insert, retrieve, update and delete** data.

### MySQL

> It is an open source *RDBMS* that uses *SQL* in order to access database using *SQL*.
> Examples: Microsoft SQL Server, Oracle Database, etc

### Installation

> Download and Install *MySQL*
> Download and Install VSCode with *MySQL* Extension from *Database Client*

### Coding Part

1. Show Database  
`Syntax: SHOW Databases;`
2. Create Database  
`Syntax: CREATE Database db_name;`
3. Drop/Delete Database  
`Syntax: DROP Database db_name;`
4. Using Database/Getting into Database  
`Syntax: USE db_name;`
5. Know which Database is currently in use  
`Syntax: SELECT DATABASE();`

---

## Day 2

Used previous 5 syntax to familarize myself with the syntax and examples to practice.

### Table

> Organized collection of data arranged in rows and columns.
> Used to store and organize data in a structured format.
> Enables us to search, retrieve and manipulate the data in easier way.  
> A table can contain different types of data.
> > Text, integer, floating point, etc  
>
> Example:
> |Name|Genre|Rating|
> |:---|:---|:---|
> |The Witcher 3 |RPG | 9.3/10 |
> |GTA V | Action-Adventure | 9.6/10 |
> |COD | Battle Royale | 8.7/10 |

### Data Types

> Simply the type of data that are stored in a table.
> It tells a database what kind of data can be stored in a *column* of a table.  
> Example:
>
> 1. A column with datatype of integer can only store whole numbers
>
> 2. A column with datatype of text can store letters, numbers and other characters.

### Creating a table

```sql
Example:

CREATE TABLE GAMES (
    name VARCHAR(50),
    ratings int
);
```

> It will create a table with the name GAME.  
> It will contain two columns *name* and *ratings*.  
> **name**: column will store variable character string with a maximum length of 50 characters.  
> **ratings**: column can store whole numbers.

```sql
Syntax:

CREATE TABLE table_name
(
    column_name data_type,
    ....
    ..
);
```

```sql
Example:

CREATE TABLE games
(
    name VARCHAR(50),
    release_year INT,
    ratings INT
);
```

### Fetching information about a Table

1. Display a list of all tables in a *database*  
`Syntax: SHOW TABLES;`
2. Display the columns of a table  
`Syntax: SHOW COLUMNS FROM table_name;`
3. Display/ Describe the structure of table  
`Syntax: DESC table_name;`  
DESC is short for DESCRIBE

4. Adding Default value

```sql
Syntax:

CREATE TABLE table_name
(
    column_name data_type DEFAULT 'default_value',
    ...,
    ..
);
```

```sql
Example:

CREATE TABLE game
(
    name VARCHAR(50) DEFAULT 'Anonymous',
    release_year INT DEFAULT 2026,
    ratings INT
);
```

5. Drop Delete a table  
`Syntax: Drop TABLE table_name;`

```sql
Example:

DROP TABLE game;
```

### Common Data Types used in MySQL

1. CHAR (*size*)

    > Used for **fixed length character** strings.  
    > When defining a column with CHAR datatype it is mandatory to specify a fixed length for the string.  
    > Can contain letters, numbers and special characters.  
    > Example: `CHAR (10)`  
    > > If characters less than 10 is filled in a column then the remaining spaces are filled to the limit size.

2. VARCHAR (*size*)

   > Used for **variable length characters** string.  
   > When you define a column with VARCHAR datatype, a maximum length for the string is needed to be specified.  
   > Can contain letters, numbers and special characters.  
   > Example: `VARCHAR (255)`  
   > > Only the required size is allocated as needed.

3. INT

   > Used to store **whole numbers** (integers) without decimal points.  
   > Example: `INT (255)`

4. DECIMAL

    > Used to store **exact numeric value**.  
    > Commonly used for monetary or other values where precision is required.  
    > It requires two parameters `DECIMAL (p,s)`  
    > > where,  
    > > - *p* specifies the total number of digits that can be stored (*precision*)  
    > > - *s* specifies the number of digits after the decimal point (*scale*).

5. DATE

   > Used to store a **date** value in the form of `YYYY-MM-DD`.  
   > Example: `2026-03-02`

6. TIME

    > Used to store a **time** value in the form of `HH:MM:SS`.  
    > Example `22:24:34`

7. DATETIME

    > Used to store both date and time informaton.  
    > It is in the form of `YYYY-MM-DD HH:MM:SS`.  
    > Example: `2026-03-02 22:24:34`

```sql
Example:

CREATE TABLE movies
(
    title VARCHAR(50),
    release_year INT,
    total_time TIME DEFAULT "02:18:23",
    rating DECIMAL,
    review CHAR(20),
    review_date DATE DEFAULT "2026-03-02"
);
```

---

## Day 3

### Inserting data labels and values in a table

```sql
Syntax:

INSERT INTO TABLE table_name (column1, column2, ..., columnN)
VALUES (data1, data2, ..., dataN);
```

```sql
Example:

INSERT INTO TABLE game (name, release_year, ratings)
VALUES ("The Witcher 3", 2015, 9);
```

> Datatypes should match for the column to insert data.  
> We can insert multiple values at once for multiple rows.

```sql
Syntax:
INSERT INTO TABLE table_name (column1, column2, ..., columnN)
VALUES (data1, data2,..., dataN),
       (data1, data2,..., dataN),
       (data1, data2,..., dataN);
```

```sql
Example:

INSERT INTO TABLE game (name, release_year, ratings)
VALUES ("The Witcher 3", 2015, 9),
       ("GTA V", 2013, 9);
```

### Select specific property from a table

```sql
Syntax:

SELECT PROPERTY FROM table_name;
```
> *PROPERTY* refers to the column of a table.  

```sql
Example:

SELECT name FROM game;
SELECT release_year FROM game;
```

> We can select multiple properties from a table.

```sql
Syntax:

SELECT PROPERTY_1, PROPERTY_2, ..., PROPERTY _N FROM table_name;
```

```sql
Example:

SELECT name, release_year FROM game;
SELECT name, release_year, ratings FROM game;
```

> We can even select all the properties from a table

```sql
Syntax:

SELECT * FROM table_name;
```

```sql
Example:

SELECT * FROM game;
```

### Primary Key

> It is a **unique identifier** for each record in a table.  
> It ensures that each row in a table is uniquely identifiable and helps maintain integrity of the data.  
> A primary key column can't have **NULL** value and must be **unique**.

```sql
Syntax:

CREATE TABLE table_name
(
    column_name1 data_type PRIMARY KEY,
    column_name2 data_type
);
```

```sql
Example:

CREATE TABLE students
(
    id INT PRIMARY KEY,
    name VARCHAR(50),
    admission_year INT,
    admitted_course VARCHAR(50)
);
```

> When inserting values in this table, we have to set the value for id each time.

```sql
Example:

INSERT INTO students (id, name, admision_year, admitted_course)
VALUES (1,"Ram Bahadur",2022, "BIT");
```

> To workaround for this there is a keyword `AUTO_INCREMENT` that will set the values automatically.

```sql
Syntax:

CREATE TABLE table_name 
(
    column_name data_type PRIMARY KEY AUTO_INCREMENT
);
```

```sql
Example:

CREATE TABLE students
(
    id INT PRIMARY KEY AUTO_INCREMENT,
    name VARCHAR(50),
    grade CHAR(2),
);

INSERT INTO students (name, grade)
VALUES ("Hari", 'A');
```

### Foreign Key

> It is a set of constraints that is used to establish relationship between tables.  
> A key that is a **primary key** in one table and is present in another table.  
> Creates a link between tables to maintain **referential integrity**.  
> A table with **foreign key** is called child table and the table with **primary key** is called parent or referenced table.  
> It prevents invalid data from being inserted into the foreign key column, as the value needs to also be present in parent table.

```sql
Syntax:

CREATE TABLE table_name_1
(
    column_name_1 data_type PRIMARY KEY
);

CREATE TABLE table_name_2
(
    column_name_1 data_type, 
    FOREIGN KEY (column_name_1)REFERENCES table_name_1 (column_name_1)
); 
```

```sql
Example:

-- Table 1
CREATE TABLE customers
(
    customer_id INT PRIMARY KEY AUTO_INCREMENT,
    customer_name VARCHAR(50)
);

-- Table 2
CREATE TABLE transactions
(
    transaction_id PRIMARY KEY AUTO_INCREMENT,
    transaction_amount DOUBLE,
    customer_id INT,
    FOREIGN KEY(customer_id) REFERENCES customer(customer_id)
);
```

### WHERE Clause

> It is used to **filter records** that meets a specified condition.  
> Typically used in *SELECT*, *UPDATE* and *DELETE* statements.  
> It specifies which specific rows to *UPDATE* or *DELETE*.

```sql
Syntax:

SELECT property_1, .., property_N
FROM table_name
WHERE conditions;
```

```sql
Example:

SELECT name
FROM game
WHERE release_year < 2025;
```

### Aliases

> It is used to give a *column* or *table* a temporary name.  
> This temporary name only exist for the duration of that query.

```sql
Syntax:

SELECT column_name AS alias_name
FROM table_name;
```

```sql
Example:

SELECT name AS game_title 
FROM game;
```

### Update data in a table

> It is used to update or modify one or more records in a table.

```sql
Syntax:

UPDATE table_name
SET column_1 = value_1, column_2 = value_2, ..., column_N = value_N
WHERE condition;
```

```sql
Example:

UPDATE students
SET grade = "B"
WHERE id = 1;
```

> Always keep in mind to put `WHERE` clause when using `UPDATE` keyword.
> >
> If `WHERE` clause isn't used then all the values for that selected column will be updated.

### Delete data in a table

> **Delete** statement is used to delete existing records from a table.

```sql
Syntax:

DELETE 
FROM table_name
WHERE conditions;
```

```sql
Example:

DELETE
FROM users
WHERE status = "inactive";
```

> Always keep in mind to put `WHERE` clause when using `DELETE` keyword.
>
> If `WHERE` clause isn't used then all the data in the table will be deleted.

---
