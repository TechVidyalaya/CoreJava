# Chapter 03: Constructors

## 📖 Overview

A **constructor** is a special method used to initialize an object. It is automatically called whenever an object is created using the `new` keyword.

Constructors help us assign initial values to object variables, making object creation easier and more organised.

---

# 🎯 Learning Objectives

After completing this chapter, you will be able to:

- Understand constructors
- Create default and parameterized constructors
- Differentiate constructors and methods
- Use constructor overloading
- Understand the `this()` constructor call

---

# What is a Constructor?

A constructor is a special member of a class that:

- Has the same name as the class
- Has no return type
- Executes automatically when an object is created

### Syntax

```java
class Student {

    Student() {
        System.out.println("Constructor Called");
    }
}
```

---

# Creating an Object

```java
class Student {

    Student() {
        System.out.println("Object Created");
    }
}

public class Main {

    public static void main(String[] args) {

        Student s1 = new Student();
    }
}
```

### Output

```
Object Created
```

---

# Why Do We Need Constructors?

Without constructors:

```java
Student s = new Student();

s.name = "Rahul";
s.age = 22;
```

Using constructors:

```java
Student s = new Student("Rahul", 22);
```

This makes code cleaner and reduces mistakes.

---

# Default Constructor

A constructor with **no parameters** is called a default (no-argument) constructor.

```java
class Student {

    Student() {
        System.out.println("Default Constructor");
    }
}
```

---

# Java's Default Constructor

If you do not create any constructor, Java automatically provides one.

```java
class Student {

}
```

Equivalent to:

```java
class Student {

    Student() {

    }
}
```

> Once you create any constructor, Java no longer provides the default constructor automatically.

---

# Parameterized Constructor

A constructor that accepts parameters.

```java
class Student {

    String name;
    int age;

    Student(String n, int a) {

        name = n;
        age = a;
    }
}
```

Creating objects:

```java
Student s1 = new Student("Rahul", 22);
Student s2 = new Student("Amit", 20);
```

---

# Displaying Object Data

```java
class Student {

    String name;
    int age;

    Student(String n, int a) {
        name = n;
        age = a;
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

# Constructor Overloading

A class can have multiple constructors with different parameter lists.

```java
class Student {

    Student() {
        System.out.println("Default");
    }

    Student(String name) {
        System.out.println(name);
    }

    Student(String name, int age) {
        System.out.println(name + " " + age);
    }
}
```

---

# Using `this` Keyword

Sometimes parameter names are the same as instance variables.

```java
class Student {

    String name;
    int age;

    Student(String name, int age) {

        this.name = name;
        this.age = age;
    }
}
```

`this` refers to the current object.

---

# Constructor Chaining

One constructor can call another constructor using `this()`.

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

# Constructor vs Method

| Constructor | Method |
|-------------|--------|
| Initializes objects | Performs actions |
| Same name as class | Any valid name |
| No return type | Has a return type or `void` |
| Called automatically | Called explicitly |
| Executes during object creation | Executes when invoked |

---

# Real-World Example

```java
class Car {

    String brand;
    String colour;

    Car(String brand, String colour) {

        this.brand = brand;
        this.colour = colour;
    }

    void display() {
        System.out.println(brand + " " + colour);
    }
}
```

```java
Car car = new Car("Toyota", "White");

car.display();
```

### Output

```
Toyota White
```

---

# Common Mistakes

### Constructor with Return Type

❌ Incorrect

```java
void Student() {

}
```

This is a method, not a constructor.

---

### Constructor Name Doesn't Match Class

❌ Incorrect

```java
class Student {

    Person() {

    }
}
```

The constructor name must exactly match the class name.

---

### Forgetting `new`

```java
Student s;

s = new Student();
```

Objects must be created using the `new` keyword.

---

# Best Practices

- Use constructors to initialise objects.
- Keep constructors simple.
- Use parameterized constructors for mandatory data.
- Use constructor overloading when needed.
- Use `this` to avoid variable name conflicts.

---

# Summary

In this chapter, you learned:

- What a constructor is
- Default constructors
- Parameterized constructors
- Constructor overloading
- Constructor chaining
- `this` keyword
- Difference between constructors and methods

---

# Quick Revision

- Constructor name must match the class name.
- Constructors have no return type.
- Constructors are called automatically.
- Constructors initialise objects.
- `this()` calls another constructor.
- `this` refers to the current object.

---

# Practice Questions

### Basic

1. What is a constructor?
2. When is a constructor called?
3. Can a constructor have a return type?
4. What is a default constructor?
5. What is a parameterized constructor?

### Intermediate

6. Explain constructor overloading.
7. What is constructor chaining?
8. Why is the `this` keyword used?

### Interview Questions

1. Can constructors be inherited?
2. Can constructors be overridden?
3. What happens if no constructor is written?
4. What is the difference between a constructor and a method?
5. Why is `this()` required to be the first statement?

---

# Hands-on Exercise

Create a class named **Employee** with:

**Variables**

- id
- name
- salary

Create:

1. A default constructor
2. A parameterized constructor
3. A `display()` method

Create three Employee objects using different constructors and display their details.
