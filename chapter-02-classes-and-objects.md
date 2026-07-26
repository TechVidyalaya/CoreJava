# Chapter 02: Classes and Objects

## 📖 Overview

Classes and objects are the building blocks of Object-Oriented Programming (OOP). A **class** acts as a blueprint, while an **object** is a real instance created from that blueprint.

Understanding classes and objects is essential before learning constructors, inheritance, and other OOP concepts.

---

# 🎯 Learning Objectives

After completing this chapter, you will be able to:

- Understand classes and objects
- Create your own classes
- Create multiple objects
- Access object properties and methods
- Understand object references and memory basics

---

# What is a Class?

A **class** is a blueprint that defines the properties (variables) and behaviours (methods) of an object.

A class itself does not occupy memory for its variables until an object is created.

### Syntax

```java
class ClassName {

    // Variables

    // Methods

}
```

---

# Example

```java
class Student {

    String name;
    int age;

    void study() {
        System.out.println("Studying...");
    }
}
```

Here,

- `name` and `age` are instance variables.
- `study()` is an instance method.

---

# What is an Object?

An **object** is an instance of a class.

When an object is created:

- Memory is allocated.
- Variables get their own values.
- Methods can be called.

---

## Creating an Object

```java
Student s1 = new Student();
```

Breaking it down:

- `Student` → Class name
- `s1` → Reference variable
- `new` → Creates an object
- `Student()` → Calls the constructor

---

# Accessing Variables

```java
class Student {

    String name;
    int age;
}

public class Main {

    public static void main(String[] args) {

        Student s1 = new Student();

        s1.name = "Rahul";
        s1.age = 22;

        System.out.println(s1.name);
        System.out.println(s1.age);
    }
}
```

### Output

```
Rahul
22
```

---

# Calling Methods

```java
class Student {

    void study() {
        System.out.println("Student is studying");
    }
}

public class Main {

    public static void main(String[] args) {

        Student s1 = new Student();

        s1.study();
    }
}
```

### Output

```
Student is studying
```

---

# Multiple Objects

Each object has its own copy of instance variables.

```java
class Student {

    String name;
}

public class Main {

    public static void main(String[] args) {

        Student s1 = new Student();
        Student s2 = new Student();

        s1.name = "Rahul";
        s2.name = "Amit";

        System.out.println(s1.name);
        System.out.println(s2.name);
    }
}
```

### Output

```
Rahul
Amit
```

---

# Real-World Example

```java
class Car {

    String brand;
    String colour;

    void start() {
        System.out.println("Car Started");
    }
}
```

```java
Car c1 = new Car();

c1.brand = "Toyota";
c1.colour = "White";

c1.start();
```

---

# Object Reference

```java
Student s1 = new Student();
```

`s1` does not store the object itself.

It stores the **reference (memory address)** of the object.

```
s1
 │
 ▼
+----------------------+
| name = Rahul         |
| age = 22             |
+----------------------+
```

---

# Creating Multiple Objects

```java
Student s1 = new Student();
Student s2 = new Student();
Student s3 = new Student();
```

Each object has its own memory.

---

# Class vs Object

| Class | Object |
|--------|--------|
| Blueprint | Real instance |
| Logical entity | Physical entity |
| No memory for instance data | Occupies memory |
| Created once | Can have many instances |

---

# Default Values

When an object is created, Java automatically assigns default values.

| Data Type | Default Value |
|-----------|---------------|
| int | 0 |
| long | 0 |
| double | 0.0 |
| boolean | false |
| char | '\u0000' |
| String | null |
| Object | null |

Example:

```java
class Test {

    int number;
    boolean active;
    String name;
}
```

Output after object creation:

```
0
false
null
```

---

# Memory Representation

```
Student s1 = new Student();
```

```
Stack Memory

s1
 │
 ▼

Heap Memory

-----------------------
name = null
age = 0
-----------------------
```

---

# Best Practices

- Use meaningful class names (Student, Employee, BankAccount).
- Use PascalCase for class names.
- Keep one responsibility per class.
- Create separate objects for separate entities.
- Avoid public variables (learn encapsulation next).

---

# Summary

In this chapter, you learned:

- What is a class
- What is an object
- Creating objects
- Accessing variables
- Calling methods
- Multiple objects
- Object references
- Default values
- Basic memory representation

---

# Quick Revision

- Class = Blueprint
- Object = Instance of a class
- `new` creates an object
- Objects store their own data
- Multiple objects are independent
- Reference variables point to objects in heap memory

---

# Practice Questions

### Basic

1. What is a class?
2. What is an object?
3. How do you create an object?
4. What is the purpose of the `new` keyword?
5. What is a reference variable?

### Intermediate

6. Explain the difference between a class and an object.
7. What happens in memory when an object is created?
8. Why can multiple objects have different values?

### Interview Questions

1. What is the difference between an object and an object reference?
2. Where are objects stored in Java memory?
3. What are the default values of object variables?
4. Can a class exist without objects?
5. Can multiple objects be created from the same class?

---

# Hands-on Exercise

Create a class named **Employee** with the following:

**Variables**

- id
- name
- salary

**Method**

```java
displayInfo()
```

Create **three Employee objects**, assign different values to each, and display their information using the `displayInfo()` method.
