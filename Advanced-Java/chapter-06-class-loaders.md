# Chapter 06: Class Loaders

## 📖 Overview

A **Class Loader** is a JVM component responsible for loading Java classes into memory when they are required. Instead of loading all classes at startup, the JVM loads them dynamically, making Java applications more memory-efficient.

Understanding Class Loaders is important for enterprise frameworks, application servers, plugins, and interview preparation.

---

# 🎯 Learning Objectives

After completing this chapter, you will be able to:

- Understand Class Loaders
- Learn the Class Loading process
- Explore different Class Loaders
- Understand Parent Delegation Model
- Learn custom Class Loaders
- Follow best practices

---

# What is a Class Loader?

A Class Loader is responsible for:

- Loading `.class` files
- Verifying bytecode
- Linking classes
- Initialising classes

Without Class Loaders, the JVM cannot execute Java programs.

---

# Why Class Loaders?

Advantages:

- Dynamic class loading
- Efficient memory usage
- Supports modular applications
- Enables plugin architectures
- Improves security

---

# Class Loading Process

The JVM loads a class in three phases:

```text
Loading
    │
    ▼
Linking
    │
    ▼
Initialization
```

---

# Loading Phase

During loading, the JVM:

- Finds the `.class` file
- Reads bytecode
- Creates a `Class` object

Example:

```java
Class<?> cls =
    Employee.class;
```

---

# Linking Phase

Linking consists of three steps:

```text
Linking
│
├── Verification
├── Preparation
└── Resolution
```

### Verification

Checks whether the bytecode is valid.

### Preparation

Allocates memory for static variables.

### Resolution

Resolves symbolic references to actual memory references.

---

# Initialization Phase

During initialization:

- Static variables are assigned values.
- Static blocks are executed.

Example:

```java
class Employee {

    static {

        System.out.println("Class Loaded");
    }
}
```

Output

```
Class Loaded
```

---

# Types of Class Loaders

Java provides three built-in Class Loaders.

| Class Loader | Purpose |
|--------------|---------|
| Bootstrap Class Loader | Loads core Java classes |
| Platform Class Loader | Loads platform libraries |
| Application Class Loader | Loads application classes |

---

# Bootstrap Class Loader

Loads core Java classes such as:

```java
java.lang.String

java.util.List

java.lang.Object
```

It is the parent of all other Class Loaders.

---

# Platform Class Loader

Loads platform-specific libraries.

Examples:

- Java SQL
- XML Processing
- Logging APIs

---

# Application Class Loader

Loads classes from the application's classpath.

Example:

```text
src/main/java
```

Most user-defined classes are loaded by the Application Class Loader.

---

# Parent Delegation Model

Before loading a class, a Class Loader asks its parent to load it.

```text
Application Loader
        │
        ▼
Platform Loader
        │
        ▼
Bootstrap Loader
```

If the parent cannot load the class, control returns to the child loader.

---

# Checking Class Loader

```java
ClassLoader loader =
    Employee.class.getClassLoader();

System.out.println(loader);
```

Output

```
AppClassLoader
```

---

# Bootstrap Loader Example

```java
System.out.println(
    String.class.getClassLoader()
);
```

Output

```
null
```

`null` indicates that the class was loaded by the Bootstrap Class Loader.

---

# Custom Class Loader

Developers can create their own Class Loader.

```java
class MyClassLoader
    extends ClassLoader {

}
```

Custom Class Loaders are commonly used for:

- Plugin systems
- Encryption
- Dynamic modules
- Application servers

---

# Class Loading Workflow

```text
Class Requested
        │
        ▼
Application Loader
        │
        ▼
Platform Loader
        │
        ▼
Bootstrap Loader
        │
        ▼
Load Class
        │
        ▼
Verify
        │
        ▼
Link
        │
        ▼
Initialize
```

---

# Real-World Applications

Class Loaders are widely used in:

- Spring Framework
- Tomcat
- WildFly
- OSGi
- Plugin-based applications
- IDEs like Eclipse and IntelliJ IDEA

---

# Common Mistakes

### Breaking Parent Delegation

Overriding the default delegation model incorrectly can cause:

- Duplicate classes
- Class conflicts
- Security issues

---

### ClassNotFoundException

Occurs when the JVM cannot locate a required class.

Example:

```java
Class.forName(
    "com.demo.Employee"
);
```

If the class is missing, a `ClassNotFoundException` is thrown.

---

### NoClassDefFoundError

Occurs when a class was available during compilation but is missing at runtime.

---

# Best Practices

- Follow the Parent Delegation Model.
- Avoid creating custom Class Loaders unless necessary.
- Keep the classpath clean and organised.
- Handle `ClassNotFoundException` properly.
- Understand the difference between `ClassNotFoundException` and `NoClassDefFoundError`.

---

# Summary

In this chapter, you learned:

- Class Loaders
- Class loading phases
- Bootstrap, Platform, and Application Class Loaders
- Parent Delegation Model
- Custom Class Loaders
- Common loading errors
- Best practices

---

# Quick Revision

- Class Loaders load Java classes into memory.
- Loading occurs in three phases: Loading, Linking, and Initialization.
- Bootstrap Loader loads core Java classes.
- Platform Loader loads platform libraries.
- Application Loader loads application classes.
- Parent Delegation improves security and avoids duplicate loading.
- Custom Class Loaders enable dynamic loading.

---

# Practice Questions

### Basic

1. What is a Class Loader?
2. Name the three built-in Class Loaders.
3. What are the three phases of class loading?
4. Which Class Loader loads `java.lang.String`?
5. Why does `String.class.getClassLoader()` return `null`?

### Intermediate

6. Explain the Parent Delegation Model.
7. Differentiate `ClassNotFoundException` and `NoClassDefFoundError`.
8. When would you create a custom Class Loader?

### Interview Questions

1. Explain the Java Class Loading mechanism.
2. What happens during the Linking phase?
3. Why is the Parent Delegation Model important?
4. How do application servers use Class Loaders?
5. What are the advantages and risks of custom Class Loaders?

---

# Hands-on Exercise

Create a **Class Loader Explorer** application that:

1. Display the Class Loader for:
   - `String`
   - `ArrayList`
   - Your own `Employee` class
2. Print the hierarchy of Class Loaders.
3. Demonstrate class loading using `Class.forName()`.
4. Observe when static blocks are executed during class initialization.
5. Compare `ClassNotFoundException` and `NoClassDefFoundError`.
6. Create a simple custom Class Loader skeleton.
7. Explain the Parent Delegation Model using your observations.
8. Document the complete class loading lifecycle.
