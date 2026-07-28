# Chapter 06: CallableStatement

## 📖 Overview

A **CallableStatement** is a JDBC interface used to execute **Stored Procedures** in a relational database. Stored Procedures are precompiled SQL programs stored inside the database, making database operations faster, reusable, and more secure.

CallableStatement is commonly used in enterprise applications for complex business logic.

---

# 🎯 Learning Objectives

After completing this chapter, you will be able to:

- Understand `CallableStatement`
- Learn Stored Procedures
- Execute Stored Procedures using JDBC
- Pass input and output parameters
- Learn real-world use cases
- Follow best practices

---

# What is a Stored Procedure?

A **Stored Procedure** is a collection of SQL statements stored inside the database.

Benefits:

- Faster execution
- Reusable code
- Better security
- Reduced network traffic
- Centralised business logic

---

# What is CallableStatement?

`CallableStatement` is used to call Stored Procedures from Java.

Example:

```java
CallableStatement cs =
    connection.prepareCall(
        "{CALL getStudents()}"
    );
```

---

# JDBC Workflow

```text
Java Application
        │
        ▼
CallableStatement
        │
        ▼
Stored Procedure
        │
        ▼
Database
        │
        ▼
Result
```

---

# Creating a Stored Procedure

Example (MySQL):

```sql
DELIMITER //

CREATE PROCEDURE getStudents()

BEGIN

    SELECT * FROM students;

END //

DELIMITER ;
```

---

# Calling a Stored Procedure

```java
CallableStatement cs =
    connection.prepareCall(
        "{CALL getStudents()}"
    );

ResultSet rs =
    cs.executeQuery();
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

# Stored Procedure with Input Parameter

SQL:

```sql
DELIMITER //

CREATE PROCEDURE getStudentById(

    IN studentId INT

)

BEGIN

    SELECT *

    FROM students

    WHERE id = studentId;

END //

DELIMITER ;
```

Java:

```java
CallableStatement cs =
    connection.prepareCall(
        "{CALL getStudentById(?)}"
    );

cs.setInt(1, 101);

ResultSet rs =
    cs.executeQuery();
```

---

# Stored Procedure with Output Parameter

SQL:

```sql
DELIMITER //

CREATE PROCEDURE totalStudents(

    OUT total INT

)

BEGIN

    SELECT COUNT(*)

    INTO total

    FROM students;

END //

DELIMITER ;
```

Java:

```java
CallableStatement cs =
    connection.prepareCall(
        "{CALL totalStudents(?)}"
    );

cs.registerOutParameter(
    1,
    Types.INTEGER
);

cs.execute();

System.out.println(
    cs.getInt(1)
);
```

---

# Stored Procedure with Input and Output Parameters

```java
CallableStatement cs =
    connection.prepareCall(
        "{CALL calculateMarks(?, ?)}"
    );

cs.setInt(1, 101);

cs.registerOutParameter(
    2,
    Types.INTEGER
);

cs.execute();

System.out.println(
    cs.getInt(2)
);
```

---

# Important Methods

| Method | Purpose |
|---------|---------|
| `prepareCall()` | Creates a CallableStatement |
| `setInt()` | Sets integer input |
| `setString()` | Sets string input |
| `registerOutParameter()` | Registers output parameter |
| `execute()` | Executes procedure |
| `executeQuery()` | Executes SELECT procedure |
| `getInt()` | Reads integer output |
| `getString()` | Reads string output |

---

# Statement vs PreparedStatement vs CallableStatement

| Feature | Statement | PreparedStatement | CallableStatement |
|---------|-----------|-------------------|-------------------|
| Static SQL | ✅ | ❌ | ❌ |
| Parameterized Queries | ❌ | ✅ | ✅ |
| Stored Procedures | ❌ | ❌ | ✅ |
| SQL Injection Protection | ❌ | ✅ | ✅ |
| Reusable | ❌ | ✅ | ✅ |

---

# Real-World Applications

`CallableStatement` is commonly used in:

- Banking transactions
- Payroll systems
- Hospital Management Systems
- ERP applications
- Financial reporting
- Enterprise applications

---

# Common Mistakes

### Forgetting Output Parameter Registration

Incorrect:

```java
cs.execute();

cs.getInt(1);
```

Correct:

```java
cs.registerOutParameter(
    1,
    Types.INTEGER
);
```

---

### Incorrect Procedure Name

Calling a procedure that does not exist results in an SQL exception.

---

### Wrong Parameter Order

Parameters must match the Stored Procedure definition exactly.

---

# Best Practices

- Use Stored Procedures for complex business logic.
- Register output parameters before execution.
- Close `CallableStatement` after use.
- Handle SQL exceptions properly.
- Use meaningful procedure names.
- Keep business logic maintainable between Java and the database.

---

# Summary

In this chapter, you learned:

- Stored Procedures
- CallableStatement
- Input parameters
- Output parameters
- Executing procedures
- Best practices

---

# Quick Revision

- `CallableStatement` executes Stored Procedures.
- `prepareCall()` creates a `CallableStatement`.
- Use `registerOutParameter()` for output values.
- `executeQuery()` is used for procedures returning data.
- `execute()` is commonly used for procedures with output parameters.
- Stored Procedures improve reusability and performance.

---

# Practice Questions

### Basic

1. What is a Stored Procedure?
2. What is `CallableStatement`?
3. Which method creates a `CallableStatement`?
4. Why are Stored Procedures used?
5. What is an output parameter?

### Intermediate

6. Explain how to call a Stored Procedure using JDBC.
7. Differentiate input and output parameters.
8. When should `execute()` be used instead of `executeQuery()`?

### Interview Questions

1. Explain `CallableStatement` with an example.
2. Differentiate `Statement`, `PreparedStatement`, and `CallableStatement`.
3. What are the advantages of Stored Procedures?
4. How do you retrieve output parameters in JDBC?
5. When should business logic be implemented in Stored Procedures instead of Java?

---

# Hands-on Exercise

Create a **Student Stored Procedure** application that:

1. Create a `students` table.
2. Create a Stored Procedure to display all students.
3. Create another Stored Procedure to search for a student by ID.
4. Create a Stored Procedure that returns the total number of students using an output parameter.
5. Call all procedures using `CallableStatement`.
6. Display the returned records and output values.
7. Handle SQL exceptions properly.
8. Close all JDBC resources using try-with-resources.
