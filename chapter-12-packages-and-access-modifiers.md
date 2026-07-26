# Chapter 12: Packages and Access Modifiers

## 📖 Overview

As applications grow larger, managing hundreds of classes becomes difficult. **Packages** help organise related classes, while **Access Modifiers** control the visibility of classes, variables, methods, and constructors.

These concepts are essential for building maintainable and secure Java applications.

---

# 🎯 Learning Objectives

After completing this chapter, you will be able to:

- Understand packages
- Create and use packages
- Import classes from packages
- Understand access modifiers
- Choose the appropriate access level

---

# What is a Package?

A **package** is a collection of related classes and interfaces.

Packages help:

- Organise code
- Avoid naming conflicts
- Improve maintainability
- Control access

Example:

```
com.techvidyalaya.student
```

---

# Types of Packages

## 1. Built-in Packages

Provided by Java.

Examples:

- `java.lang`
- `java.util`
- `java.io`
- `java.time`

Example:

```java
import java.util.Scanner;
```

---

## 2. User-Defined Packages

Created by developers.

Example:

```java
package com.techvidyalaya.student;
```

---

# Creating a Package

```java
package com.techvidyalaya.student;

public class Student {

    public void display() {
        System.out.println("Student Package");
    }
}
```

---

# Importing a Package

```java
import com.techvidyalaya.student.Student;

public class Main {

    public static void main(String[] args) {

        Student s = new Student();

        s.display();
    }
}
```

---

# Importing All Classes

```java
import java.util.*;
```

This imports all public classes from the `java.util` package.

---

# Fully Qualified Class Name

Instead of importing:

```java
java.util.Scanner scanner =
        new java.util.Scanner(System.in);
```

Although valid, using `import` is more readable.

---

# Package Naming Convention

Java package names are usually written in lowercase.

Example:

```
com.techvidyalaya.project

org.company.application

in.techvidyalaya.java
```

---

# Access Modifiers

Access modifiers control **who can access** classes and members.

Java provides four access modifiers:

- public
- protected
- default (package-private)
- private

---

# 1. Public

Accessible from anywhere.

```java
public class Student {

    public void display() {

        System.out.println("Public Method");
    }
}
```

---

# 2. Private

Accessible only within the same class.

```java
class Student {

    private int age;
}
```

Useful for encapsulation.

---

# 3. Protected

Accessible:

- Within the same package
- By subclasses in other packages

```java
protected void show() {

}
```

---

# 4. Default (Package-Private)

If no modifier is specified:

```java
class Student {

    void display() {

    }
}
```

Accessible only within the same package.

---

# Access Modifier Visibility

| Modifier | Same Class | Same Package | Subclass | Other Package |
|-----------|:----------:|:------------:|:--------:|:-------------:|
| public | ✅ | ✅ | ✅ | ✅ |
| protected | ✅ | ✅ | ✅ | ❌* |
| default | ✅ | ✅ | ❌ | ❌ |
| private | ✅ | ❌ | ❌ | ❌ |

> *Protected members are accessible in subclasses even if they are in different packages.

---

# Access Modifiers for Classes

Top-level classes can use only:

- `public`
- default (package-private)

Invalid:

```java
private class Student {

}
```

❌ Compilation Error

---

# Real-World Example

```
Bank Account

Private
---------
balance

Public
---------
deposit()

withdraw()

getBalance()
```

Users cannot directly modify the balance.

---

# Choosing the Right Modifier

| Situation | Modifier |
|-----------|----------|
| Accessible everywhere | public |
| Internal implementation | private |
| Shared within package | default |
| Shared with subclasses | protected |

---

# Common Mistakes

### Public Variables

```java
public double balance;
```

❌ Avoid exposing sensitive data.

Prefer:

```java
private double balance;
```

---

### Missing Import

```java
Scanner sc = new Scanner(System.in);
```

Without:

```java
import java.util.Scanner;
```

Compilation Error.

---

### Incorrect Package Name

```java
package StudentPackage;
```

Prefer lowercase:

```java
package studentpackage;
```

---

# Best Practices

- Organise related classes into packages.
- Use lowercase package names.
- Keep variables private.
- Expose only required methods.
- Avoid wildcard imports in large projects.
- Use meaningful package structures.

---

# Summary

In this chapter, you learned:

- What packages are
- Built-in and user-defined packages
- Import statements
- Fully qualified class names
- Access modifiers
- Visibility rules
- Package naming conventions

---

# Quick Revision

- Packages organise Java classes.
- `import` allows using classes from other packages.
- `public` → Accessible everywhere.
- `private` → Accessible only within the same class.
- `protected` → Accessible in the same package and subclasses.
- `default` → Accessible only within the same package.

---

# Practice Questions

### Basic

1. What is a package?
2. Why are packages used?
3. What is the purpose of the `import` statement?
4. Name the four access modifiers.
5. Which access modifier provides the highest level of security?

### Intermediate

6. Explain the difference between public and protected.
7. What is a fully qualified class name?
8. Why should package names be lowercase?

### Interview Questions

1. What is the difference between default and protected access?
2. Can a top-level class be private?
3. Why should instance variables usually be private?
4. What are the advantages of packages?
5. How do packages help avoid naming conflicts?

---

# Hands-on Exercise

Create the following package structure:

```
com.techvidyalaya.employee
```

Inside the package, create a class named **Employee** with:

- private variables:
  - id
  - name
- public getter and setter methods
- a public `display()` method

Create another class named **Main** in a different package.

Requirements:

1. Import the `Employee` class.
2. Create an Employee object.
3. Set values using setters.
4. Display the employee details.
5. Observe how the private variables are accessible only through public methods.
