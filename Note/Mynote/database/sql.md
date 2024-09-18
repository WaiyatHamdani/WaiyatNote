# SQL Notes

## Table of Contents
1. [DML (Data Manipulation Language)](#dml-data-manipulation-language)
2. [DDL (Data Definition Language)](#ddl-data-definition-language)
3. [DCL (Data Control Language)](#dcl-data-control-language)
4. [TCL (Transaction Control Language)](#tcl-transaction-control-language)
5. [DQL (Data Query Language)](#dql-data-query-language)
6. [Joins](#joins)
7. [Union](#union)
8. [Primary Key Foreign Key](#primary-key-foreign-key)
9. [Aggregation](#aggregation)
10. [Scalar Functions](#scalar-functions)
11. [Other SQL Commands](#other-sql-commands)
12. [Procedures](#procedures)
---


## DML (Data Manipulation Language)
DML commands are used to manage data within database tables.

- **INSERT:** Adds new records to a table.
    ```sql
    INSERT INTO Idols (Name, Age, Group)
    VALUES ('Yuqi', 23, '(G)I-DLE');
    ```

- **UPDATE:** Modifies existing records in a table.
    ```sql
    UPDATE Idols
    SET Age = 24
    WHERE Name = 'Yuqi';
    ```

- **DELETE:** Removes records from a table.
    ```sql
    DELETE FROM Idols
    WHERE Name = 'Yuqi';
    ```



## DDL (Data Definition Language)
DDL commands define and manage database structures like tables and indexes.

- **CREATE:** Creates new database objects like tables, indexes, etc.
    ```sql
    CREATE TABLE Idols (
        ID INT PRIMARY KEY,
        Name VARCHAR(50),
        Age INT,
        Group VARCHAR(50)
    );
    ```

- **ALTER:** Modifies an existing database object.
    ```sql
    ALTER TABLE Idols
    ADD COLUMN Position VARCHAR(50);
    ```

- **DROP:** Deletes an existing database object.
    ```sql
    DROP TABLE Idols;
    ```

- **TRUNCATE:** Removes all records from a table but keeps its structure.
    ```sql
    TRUNCATE TABLE Idols;
    ```



## DCL (Data Control Language)
DCL commands control access to data in the database.

- **GRANT:** Provides specific privileges to users.
    ```sql
    GRANT SELECT, INSERT ON Idols TO 'user1';
    ```

- **REVOKE:** Removes specific privileges from users.
    ```sql
    REVOKE INSERT ON Idols FROM 'user1';
    ```



## TCL (Transaction Control Language)
TCL commands manage transactions within a database.

- **COMMIT:** Saves the changes made during the current transaction.
    ```sql
    COMMIT;
    ```

- **ROLLBACK:** Reverts the changes made during the current transaction.
    ```sql
    ROLLBACK;
    ```

- **SAVEPOINT:** Sets a savepoint within a transaction.
    ```sql
    SAVEPOINT sp1;
    ```



## DQL (Data Query Language)
DQL commands are used to query the database.

- **SELECT:** Retrieves data from one or more tables.
    ```sql
    SELECT Name, Age
    FROM Idols
    WHERE Group = '(G)I-DLE';
    ```



## Joins
Joins are used to combine rows from two or more tables based on a related column:
- **INNER JOIN:** Returns records with matching values in both tables.
    ```sql
    SELECT Idols.Name, Groups.GroupName
    FROM Idols
    INNER JOIN Groups ON Idols.GroupID = Groups.ID;
    ```

- **LEFT JOIN:** Returns all records from the left table and the matched records from the right table.
    ```sql
    SELECT Idols.Name, Groups.GroupName
    FROM Idols
    LEFT JOIN Groups ON Idols.GroupID = Groups.ID;
    ```

- **RIGHT JOIN:** Returns all records from the right table and the matched records from the left table.
    ```sql
    SELECT Idols.Name, Groups.GroupName
    FROM Idols
    RIGHT JOIN Groups ON Idols.GroupID = Groups.ID;
    ```

- **FULL JOIN:** Returns all records when there is a match in either table.
    ```sql
    SELECT Idols.Name, Groups.GroupName
    FROM Idols
    FULL JOIN Groups ON Idols.GroupID = Groups.ID;
    ```




## Union
- **UNION:** Combines the result sets of two or more `SELECT` statements (removes duplicates).
    ```sql
    SELECT Name FROM Idols
    UNION
    SELECT GroupName FROM Groups;
    ```

- **UNION ALL:** Combines the result sets of two or more `SELECT` statements (includes duplicates).
    ```sql
    SELECT Name FROM Idols
    UNION ALL
    SELECT GroupName FROM Groups;
    ```




## Primary Key Foreign Key
```sql
CREATE TABLE Groups (
    GroupID INT PRIMARY KEY,
    GroupName VARCHAR(50)
);

CREATE TABLE Idols (
    IdolID INT PRIMARY KEY, -- Primary Key
    Name VARCHAR(50),
    Age INT,
    GroupID INT,
    FOREIGN KEY (GroupID) REFERENCES Groups(GroupID)  -- Foreign Key
);
```



## Aggregation
Aggregation in SQL refers to performing a calculation on a set of values to return a single scalar value:
- SUM, AVG, COUNT, MIN, and MAX.
example:
```sql
-- Calculate the average age of idols
SELECT AVG(Age) AS AverageAge
FROM Idols;

-- Count the number of idols in a group
SELECT Group, COUNT(*) AS NumberOfIdols
FROM Idols
GROUP BY Group;

-- Sum of idol salaries
SELECT SUM(Salary) AS TotalSalary
FROM Idols;
```



## Scalar Functions
Scalar Functions operate on a single value and return a single value:
- UPPER() / LOWER(),LEN(),ROUND(),GETDATE()
example:
```sql
-- Convert idol names to uppercase
SELECT UPPER(Name) AS UpperCaseName
FROM Idols;

-- Round the salary to 2 decimal places
SELECT Name, ROUND(Salary, 2) AS RoundedSalary
FROM Idols;

-- Get the length of each group's name
SELECT GroupName, LEN(GroupName) AS NameLength
FROM Groups;
```



## Other SQL Commands
- **SET:** Changes the value of a variable.
    ```sql
    SET @idolName = 'Yuqi';
    ```

- **CREATE INDEX:** Improves the speed of data retrieval.
    ```sql
    CREATE INDEX idx_group ON Idols(Group);
    ```

- **DROP INDEX:** Deletes an existing index.
    ```sql
    DROP INDEX idx_group ON Idols;
    ```

- **CREATE VIEW:** Creates a virtual table based on a `SELECT` statement.
    ```sql
    CREATE VIEW IdolView AS
    SELECT Name, Group FROM Idols;
    ```

- **CALL FUNCTION:** Calls a user-defined function.
    ```sql
    SELECT GetIdolAge('Yuqi');
    ```




## Procedures
Procedures are stored routines in SQL that allow you to encapsulate logic for repetitive tasks.

- **CREATE PROCEDURE:** Defines a new stored procedure.
    ```sql
    CREATE PROCEDURE AddNewIdol(IN idolName VARCHAR(50), IN idolAge INT, IN idolGroup VARCHAR(50))
    BEGIN
        INSERT INTO Idols (Name, Age, Group)
        VALUES (idolName, idolAge, idolGroup);
    END;
    ```

- **CALL PROCEDURE:** Executes a stored procedure.
    ```sql
    CALL AddNewIdol('Soyeon', 25, '(G)I-DLE');
    ```





