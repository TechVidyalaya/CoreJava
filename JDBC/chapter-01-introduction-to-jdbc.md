# Chapter 01: Introduction to JDBC

## 📖 Overview

**JDBC (Java Database Connectivity)** is the standard Java API used to connect Java applications with relational databases. It enables applications to execute SQL queries, retrieve data, update records, and manage database transactions.

JDBC acts as a bridge between Java applications and databases like **MySQL**, **Oracle**, **PostgreSQL**, and **SQL Server**.

---

# 🎯 Learning Objectives

After completing this chapter, you will be able to:

- Understand JDBC
- Learn why JDBC is used
- Explore JDBC features
- Understand JDBC components
- Learn the JDBC workflow
- Identify real-world use cases

---

# What is JDBC?

JDBC (Java Database Connectivity) is a collection of Java classes and interfaces that allow Java programs to communicate with databases.

Using JDBC, you can:

- Connect to a database
- Execute SQL statements
- Retrieve data
- Insert, update, and delete records
- Manage transactions

---

# Why JDBC?

Without JDBC, every database would require its own Java API.

JDBC provides a **common standard API** that works with different databases using their respective JDBC drivers.

Benefits:

- Database independent
- Standard Java API
- Supports SQL
- Portable across platforms
- Easy integration with enterprise applications

---

# JDBC Architecture

```text
Java Application
        │
        ▼
     JDBC API
        │
        ▼
   JDBC Driver
        │
        ▼
    Database
```

---

# JDBC Components

| Component | Purpose |
|-----------|---------|
| JDBC API | Standard Java interfaces |
| JDBC Driver | Connects Java to the database |
| DriverManager | Manages database drivers |
| Connection | Represents a database connection |
| Statement | Executes SQL queries |
| ResultSet | Stores query results |

---

# Supported Databases

JDBC works with many relational databases, including:

- MySQL
- Oracle Database
- PostgreSQL
- Microsoft SQL Server
- MariaDB
- SQLite

---

# JDBC Driver

A JDBC Driver is a software component that translates Java JDBC calls into database-specific commands.

Example:

```text
Java Program

↓

JDBC Driver

↓

MySQL Database
```

---

# Basic JDBC Workflow

```text
Load JDBC Driver
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
Process Result
        │
        ▼
Close Resources
```

---

# Simple JDBC Code

```java
Connection connection =
    DriverManager.getConnection(
        url,
        username,
        password
    );
```

This creates a connection between the Java application and the database.

---

# Common JDBC Interfaces

| Interface | Description |
|-----------|-------------|
| `Connection` | Represents a database connection |
| `Statement` | Executes SQL statements |
| `PreparedStatement` | Executes parameterized SQL queries |
| `CallableStatement` | Executes stored procedures |
| `ResultSet` | Stores query results |

---

# Advantages of JDBC

- Standard API
- Platform independent
- Supports transactions
- Secure with `PreparedStatement`
- Easy integration with Java applications
- Supports multiple databases

---

# Limitations of JDBC

- Requires SQL knowledge
- Manual resource management
- More boilerplate code
- Object-relational mapping is not supported directly

Frameworks like **Hibernate** and **Spring Data JPA** simplify many of these tasks.

---

# Real-World Applications

JDBC is commonly used in:

- Banking systems
- E-commerce applications
- Student Management Systems
- Hospital Management Systems
- Inventory Management
- ERP and CRM applications

---

# Common Mistakes

### Not Closing Resources

Leaving connections open can lead to resource leaks.

Always close:

- ResultSet
- Statement
- Connection

---

### Using String Concatenation for SQL

Avoid:

```java
String sql =
    "SELECT * FROM users WHERE id=" + id;
```

Prefer:

```java
PreparedStatement
```

to prevent SQL Injection.

---

### Ignoring Exceptions

Always handle database exceptions using `try-catch` or **try-with-resources**.

---

# Best Practices

- Use `PreparedStatement` instead of `Statement`.
- Close all JDBC resources properly.
- Handle SQL exceptions gracefully.
- Store database credentials securely.
- Use connection pooling for enterprise applications.

---

# Summary

In this chapter, you learned:

- What JDBC is
- Why JDBC is used
- JDBC architecture
- JDBC components
- JDBC workflow
- Advantages and limitations
- Best practices

---

# Quick Revision

- JDBC stands for **Java Database Connectivity**.
- JDBC connects Java applications to relational databases.
- JDBC uses database-specific drivers.
- `Connection` represents a database connection.
- `Statement` executes SQL queries.
- `ResultSet` stores query results.
- Always close JDBC resources.

---

# Practice Questions

### Basic

1. What is JDBC?
2. Why is JDBC used?
3. What is a JDBC Driver?
4. What is the purpose of `Connection`?
5. What is `ResultSet`?

### Intermediate

6. Explain the JDBC architecture.
7. Differentiate `Statement` and `PreparedStatement`.
8. What are the advantages of JDBC?

### Interview Questions

1. Explain JDBC with its architecture.
2. What are the core JDBC interfaces?
3. Why is `PreparedStatement` preferred over `Statement`?
4. What are the limitations of JDBC?
5. How does JDBC communicate with different databases?

---

# Hands-on Exercise

Create a simple **JDBC Demo** application that:

1. Install MySQL and MySQL Workbench.
2. Create a database named `student_db`.
3. Add a table named `students`.
4. Add the MySQL JDBC Driver to your Java project.
5. Write a Java program to establish a database connection.
6. Display a success message if the connection is established.
7. Handle exceptions properly.
8. Close the database connection before exiting the application.
