# JDBC with CRUD(Create,Read,Update,Insert)

## Table of Contents
1. [Introduction to JDBC](#introduction-to-jdbc)
2. [Why Use PreparedStatement?](#why-use-preparedstatement)
3. [CRUD Operations with PreparedStatement](#crud-operations-with-preparedstatement)
    - [Create (INSERT)](#create-insert)
    - [Read (SELECT)](#read-select)
    - [Update (UPDATE)](#update-update)
    - [Delete (DELETE)](#delete-delete)
4. [Benefits of Using PreparedStatement](#benefits-of-using-preparedstatement)
5. [Dburl Syntax Example](#dburl-syntax-example)
---

## Introduction to JDBC
JDBC (Java Database Connectivity) is an API in Java that allows you to interact with databases.



## Why Use PreparedStatement?
- `PreparedStatement` is a subclass of `Statement` used for executing parameterized SQL queries. 
- Unlike `Statement`, `PreparedStatement` helps protect against SQL injection by allowing you to set parameters in a query safely.



## CRUD Operations with PreparedStatement
### Create (INSERT)
- to make it easier just import all from sql : import java.sql.*;
```java
String insertSQL = "INSERT INTO users (username, password, email) VALUES (?, ?, ?)";
try (Connection conn = DriverManager.getConnection(DB_URL, USER, PASS);
     PreparedStatement pstmt = conn.prepareStatement(insertSQL, Statement.RETURN_GENERATED_KEYS)) {  // this is example of the try with resources
    // Set the values ? insert sql
    pstmt.setString(1, "Eunchae");
    pstmt.setString(2, "lesserafim");
    pstmt.setString(3, "Eunchae@example.com");
    pstmt.executeUpdate(); // Execute the INSERT statement
    // Retrieve the generated keys (e.g., auto-increment ID)
    ResultSet generatedKeys = pstmt.getGeneratedKeys();
        if (generatedKeys.next()) {
            long generatedId = generatedKeys.getLong(1); // Assuming the generated key is a long type
            System.out.println("Inserted record ID: " + generatedId);
        }
}
```
### Read (SELECT)
```java
String selectSQL = "SELECT * FROM users WHERE username = ?";
try (Connection conn = DriverManager.getConnection(DB_URL, USER, PASS);
     PreparedStatement pstmt = conn.prepareStatement(selectSQL)) {
    pstmt.setString(1, "Eunchae");
    ResultSet rs = pstmt.executeQuery();
    while (rs.next()) {// Process data while they have it 
        rs.getString("username");
        rs.getString("email");
    }
}
```
### Update (UPDATE)
```java
String deleteSQL = "DELETE FROM users WHERE username = ?";
try (Connection conn = DriverManager.getConnection(DB_URL, USER, PASS);
     PreparedStatement pstmt = conn.prepareStatement(deleteSQL)) {
    pstmt.setString(1, "johndoe");
    pstmt.executeUpdate();
}
```




## Dburl Syntax Example
```java
//sqlite
String DB_URL = "jdbc:sqlite:/path/to/your/database.db";

//PostgreSql
String DB_URL = "jdbc:postgresql://localhost:5432/your_database";

//Mysql
String DB_URL = "jdbc:mysql://localhost:3306/your_database";
```