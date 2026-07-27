# Chapter 08: Mini Project – JVM Analyzer

## 📖 Overview

In this mini project, you'll build a **JVM Analyzer** application that demonstrates key Advanced Java concepts covered in this module, including Reflection, Annotations, JVM Memory Management, Garbage Collection, and Class Loaders.

This project helps reinforce theoretical concepts with practical implementation.

---

# 🎯 Learning Objectives

After completing this project, you will be able to:

- Use Reflection to inspect classes
- Create and read custom annotations
- Monitor JVM memory usage
- Observe Garbage Collection
- Explore Class Loaders
- Understand JVM behaviour in a real application

---

# Project Overview

**Project Name:** JVM Analyzer

The application will:

- Display JVM memory statistics
- Show class loading information
- Inspect classes using Reflection
- Read custom annotations
- Demonstrate object creation and Garbage Collection

---

# Project Structure

```text
JVMAnalyzer
│
├── Main.java
├── Employee.java
├── Developer.java
├── Author.java
├── ReflectionUtil.java
├── MemoryMonitor.java
├── ClassLoaderDemo.java
└── GarbageCollectionDemo.java
```

---

# Features

### 1. JVM Information

Display:

- Java Version
- JVM Name
- JVM Vendor
- Operating System
- Available Processors

Example:

```java
System.out.println(
    System.getProperty("java.version")
);

System.out.println(
    System.getProperty("java.vm.name")
);
```

---

### 2. Memory Statistics

Display:

- Total Memory
- Free Memory
- Used Memory
- Maximum Memory

Example:

```java
Runtime runtime =
    Runtime.getRuntime();

long total =
    runtime.totalMemory();

long free =
    runtime.freeMemory();

long used =
    total - free;

long max =
    runtime.maxMemory();
```

---

### 3. Reflection Demo

Inspect the `Employee` class.

Display:

- Class name
- Constructors
- Fields
- Methods

Example:

```java
Class<?> cls =
    Employee.class;
```

---

### 4. Custom Annotation

Create:

```java
@interface Author {

    String name();

}
```

Usage:

```java
@Author(name = "TechVidyalaya")
class Employee {

}
```

Read it using Reflection.

---

### 5. Class Loader Demo

Display the Class Loader for:

```java
Employee.class

String.class

ArrayList.class
```

Expected observation:

- `Employee` → Application Class Loader
- `String` → Bootstrap Class Loader (`null`)
- `ArrayList` → Bootstrap Class Loader (`null`)

---

### 6. Garbage Collection Demo

Create objects dynamically.

```java
for(int i = 0; i < 1000; i++) {

    new Employee();
}
```

Request Garbage Collection.

```java
System.gc();
```

Observe memory changes before and after execution.

---

### 7. Reflection Method Invocation

Invoke a method dynamically.

```java
Method method =
    cls.getMethod("display");

method.invoke(employee);
```

---

### 8. Private Field Access

Modify a private field.

```java
Field field =
    cls.getDeclaredField("name");

field.setAccessible(true);

field.set(employee, "Rahul");
```

Display the updated value.

---

# Sample Output

```text
===== JVM ANALYZER =====

Java Version : 21

JVM          : OpenJDK

Total Memory : 256 MB

Free Memory  : 180 MB

Used Memory  : 76 MB

Max Memory   : 2048 MB

----------------------------

Class Name : Employee

Fields

- id

- name

Methods

- display()

----------------------------

Annotation

Author : TechVidyalaya

----------------------------

Class Loader

Employee  -> AppClassLoader

String    -> Bootstrap

ArrayList -> Bootstrap

----------------------------

Garbage Collection Requested

Memory Released Successfully
```

---

# Project Workflow

```text
Start Application
        │
        ▼
Display JVM Information
        │
        ▼
Show Memory Usage
        │
        ▼
Reflection Analysis
        │
        ▼
Read Annotation
        │
        ▼
Display Class Loader
        │
        ▼
Garbage Collection Demo
        │
        ▼
Exit
```

---

# Expected Learning

After completing this project, you will understand:

- JVM memory behaviour
- Reflection in action
- Runtime annotations
- Class loading process
- Garbage Collection basics
- JVM monitoring concepts

---

# Possible Enhancements

- Export JVM statistics to a file
- Display CPU usage
- Monitor thread count
- Generate a Heap dump
- Read JVM arguments
- Display system properties
- Add a simple console menu
- Build a GUI using JavaFX or Swing

---

# Real-World Applications

The concepts used in this project are common in:

- Spring Framework
- Hibernate
- Monitoring tools
- Application servers
- IDE plugins
- Performance profilers
- Enterprise Java applications

---

# Best Practices

- Use Reflection only when necessary.
- Handle Reflection exceptions properly.
- Avoid unnecessary object creation.
- Monitor JVM memory regularly.
- Do not rely on `System.gc()` for memory management.
- Keep custom annotations meaningful and lightweight.

---

# Summary

Congratulations! 🎉

You have completed the **Advanced Java Module** and learned:

- Annotations
- Reflection API
- JVM Memory Management
- Garbage Collection
- JVM Performance Tuning
- Class Loaders
- JVM Interview Questions
- Building a JVM Analyzer project

These concepts form the foundation for understanding how Java works internally and are essential for enterprise development and technical interviews.

---

# Quick Revision

- Reflection enables runtime inspection.
- Annotations provide metadata.
- Heap stores objects; Stack stores method frames.
- Garbage Collection manages Heap memory.
- Class Loaders load classes dynamically.
- JVM tuning improves application performance.
- Monitoring tools help diagnose memory and performance issues.

---

# Practice Challenges

### Basic

1. Display all JVM system properties.
2. Print all methods of a class using Reflection.
3. Show memory usage before and after object creation.

### Intermediate

4. Create multiple custom annotations.
5. Build a utility to inspect any class passed as input.
6. Compare memory usage before and after requesting Garbage Collection.

### Advanced

7. Add a menu-driven interface to the JVM Analyzer.
8. Generate a JVM health report showing memory, class loading, and thread information.
9. Extend the application to monitor multiple classes dynamically.
10. Package the project as a runnable JAR and execute it with different JVM options (`-Xms`, `-Xmx`, and G1 GC) to compare behaviour.
