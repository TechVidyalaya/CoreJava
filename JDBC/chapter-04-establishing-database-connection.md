# Chapter 04: Establishing Database Connection

## 📖 Overview

A **database connection** is the first step in every JDBC application. Before executing SQL queries, Java must establish a connection with the database using the JDBC API.

This chapter explains how to create, use, and close database connections properly.

---

# 🎯 Learning Objectives

After completing this chapter, you will be able to:

- Understand database connections
- Use `DriverManager`
- Create a `Connection` object
- Configure JDBC URLs
- Close database resources
- Follow connection best practices

---

# What is a Database Connection?

A database connection is a communication link between a Java application and a database server.

Once connected, the application can:

- Execute SQL queries
- Insert records
- Update data
- Delete records
- Retrieve data

---

# JDBC Connection Flow

```text
Java Application
        │
        ▼
DriverManager
        │
        ▼
Connection
        │
        ▼
Database
```

---

# DriverManager

`DriverManager` is responsible for establishing database connections.

Syntax:

```java
Connection connection =
    DriverManager.getConnection(
        url,
        username,
        password
    );
```

---

# JDBC URL Format

General format:

```text
jdbc:database://host:port/database_name
```

Example (MySQL):

```text
jdbc:mysql://localhost:3306/student_db
```

---

# Connection Parameters

| Parameter | Description |
|-----------|-------------|
| URL | Database location |
| Username | Database user |
| Password | User password |

Example:

```java
String url =
    "jdbc:mysql://localhost:3306/student_db";

String username = "root";

String password = "password";
```

---

# Creating a Connection

```java
import java.sql.*;

public class ConnectionDemo {

    public static void main(String[] args)
            throws SQLException {

        String url =
            "jdbc:mysql://localhost:3306/student_db";

        String username = "root";

        String password = "password";

        Connection connection =
            DriverManager.getConnection(
                url,
                username,
                password
            );

        System.out.println(
            "Connected Successfully!"
        );

        connection.close();
    }
}
```

---

# Checking Connection Status

```java
if (connection != null) {

    System.out.println(
        "Connection Established"
    );
}
```

---

# Closing the Connection

Always close the connection after use.

```java
connection.close();
```

Closing the connection releases database resources.

---

# Using Try-With-Resources

Recommended approach:

```java
try (Connection connection =
         DriverManager.getConnection(
             url,
             username,
             password)) {

    System.out.println(
        "Connected Successfully!"
    );

}
catch (SQLException e) {

    e.printStackTrace();
}
```

Resources are closed automatically.

---

# Common Connection Errors

### Invalid URL

```text
No suitable driver found
```

Cause:

- Incorrect JDBC URL
- Missing driver

---

### Wrong Username or Password

```text
Access denied for user
```

Verify database credentials.

---

### Database Not Running

```text
Communications link failure
```

Ensure the database server is running.

---

### Unknown Database

```text
Unknown database 'student_db'
```

Create the database before connecting.

---

# Connection Lifecycle

```text
Load Driver
      │
      ▼
Create Connection
      │
      ▼
Execute Queries
      │
      ▼
Process Results
      │
      ▼
Close Connection
```

---

# Real-World Applications

Database connections are used in:

- Banking systems
- Hospital Management Systems
- Student portals
- Inventory systems
- E-commerce applications
- Spring Boot applications

---

# Common Mistakes

### Hardcoding Credentials

Avoid:

```java
String password =
    "password";
```

Store credentials in:

- Properties files
- Environment variables
- Configuration servers

---

### Not Closing Connections

Leaving connections open can exhaust database resources.

Always close connections or use try-with-resources.

---

### Opening Multiple Unnecessary Connections

Reuse connections where appropriate or use **connection pooling** in enterprise applications.

---

# Best Practices

- Use try-with-resources.
- Validate database credentials.
- Keep JDBC URLs configurable.
- Close resources immediately after use.
- Use connection pooling for production applications.
- Never hardcode sensitive credentials.

---

# Summary

In this chapter, you learned:

- Database connections
- DriverManager
- JDBC URL
- Connection object
- Closing connections
- Try-with-resources
- Common connection errors
- Best practices

---

# Quick Revision

- `DriverManager` creates database connections.
- `Connection` represents an active database connection.
- JDBC URLs specify the database location.
- Always close connections after use.
- Prefer try-with-resources.
- Store credentials securely.
- Use connection pooling in production.

---

# Practice Questions

### Basic

1. What is a database connection?
2. What is the role of `DriverManager`?
3. What is the purpose of the `Connection` interface?
4. What is the format of a JDBC URL?
5. Why should connections be closed?

### Intermediate

6. Explain the connection lifecycle.
7. Why is try-with-resources preferred?
8. What causes the "Access denied for user" error?

### Interview Questions

1. Explain how a JDBC connection is established.
2. What parameters are required by `DriverManager.getConnection()`?
3. Why should database credentials not be hardcoded?
4. What are common JDBC connection errors and how do you resolve them?
5. Why is connection pooling preferred over creating new connections repeatedly?

---

# Hands-on Exercise

Create a **Database Connection Tester** that:

1. Create a `student_db` database.
2. Configure the JDBC URL.
3. Establish a connection using `DriverManager`.
4. Print a success message if the connection is established.
5. Handle connection failures using `try-catch`.
6. Use try-with-resources to close the connection automatically.
7. Test the application with incorrect credentials and observe the error.
8. Modify the application to read database credentials from a properties file.
