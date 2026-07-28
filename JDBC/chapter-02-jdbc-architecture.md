# Chapter 02: JDBC Architecture

## 📖 Overview

The **JDBC Architecture** defines how a Java application communicates with a relational database. It consists of the JDBC API, JDBC Driver, DriverManager, and the database.

Understanding this architecture helps developers write efficient and database-independent applications.

---

# 🎯 Learning Objectives

After completing this chapter, you will be able to:

- Understand JDBC Architecture
- Learn the role of each JDBC component
- Understand the JDBC workflow
- Explore different JDBC driver types
- Learn how Java communicates with databases

---

# JDBC Architecture

```text
+----------------------+
|  Java Application    |
+----------------------+
           │
           ▼
+----------------------+
|      JDBC API        |
+----------------------+
           │
           ▼
+----------------------+
|     JDBC Driver      |
+----------------------+
           │
           ▼
+----------------------+
| Relational Database  |
+----------------------+
```

---

# JDBC Components

## Java Application

The Java application contains business logic and uses the JDBC API to interact with a database.

Example:

```java
public class StudentApp {

    public static void main(String[] args) {

    }
}
```

---

## JDBC API

The JDBC API provides standard interfaces for database operations.

Common interfaces include:

- Connection
- Statement
- PreparedStatement
- CallableStatement
- ResultSet

The API remains the same regardless of the database.

---

## JDBC Driver

A JDBC Driver converts JDBC API calls into database-specific commands.

Example:

```text
JDBC API

↓

MySQL JDBC Driver

↓

MySQL Database
```

Each database has its own JDBC driver.

---

## Database

The database stores and manages data.

Examples:

- MySQL
- Oracle
- PostgreSQL
- SQL Server
- MariaDB

---

# JDBC Workflow

```text
Java Application
        │
        ▼
Load Driver
        │
        ▼
Create Connection
        │
        ▼
Create Statement
        │
        ▼
Execute SQL
        │
        ▼
Receive ResultSet
        │
        ▼
Close Resources
```

---

# DriverManager

`DriverManager` manages JDBC drivers and establishes database connections.

Example:

```java
Connection connection =
    DriverManager.getConnection(
        url,
        username,
        password
    );
```

---

# Connection

The `Connection` interface represents an active connection with the database.

Example:

```java
Connection connection =
    DriverManager.getConnection(
        url,
        user,
        password
);
```

A connection must be established before executing SQL queries.

---

# Statement

The `Statement` interface executes simple SQL queries.

Example:

```java
Statement statement =
    connection.createStatement();
```

---

# PreparedStatement

`PreparedStatement` executes parameterized SQL queries.

Example:

```java
PreparedStatement ps =
    connection.prepareStatement(
        "SELECT * FROM students WHERE id=?"
    );
```

Advantages:

- Faster execution
- Prevents SQL Injection
- Easier parameter handling

---

# ResultSet

A `ResultSet` stores the data returned by a query.

Example:

```java
ResultSet rs =
    statement.executeQuery(
        "SELECT * FROM students"
    );
```

Reading data:

```java
while (rs.next()) {

    System.out.println(
        rs.getString("name")
    );
}
```

---

# Types of JDBC Drivers

Java supports four types of JDBC drivers.

| Type | Description |
|------|-------------|
| Type 1 | JDBC-ODBC Bridge Driver (Obsolete) |
| Type 2 | Native API Driver |
| Type 3 | Network Protocol Driver |
| Type 4 | Thin Driver (Pure Java) |

---

# Type 4 Driver

The **Type 4 Driver** is the most commonly used today.

Advantages:

- Pure Java
- High performance
- Easy to configure
- No native libraries required

Example:

```
Java Application

↓

MySQL Connector/J

↓

MySQL Database
```

---

# JDBC Architecture Workflow

```text
Java Program
      │
      ▼
DriverManager
      │
      ▼
Connection
      │
      ▼
Statement /
PreparedStatement
      │
      ▼
Database
      │
      ▼
ResultSet
```

---

# Real-World Applications

JDBC Architecture is used in:

- Banking applications
- E-commerce systems
- Student portals
- Hospital Management Systems
- ERP software
- Spring Boot applications

---

# Common Mistakes

### Not Closing Connections

Leaving database connections open can exhaust available connections.

Always close:

- ResultSet
- Statement
- Connection

---

### Using Statement for User Input

Avoid:

```java
Statement
```

Use:

```java
PreparedStatement
```

to improve security.

---

### Hardcoding Database Credentials

Avoid storing usernames and passwords directly in source code.

Use:

- Configuration files
- Environment variables
- Secret management tools

---

# Best Practices

- Use Type 4 JDBC drivers.
- Prefer `PreparedStatement` over `Statement`.
- Use try-with-resources for automatic resource management.
- Keep database credentials secure.
- Close JDBC resources in the correct order.

---

# Summary

In this chapter, you learned:

- JDBC Architecture
- JDBC components
- DriverManager
- Connection
- Statement
- PreparedStatement
- ResultSet
- JDBC driver types
- Best practices

---

# Quick Revision

- JDBC Architecture connects Java applications to databases.
- DriverManager establishes database connections.
- Connection represents an active database connection.
- Statement executes SQL queries.
- PreparedStatement executes parameterized SQL.
- ResultSet stores query results.
- Type 4 drivers are the preferred choice.

---

# Practice Questions

### Basic

1. What is JDBC Architecture?
2. What is the role of DriverManager?
3. What does the Connection interface represent?
4. What is a ResultSet?
5. Which JDBC driver type is commonly used today?

### Intermediate

6. Explain the JDBC workflow.
7. Differentiate Statement and PreparedStatement.
8. Explain the four types of JDBC drivers.

### Interview Questions

1. Explain JDBC Architecture with a diagram.
2. What is the role of the JDBC Driver?
3. Why is the Type 4 JDBC Driver preferred?
4. How does DriverManager establish a connection?
5. Describe the lifecycle of a JDBC request.

---

# Hands-on Exercise

Create a **JDBC Architecture Demo** application that:

1. Install the MySQL JDBC Driver (Connector/J).
2. Create a Java project and add the driver.
3. Create a database named `student_db`.
4. Establish a connection using `DriverManager`.
5. Create a `Statement` and execute a simple query.
6. Retrieve data using `ResultSet`.
7. Display the retrieved records.
8. Close all JDBC resources using try-with-resources.
