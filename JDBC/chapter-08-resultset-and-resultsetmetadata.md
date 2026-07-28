# Chapter 08: ResultSet and ResultSetMetaData

## 📖 Overview

After executing a **SELECT** query in JDBC, the returned data is stored in a **ResultSet** object. A **ResultSetMetaData** object provides information about the structure of the returned data, such as column names, data types, and the number of columns.

These interfaces are essential for reading query results dynamically.

---

# 🎯 Learning Objectives

After completing this chapter, you will be able to:

- Understand `ResultSet`
- Navigate query results
- Retrieve different data types
- Understand `ResultSetMetaData`
- Read column information dynamically
- Follow ResultSet best practices

---

# What is ResultSet?

A `ResultSet` is an object that stores the rows returned by a SQL query.

Example:

```java
PreparedStatement ps =
    connection.prepareStatement(
        "SELECT * FROM students"
    );

ResultSet rs =
    ps.executeQuery();
```

---

# ResultSet Workflow

```text
Execute SELECT Query
        │
        ▼
Create ResultSet
        │
        ▼
Read Records
        │
        ▼
Process Data
```

---

# Moving Through ResultSet

The `next()` method moves the cursor to the next row.

```java
while (rs.next()) {

    System.out.println(
        rs.getString("name")
    );
}
```

---

# Retrieving Data by Column Name

```java
while (rs.next()) {

    System.out.println(
        rs.getInt("id")
    );

    System.out.println(
        rs.getString("name")
    );

    System.out.println(
        rs.getString("course")
    );
}
```

---

# Retrieving Data by Column Index

```java
while (rs.next()) {

    System.out.println(
        rs.getInt(1)
    );

    System.out.println(
        rs.getString(2)
    );
}
```

> **Note:** Using column names improves readability and reduces errors if the column order changes.

---

# Common Getter Methods

| Method | Data Type |
|---------|-----------|
| `getInt()` | Integer |
| `getString()` | String |
| `getDouble()` | Double |
| `getBoolean()` | Boolean |
| `getDate()` | Date |
| `getLong()` | Long |

---

# Sample Output

```text
ID : 101

Name : Rahul

Course : Java

Marks : 90
```

---

# What is ResultSetMetaData?

`ResultSetMetaData` provides information about the columns in a `ResultSet`.

It helps when column details are not known at compile time.

---

# Getting ResultSetMetaData

```java
ResultSetMetaData metaData =
    rs.getMetaData();
```

---

# Number of Columns

```java
int columns =
    metaData.getColumnCount();

System.out.println(columns);
```

---

# Column Names

```java
for (int i = 1; i <= metaData.getColumnCount(); i++) {

    System.out.println(

        metaData.getColumnName(i)

    );
}
```

Output:

```text
id

name

course

marks
```

---

# Column Data Types

```java
for (int i = 1; i <= metaData.getColumnCount(); i++) {

    System.out.println(

        metaData.getColumnTypeName(i)

    );
}
```

Example Output:

```text
INT

VARCHAR

VARCHAR

INT
```

---

# Useful ResultSetMetaData Methods

| Method | Purpose |
|---------|---------|
| `getColumnCount()` | Number of columns |
| `getColumnName()` | Column name |
| `getColumnTypeName()` | SQL data type |
| `getColumnLabel()` | Column alias |
| `isNullable()` | Checks if column accepts NULL |

---

# Displaying Data Dynamically

```java
ResultSetMetaData metaData =
    rs.getMetaData();

int count =
    metaData.getColumnCount();

while (rs.next()) {

    for (int i = 1; i <= count; i++) {

        System.out.print(

            rs.getObject(i) + " "

        );
    }

    System.out.println();
}
```

This works even if the table structure changes.

---

# ResultSet Lifecycle

```text
Execute Query
      │
      ▼
ResultSet Created
      │
      ▼
Move Cursor
      │
      ▼
Read Values
      │
      ▼
Close ResultSet
```

---

# Real-World Applications

`ResultSet` and `ResultSetMetaData` are used in:

- Report generation
- Admin dashboards
- Data export tools
- Database management systems
- Dynamic table viewers
- ORM frameworks

---

# Common Mistakes

### Forgetting to Call next()

Incorrect:

```java
System.out.println(

    rs.getString("name")

);
```

Always move the cursor first.

Correct:

```java
if (rs.next()) {

    System.out.println(

        rs.getString("name")

    );
}
```

---

### Using Wrong Data Type

Incorrect:

```java
rs.getInt("name");
```

Correct:

```java
rs.getString("name");
```

---

### Using Column Index Incorrectly

Column indexes start from **1**, not **0**.

---

# Best Practices

- Prefer column names over indexes.
- Always call `next()` before reading data.
- Close `ResultSet` after use.
- Use `ResultSetMetaData` for dynamic applications.
- Use `getObject()` when column types are unknown.
- Handle SQL exceptions properly.

---

# Summary

In this chapter, you learned:

- ResultSet
- Reading query results
- Getter methods
- ResultSetMetaData
- Dynamic column processing
- Best practices

---

# Quick Revision

- `ResultSet` stores query results.
- `next()` moves to the next row.
- Use `getString()`, `getInt()`, and other getters to read values.
- `ResultSetMetaData` provides column information.
- Column indexes begin at **1**.
- Prefer column names for better readability.
- Close `ResultSet` after processing.

---

# Practice Questions

### Basic

1. What is a `ResultSet`?
2. What does the `next()` method do?
3. What is `ResultSetMetaData`?
4. Which method returns the number of columns?
5. Why should column names be preferred over indexes?

### Intermediate

6. Explain how to retrieve values from a `ResultSet`.
7. How do you read column names dynamically?
8. What is the purpose of `getObject()`?

### Interview Questions

1. Explain `ResultSet` and `ResultSetMetaData`.
2. How does the `next()` method work?
3. What is the difference between retrieving data by column name and column index?
4. When would you use `ResultSetMetaData`?
5. How would you display records from any table without knowing its structure?

---

# Hands-on Exercise

Create a **Student Report Viewer** that:

1. Retrieve all records from the `students` table.
2. Display student details using `ResultSet`.
3. Read values using both column names and column indexes.
4. Use `ResultSetMetaData` to display:
   - Number of columns
   - Column names
   - Column data types
5. Display all records dynamically using `getObject()`.
6. Handle SQL exceptions properly.
7. Close all JDBC resources using try-with-resources.
8. Test the program after adding new columns to the table and observe how the dynamic display adapts automatically.
