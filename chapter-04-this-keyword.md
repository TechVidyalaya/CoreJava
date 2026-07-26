# Chapter 04: The `this` Keyword

## 📖 Overview

The `this` keyword is a reference to the **current object**. It is commonly used to distinguish instance variables from local variables, invoke another constructor, pass the current object, and return the current object.

Understanding `this` is essential for writing clean and maintainable Java code.

---

# 🎯 Learning Objectives

After completing this chapter, you will be able to:

- Understand the `this` keyword
- Differentiate instance and local variables
- Use `this` to access current object members
- Call another constructor using `this()`
- Pass and return the current object

---

# What is `this`?

`this` is a reference variable that points to the **current object**.

Whenever an object calls a method or constructor, Java automatically passes the reference of that object using `this`.

---

# Why Do We Need `this`?

Consider the following example:

```java
class Student {

    String name;

    Student(String name) {

        name = name;
    }
}
```

Here, both variables are named `name`.

The parameter hides the instance variable.

As a result, the instance variable remains unchanged.

---

# Using `this`

```java
class Student {

    String name;

    Student(String name) {

        this.name = name;
    }
}
```

Here,

- `this.name` → Instance variable
- `name` → Constructor parameter

---

# Example

```java
class Student {

    String name;
    int age;

    Student(String name, int age) {

        this.name = name;
        this.age = age;
    }

    void display() {
        System.out.println(name + " " + age);
    }
}
```

```java
Student s = new Student("Rahul", 22);

s.display();
```

### Output

```
Rahul 22
```

---

# Accessing Current Object

```java
class Employee {

    String name = "John";

    void show() {

        System.out.println(this.name);
    }
}
```

### Output

```
John
```

---

# Calling Current Class Method

```java
class Student {

    void study() {
        System.out.println("Studying");
    }

    void start() {

        this.study();
    }
}
```

Using `this` here is optional.

---

# Calling Another Constructor

A constructor can invoke another constructor using `this()`.

```java
class Student {

    Student() {

        this("Rahul");
    }

    Student(String name) {

        System.out.println(name);
    }
}
```

### Output

```
Rahul
```

> `this()` must always be the first statement inside a constructor.

---

# Constructor Chaining

```java
class Employee {

    Employee() {

        this(101);
    }

    Employee(int id) {

        System.out.println(id);
    }
}
```

### Output

```
101
```

---

# Passing Current Object

The current object can be passed as a method argument.

```java
class Student {

    void display(Student s) {

        System.out.println("Object Received");
    }

    void show() {

        display(this);
    }
}
```

---

# Returning Current Object

A method can return the current object.

```java
class Student {

    Student getObject() {

        return this;
    }
}
```

This technique is commonly used in **method chaining**.

---

# Method Chaining Example

```java
class Student {

    Student study() {

        System.out.println("Studying");
        return this;
    }

    Student sleep() {

        System.out.println("Sleeping");
        return this;
    }
}
```

```java
Student s = new Student();

s.study().sleep();
```

### Output

```
Studying
Sleeping
```

---

# Memory Representation

```
Student s = new Student("Rahul");
```

```
Stack

s
 │
 ▼

Heap

--------------------
name = Rahul
--------------------

Inside Constructor

this
 │
 ▼
Same Object
```

Both `s` and `this` refer to the same object.

---

# Common Mistakes

### Forgetting `this`

```java
Student(String name) {

    name = name;
}
```

The instance variable is never updated.

---

### Incorrect Constructor Call

```java
Student() {

    System.out.println("Hello");

    this("Rahul");
}
```

This is invalid because `this()` is not the first statement.

---

### Infinite Constructor Loop

```java
Student() {

    this();
}
```

This causes infinite recursion and results in a compilation error.

---

# Best Practices

- Use `this` when instance variables and parameters have the same name.
- Use `this()` for constructor chaining.
- Avoid unnecessary use of `this` where there is no ambiguity.
- Keep constructor chains simple and readable.

---

# Summary

In this chapter, you learned:

- Meaning of the `this` keyword
- Accessing current object variables
- Calling current methods
- Constructor chaining using `this()`
- Passing the current object
- Returning the current object

---

# Quick Revision

- `this` refers to the current object.
- `this.variable` accesses instance variables.
- `this.method()` calls another method.
- `this()` calls another constructor.
- `this()` must be the first statement in a constructor.
- `this` can be passed or returned like any other object reference.

---

# Practice Questions

### Basic

1. What does the `this` keyword represent?
2. Why is `this` used in constructors?
3. What is constructor chaining?
4. Can `this` be returned from a method?
5. Can `this` be passed as a method argument?

### Intermediate

6. Explain the difference between `this` and `this()`.
7. Why must `this()` be the first statement in a constructor?
8. How does method chaining work?

### Interview Questions

1. What is the purpose of the `this` keyword?
2. Can `this` be used inside a static method? Why?
3. What happens if `this()` creates a recursive constructor call?
4. Explain constructor chaining with an example.
5. What is the difference between `this` and `super`?

---

# Hands-on Exercise

Create a class named **Book** with:

**Variables**

- title
- author
- price

Requirements:

1. Use a parameterized constructor with the `this` keyword.
2. Create a default constructor that calls the parameterized constructor using `this()`.
3. Create a `display()` method to print all details.
4. Create two `Book` objects and display their information.
5. 
