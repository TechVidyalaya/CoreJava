# Chapter 07: CRUD Operations

## 📖 Overview

**CRUD** stands for **Create, Read, Update, and Delete**. These are the four basic operations performed on a database.

In JDBC, CRUD operations are typically implemented using **PreparedStatement** to ensure better performance and security.

---

# 🎯 Learning Objectives

After completing this chapter, you will be able to:

- Understand CRUD operations
- Insert records into a database
- Retrieve records
- Update existing records
- Delete records
- Build a complete JDBC CRUD application

---

# What is CRUD?

CRUD represents the basic database operations.

| Operation | SQL Command | Purpose |
|-----------|-------------|---------|
| Create | INSERT | Add new records |
| Read | SELECT | Retrieve records |
| Update | UPDATE | Modify existing records |
| Delete | DELETE | Remove records |

---

# Student Table

```sql
CREATE TABLE students (

    id INT PRIMARY KEY,

    name VARCHAR(100),

    course VARCHAR(100),

    marks INT
);
```

---

# CRUD Workflow

```text
Java Application
        │
        ▼
PreparedStatement
        │
        ▼
Execute SQL
        │
        ▼
Database
        │
        ▼
Result
```

---

# Create (INSERT)

SQL:

```sql
INSERT INTO students
VALUES (?, ?, ?, ?)
```

Java:

```java
String sql =
    "INSERT INTO students VALUES (?, ?, ?, ?)";

PreparedStatement ps =
    connection.prepareStatement(sql);

ps.setInt(1, 101);
ps.setString(2, "Rahul");
ps.setString(3, "Java");
ps.setInt(4, 90);

int rows =
    ps.executeUpdate();

System.out.println(rows);
```

Output

```text
1
```

---

# Read (SELECT)

SQL:

```sql
SELECT * FROM students
```

Java:

```java
String sql =
    "SELECT * FROM students";

PreparedStatement ps =
    connection.prepareStatement(sql);

ResultSet rs =
    ps.executeQuery();

while (rs.next()) {

    System.out.println(

        rs.getInt("id") + " "

        + rs.getString("name")

    );
}
```

---

# Search by ID

SQL:

```sql
SELECT * FROM students
WHERE id = ?
```

Java:

```java
PreparedStatement ps =
    connection.prepareStatement(
        "SELECT * FROM students WHERE id=?"
    );

ps.setInt(1, 101);

ResultSet rs =
    ps.executeQuery();
```

---

# Update

SQL:

```sql
UPDATE students

SET marks = ?

WHERE id = ?
```

Java:

```java
PreparedStatement ps =
    connection.prepareStatement(

        "UPDATE students SET marks=? WHERE id=?"
);

ps.setInt(1, 95);
ps.setInt(2, 101);

int rows =
    ps.executeUpdate();
```

---

# Delete

SQL:

```sql
DELETE FROM students

WHERE id = ?
```

Java:

```java
PreparedStatement ps =
    connection.prepareStatement(

        "DELETE FROM students WHERE id=?"
);

ps.setInt(1, 101);

int rows =
    ps.executeUpdate();
```

---

# executeQuery() vs executeUpdate()

| Method | Used For | Returns |
|---------|----------|----------|
| `executeQuery()` | SELECT | ResultSet |
| `executeUpdate()` | INSERT, UPDATE, DELETE | Number of affected rows |

---

# Complete CRUD Flow

```text
Start
   │
   ▼
Connect Database
   │
   ▼
Choose Operation
   │
   ├── Insert
   ├── Select
   ├── Update
   └── Delete
   │
   ▼
Display Result
   │
   ▼
Close Resources
```

---

# Real-World Applications

CRUD operations are used in:

- Student Management Systems
- Banking applications
- Hospital Management Systems
- Inventory systems
- E-commerce platforms
- Employee Management Systems

---

# Common Mistakes

### Forgetting to Set Parameters

Incorrect:

```java
PreparedStatement ps =
    connection.prepareStatement(sql);

ps.executeUpdate();
```

Always set all required parameters before execution.

---

### Using executeQuery() for INSERT

Incorrect:

```java
ps.executeQuery();
```

Correct:

```java
ps.executeUpdate();
```

---

### Not Checking Affected Rows

Always verify whether the operation succeeded.

```java
if (rows > 0) {

    System.out.println(
        "Operation Successful"
    );
}
```

---

# Best Practices

- Use `PreparedStatement` for all CRUD operations.
- Validate user input before executing SQL.
- Use try-with-resources.
- Check affected rows after INSERT, UPDATE, and DELETE.
- Handle SQL exceptions properly.
- Close all JDBC resources.

---

# Summary

In this chapter, you learned:

- CRUD operations
- INSERT
- SELECT
- UPDATE
- DELETE
- executeQuery()
- executeUpdate()
- Best practices

---

# Quick Revision

- CRUD = Create, Read, Update, Delete.
- `INSERT` adds records.
- `SELECT` retrieves records.
- `UPDATE` modifies records.
- `DELETE` removes records.
- `executeQuery()` returns a `ResultSet`.
- `executeUpdate()` returns affected rows.

---

# Practice Questions

### Basic

1. What does CRUD stand for?
2. Which SQL command is used to insert data?
3. Which method returns a `ResultSet`?
4. Which method returns affected rows?
5. Why is `PreparedStatement` preferred?

### Intermediate

6. Explain the CRUD workflow.
7. Differentiate `executeQuery()` and `executeUpdate()`.
8. How do you retrieve a student by ID?

### Interview Questions

1. Explain CRUD operations using JDBC.
2. Why should `PreparedStatement` be used for CRUD operations?
3. How do you check whether an UPDATE operation was successful?
4. What is the difference between SELECT and UPDATE execution in JDBC?
5. How would you design a reusable DAO class for CRUD operations?

---

# Hands-on Exercise

Create a **Student Management System** that:

1. Connect to the `student_db` database.
2. Insert multiple student records.
3. Display all students.
4. Search for a student by ID.
5. Update a student's course and marks.
6. Delete a student record.
7. Display the updated student list.
8. Handle exceptions and close all JDBC resources using try-with-resources.
