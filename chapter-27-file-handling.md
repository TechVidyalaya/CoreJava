# Chapter 27: File Handling

## 📖 Overview

File Handling in Java allows applications to create, read, write, update, and delete files stored on the system. Java provides classes in the **java.io** and **java.nio.file** packages to perform file operations efficiently.

File handling is widely used for storing application data, logs, reports, configuration files, and user information.

---

# 🎯 Learning Objectives

After completing this chapter, you will be able to:

- Understand file handling in Java
- Create, read, write, and delete files
- Use `File`, `FileReader`, and `FileWriter`
- Read files efficiently using `BufferedReader`
- Use try-with-resources
- Understand basic NIO file operations

---

# What is File Handling?

File handling refers to performing operations on files stored on a computer.

Common operations include:

- Create a file
- Read data
- Write data
- Append data
- Delete a file
- Check file properties

---

# Java File Handling Packages

| Package | Purpose |
|---------|---------|
| `java.io` | Traditional file handling |
| `java.nio.file` | Modern file handling (Java 7+) |

---

# The File Class

The `File` class represents a file or directory.

```java
import java.io.File;

File file = new File("student.txt");
```

Creating a `File` object does **not** create the actual file.

---

# Creating a File

```java
import java.io.File;
import java.io.IOException;

public class Main {

    public static void main(String[] args) throws IOException {

        File file = new File("student.txt");

        if (file.createNewFile()) {
            System.out.println("File created.");
        } else {
            System.out.println("File already exists.");
        }
    }
}
```

---

# Writing to a File

Use `FileWriter`.

```java
import java.io.FileWriter;
import java.io.IOException;

FileWriter writer = new FileWriter("student.txt");

writer.write("Welcome to Java File Handling.");

writer.close();
```

---

# Appending to a File

```java
FileWriter writer = new FileWriter("student.txt", true);

writer.write("\nLearning Java IO");

writer.close();
```

The second argument `true` enables append mode.

---

# Reading a File

Use `FileReader`.

```java
import java.io.FileReader;

FileReader reader = new FileReader("student.txt");

int character;

while ((character = reader.read()) != -1) {

    System.out.print((char) character);
}

reader.close();
```

---

# Reading with BufferedReader

`BufferedReader` is faster for reading text files.

```java
import java.io.BufferedReader;
import java.io.FileReader;

BufferedReader reader =
        new BufferedReader(new FileReader("student.txt"));

String line;

while ((line = reader.readLine()) != null) {

    System.out.println(line);
}

reader.close();
```

---

# Deleting a File

```java
File file = new File("student.txt");

if (file.delete()) {

    System.out.println("File deleted.");
}
```

---

# File Information

```java
File file = new File("student.txt");

System.out.println(file.exists());
System.out.println(file.getName());
System.out.println(file.length());
System.out.println(file.canRead());
System.out.println(file.canWrite());
```

---

# try-with-resources

Automatically closes resources.

```java
try (FileWriter writer =
        new FileWriter("student.txt")) {

    writer.write("Java IO");

} catch (IOException e) {

    System.out.println(e.getMessage());
}
```

No need to call `close()` manually.

---

# NIO File Operations

Using the `Files` class.

```java
import java.nio.file.Files;
import java.nio.file.Path;

Path path = Path.of("student.txt");

Files.writeString(path, "Hello Java");
```

Reading:

```java
String content = Files.readString(path);

System.out.println(content);
```

---

# Common File Methods

| Method | Description |
|---------|-------------|
| `createNewFile()` | Creates a file |
| `exists()` | Checks existence |
| `delete()` | Deletes a file |
| `length()` | Returns file size |
| `getName()` | Returns file name |
| `canRead()` | Checks read permission |
| `canWrite()` | Checks write permission |

---

# Reader vs Writer

| Reader | Writer |
|--------|--------|
| Reads characters | Writes characters |
| `FileReader` | `FileWriter` |
| `BufferedReader` | `BufferedWriter` |

---

# Real-World Applications

File handling is commonly used for:

- Student records
- Log files
- Reports
- Configuration files
- CSV files
- Application settings

---

# Common Exceptions

| Exception | Cause |
|-----------|-------|
| `IOException` | General file error |
| `FileNotFoundException` | File not found |
| `SecurityException` | Permission denied |

---

# Common Mistakes

### Forgetting to Close Files

```java
FileWriter writer = new FileWriter("data.txt");

// Missing writer.close()
```

Prefer try-with-resources.

---

### Reading a Non-Existing File

```java
new FileReader("abc.txt");
```

Throws:

```
FileNotFoundException
```

---

### Overwriting Existing Data

```java
new FileWriter("data.txt");
```

This overwrites the file.

Use:

```java
new FileWriter("data.txt", true);
```

To append data.

---

# Best Practices

- Use try-with-resources.
- Handle `IOException` properly.
- Prefer `BufferedReader` for reading large files.
- Use `Files` API (`java.nio.file`) for modern applications.
- Check file existence before reading or deleting.

---

# Summary

In this chapter, you learned:

- File handling basics
- Creating files
- Reading and writing files
- Appending data
- Deleting files
- File information
- try-with-resources
- NIO file operations

---

# Quick Revision

- `File` represents a file or directory.
- `FileReader` reads text files.
- `FileWriter` writes text files.
- `BufferedReader` improves reading performance.
- Use append mode to preserve existing data.
- Prefer try-with-resources for automatic resource management.

---

# Practice Questions

### Basic

1. What is file handling?
2. Which package contains the `File` class?
3. What is the purpose of `FileWriter`?
4. How do you append data to a file?
5. What does `createNewFile()` do?

### Intermediate

6. Explain the difference between `FileReader` and `BufferedReader`.
7. Why should try-with-resources be used?
8. Compare `java.io` and `java.nio.file`.

### Interview Questions

1. What is the difference between `File` and `Path`?
2. Why is `BufferedReader` faster than `FileReader`?
3. What is try-with-resources?
4. How do you safely append data to a file?
5. What exceptions are commonly encountered during file handling?

---

# Hands-on Exercise

Create a **Student Record Manager** that:

1. Creates a file named `students.txt`.
2. Writes five student records to the file.
3. Appends one additional record.
4. Reads and displays all records using `BufferedReader`.
5. Displays:
   - File name
   - File size
   - Read/Write permissions
6. Delete the file after user confirmation.
