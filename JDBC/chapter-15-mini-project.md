# Chapter 15: Mini Project – Student Management System

## 📖 Overview

In this chapter, you will build a **Student Management System** using JDBC. This project combines all the concepts learned throughout the module, including database connectivity, CRUD operations, transactions, exception handling, and connection pooling.

This project serves as an excellent portfolio project for beginners.

---

# 🎯 Learning Objectives

After completing this chapter, you will be able to:

- Connect Java with MySQL
- Perform CRUD operations
- Use `PreparedStatement`
- Handle exceptions
- Use transactions
- Organise code using the DAO pattern
- Build a real-world JDBC application

---

# Project Features

The application should support:

- Add Student
- View All Students
- Search Student by ID
- Update Student
- Delete Student
- Exit Application

---

# Technologies Used

| Technology | Purpose |
|------------|---------|
| Java | Programming Language |
| JDBC | Database Connectivity |
| MySQL | Database |
| HikariCP | Connection Pooling |
| IntelliJ IDEA / Eclipse | IDE |

---

# Database Design

Database:

```sql
CREATE DATABASE student_db;
```

Table:

```sql
CREATE TABLE students (

    id INT PRIMARY KEY,

    name VARCHAR(100),

    course VARCHAR(100),

    marks INT
);
```

---

# Recommended Project Structure

```text
StudentManagement/
│
├── config/
│   └── DBConfig.java
│
├── dao/
│   └── StudentDAO.java
│
├── entity/
│   └── Student.java
│
├── service/
│   └── StudentService.java
│
├── util/
│   └── DBUtil.java
│
└── Main.java
```

---

# Student Entity

```java
public class Student {

    private int id;
    private String name;
    private String course;
    private int marks;

}
```

---

# DAO Responsibilities

The `StudentDAO` class should provide methods such as:

```java
addStudent()

getAllStudents()

getStudentById()

updateStudent()

deleteStudent()
```

The DAO contains all database-related code.

---

# Application Workflow

```text
Start
   │
   ▼
Connect Database
   │
   ▼
Display Menu
   │
   ├── Add Student
   ├── View Students
   ├── Search Student
   ├── Update Student
   ├── Delete Student
   └── Exit
   │
   ▼
Perform Database Operation
   │
   ▼
Display Result
   │
   ▼
Exit
```

---

# Sample Menu

```text
====== Student Management ======

1. Add Student
2. View Students
3. Search Student
4. Update Student
5. Delete Student
6. Exit

Enter your choice:
```

---

# Sample Output

```text
Student Added Successfully.

------------------------------

ID : 101

Name : Rahul

Course : Java

Marks : 90
```

---

# Features Used

During this project, you will use:

- JDBC Connection
- PreparedStatement
- ResultSet
- CRUD Operations
- Transactions
- Exception Handling
- Connection Pooling
- DAO Pattern

---

# Possible Enhancements

You can extend the project by adding:

- Search by course
- Pagination
- Student attendance
- Login system
- Marks report
- Export to CSV
- Logging
- REST API using Spring Boot

---

# Common Mistakes

### Using Statement

Always use:

```java
PreparedStatement
```

---

### Forgetting to Close Resources

Use:

```java
try-with-resources
```

---

### No Input Validation

Validate:

- Student ID
- Marks
- Name
- Course

before saving data.

---

### Mixing UI and Database Code

Keep responsibilities separate:

- UI → Main
- Business Logic → Service
- Database Logic → DAO

---

# Best Practices

- Use the DAO pattern.
- Prefer `PreparedStatement`.
- Use Connection Pooling (HikariCP).
- Validate all user input.
- Handle exceptions gracefully.
- Keep SQL queries inside DAO classes.
- Use transactions for multiple related operations.
- Organise the project into separate packages.

---

# Project Challenges

Try implementing the following:

### Beginner

- Add Student
- View Students
- Search by ID

### Intermediate

- Update Student
- Delete Student
- Input validation

### Advanced

- Connection Pooling
- Batch insert
- Transaction management
- Logging
- Search by course

---

# Summary

Congratulations! 🎉

You have completed the **JDBC Module**.

You now understand:

- JDBC Architecture
- Database Connectivity
- CRUD Operations
- PreparedStatement
- CallableStatement
- ResultSet
- Transactions
- Batch Processing
- Exception Handling
- Connection Pooling
- DAO Pattern
- JDBC Best Practices

You are now ready to build database-driven Java applications and move on to **Maven & Gradle**.

---

# Module Revision

✔ JDBC Basics

✔ Database Connections

✔ CRUD Operations

✔ ResultSet

✔ Transactions

✔ Batch Processing

✔ Exception Handling

✔ Connection Pooling

✔ Best Practices

✔ Mini Project

---

# Final Practice Questions

### Basic

1. What is JDBC?
2. What is a JDBC Driver?
3. Why is `PreparedStatement` preferred?
4. What is a transaction?
5. What is Connection Pooling?

### Intermediate

6. Explain the DAO Pattern.
7. How does Batch Processing improve performance?
8. Why should try-with-resources be used?

### Interview Questions

1. Design a Student Management System using JDBC.
2. How would you structure a production-ready JDBC application?
3. Explain the complete lifecycle of a JDBC request.
4. How would you optimise the performance of a JDBC application?
5. What improvements would you make before deploying this application to production?

---

# Hands-on Exercise

Build a complete **Student Management System** that:

1. Create the `student_db` database and `students` table.
2. Configure HikariCP for connection pooling.
3. Implement the DAO pattern.
4. Perform all CRUD operations using `PreparedStatement`.
5. Use transactions for update and delete operations where appropriate.
6. Handle all exceptions using try-with-resources.
7. Validate user input before saving records.
8. Test the application and organise the code into packages following industry best practices.
