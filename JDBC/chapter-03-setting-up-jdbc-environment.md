# Chapter 03: Setting Up JDBC Environment

## 📖 Overview

Before working with JDBC, you need to set up the development environment by installing a database, adding the JDBC driver, and configuring your Java project.

In this chapter, you'll configure **MySQL** with Java and establish everything required for JDBC development.

---

# 🎯 Learning Objectives

After completing this chapter, you will be able to:

- Install MySQL Server
- Install MySQL Workbench
- Download the MySQL JDBC Driver
- Configure a Java project
- Create a database
- Verify the JDBC setup

---

# Prerequisites

Ensure the following software is installed:

- JDK 17 or later
- IntelliJ IDEA / Eclipse / VS Code
- MySQL Server
- MySQL Workbench

---

# Install MySQL

Download and install:

- MySQL Server
- MySQL Workbench

During installation:

- Set a root password
- Keep the default port **3306**
- Start the MySQL service

---

# Verify MySQL Installation

Open MySQL Workbench and connect using:

```text
Host      : localhost
Port      : 3306
Username  : root
Password  : ********
```

If the connection is successful, the setup is complete.

---

# Create a Database

Execute the following SQL:

```sql
CREATE DATABASE student_db;
```

Verify:

```sql
SHOW DATABASES;
```

Output:

```text
information_schema

mysql

performance_schema

student_db
```

---

# Use the Database

```sql
USE student_db;
```

---

# Create a Table

```sql
CREATE TABLE students (

    id INT PRIMARY KEY,

    name VARCHAR(100),

    course VARCHAR(100),

    marks INT
);
```

Verify:

```sql
SHOW TABLES;
```

---

# Download MySQL JDBC Driver

Download **MySQL Connector/J**.

Driver File:

```text
mysql-connector-j-x.x.x.jar
```

Add this JAR file to your Java project's libraries.

---

# Add Driver to IntelliJ IDEA

Steps:

1. Right-click the project.
2. Open **Project Structure**.
3. Select **Libraries**.
4. Click **+**.
5. Choose the MySQL Connector JAR.
6. Apply the changes.

---

# Add Driver Using Maven

If using Maven, add the dependency:

```xml
<dependency>
    <groupId>com.mysql</groupId>
    <artifactId>mysql-connector-j</artifactId>
    <version>9.4.0</version>
</dependency>
```

---

# Add Driver Using Gradle

```gradle
implementation 'com.mysql:mysql-connector-j:9.4.0'
```

---

# Database Connection Details

Typical configuration:

```text
URL

jdbc:mysql://localhost:3306/student_db

Username

root

Password

********
```

---

# Loading the Driver

Modern JDBC drivers are automatically loaded.

Older approach:

```java
Class.forName(
    "com.mysql.cj.jdbc.Driver"
);
```

This is generally unnecessary with JDBC 4.0+.

---

# Test Database Connection

```java
import java.sql.*;

public class TestConnection {

    public static void main(String[] args)
            throws Exception {

        String url =
            "jdbc:mysql://localhost:3306/student_db";

        String user = "root";

        String password = "password";

        Connection connection =
            DriverManager.getConnection(
                url,
                user,
                password
            );

        System.out.println(
            "Database Connected!"
        );

        connection.close();
    }
}
```

---

# Expected Output

```text
Database Connected!
```

---

# Project Structure

```text
JDBCDemo
│
├── src
│    └── TestConnection.java
│
├── pom.xml (Maven)
│
└── mysql-connector-j.jar
```

---

# Environment Setup Workflow

```text
Install JDK
      │
      ▼
Install MySQL
      │
      ▼
Create Database
      │
      ▼
Add JDBC Driver
      │
      ▼
Write Java Program
      │
      ▼
Test Connection
```

---

# Real-World Applications

This setup is used for:

- Spring Boot applications
- Banking systems
- Student portals
- E-commerce platforms
- Inventory systems
- Enterprise applications

---

# Common Mistakes

### Wrong Database URL

Incorrect:

```text
jdbc:mysql://localhost/student
```

Correct:

```text
jdbc:mysql://localhost:3306/student_db
```

---

### Missing JDBC Driver

If the JDBC driver is not added, the application cannot establish a database connection.

---

### Incorrect Credentials

Using an invalid username or password results in:

```text
Access denied for user
```

---

### Forgetting to Close Connections

Always close the database connection after use to avoid resource leaks.

---

# Best Practices

- Use Maven or Gradle for dependency management.
- Keep database credentials in configuration files.
- Use strong passwords.
- Never hardcode production credentials.
- Test the database connection before writing business logic.
- Use try-with-resources for automatic resource cleanup.

---

# Summary

In this chapter, you learned:

- Installing MySQL
- Creating a database
- Creating tables
- Adding the JDBC Driver
- Configuring Java projects
- Testing database connections
- Environment setup best practices

---

# Quick Revision

- Install MySQL Server and Workbench.
- Create the `student_db` database.
- Add the MySQL JDBC Driver.
- Configure the JDBC URL.
- Use `DriverManager.getConnection()` to connect.
- Modern JDBC drivers are loaded automatically.
- Always close database resources.

---

# Practice Questions

### Basic

1. What software is required for JDBC development?
2. What is the default MySQL port?
3. What is the JDBC URL?
4. Why is the JDBC driver required?
5. What does `DriverManager.getConnection()` do?

### Intermediate

6. How do you add the MySQL driver using Maven?
7. Why is `Class.forName()` generally unnecessary in modern JDBC?
8. How do you verify that the database connection is successful?

### Interview Questions

1. Explain how to set up a JDBC development environment.
2. What is the role of the MySQL Connector/J driver?
3. How do you configure JDBC in a Maven project?
4. What are common causes of database connection failures?
5. What best practices should be followed when configuring JDBC applications?

---

# Hands-on Exercise

Create a **JDBC Environment Setup** project that:

1. Install MySQL Server and MySQL Workbench.
2. Create a database named `student_db`.
3. Create a `students` table.
4. Add the MySQL Connector/J dependency using Maven or Gradle.
5. Write a Java program to connect to the database.
6. Print **"Database Connected Successfully!"** if the connection succeeds.
7. Close the connection using try-with-resources.
8. Verify the setup by running the application successfully.
