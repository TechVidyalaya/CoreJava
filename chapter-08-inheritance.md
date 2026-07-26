# Chapter 08: Inheritance

## 📖 Overview

**Inheritance** is one of the four pillars of Object-Oriented Programming (OOP). It allows one class to acquire the properties and behaviours of another class.

Inheritance promotes **code reusability**, **maintainability**, and helps create hierarchical relationships between classes.

---

# 🎯 Learning Objectives

After completing this chapter, you will be able to:

- Understand inheritance
- Create parent and child classes
- Use the `extends` keyword
- Understand different types of inheritance
- Use method overriding
- Understand the `super` keyword

---

# What is Inheritance?

Inheritance is the process where one class inherits the properties and methods of another class.

The existing class is called the **Parent (Superclass)**.

The new class is called the **Child (Subclass)**.

---

# Why Do We Need Inheritance?

Without inheritance:

```java
class Car {

    void start() {
        System.out.println("Car Started");
    }
}

class Bike {

    void start() {
        System.out.println("Bike Started");
    }
}
```

Common functionality must be written repeatedly.

Using inheritance:

```java
class Vehicle {

    void start() {
        System.out.println("Vehicle Started");
    }
}
```

Both Car and Bike can reuse this method.

---

# Syntax

```java
class Parent {

}

class Child extends Parent {

}
```

The `extends` keyword is used to inherit a class.

---

# Simple Example

```java
class Animal {

    void eat() {
        System.out.println("Eating...");
    }
}

class Dog extends Animal {

    void bark() {
        System.out.println("Barking...");
    }
}
```

```java
public class Main {

    public static void main(String[] args) {

        Dog d = new Dog();

        d.eat();
        d.bark();
    }
}
```

### Output

```
Eating...
Barking...
```

---

# Real-World Example

```
Vehicle
   │
   ├── Car
   ├── Bike
   └── Bus
```

All vehicles share common features like:

- Start
- Stop
- Fuel Type

Specific vehicles add their own features.

---

# Types of Inheritance

## 1. Single Inheritance

```
Animal
   │
  Dog
```

One parent and one child.

---

## 2. Multilevel Inheritance

```
Animal
   │
 Mammal
   │
  Dog
```

A child inherits from another child class.

---

## 3. Hierarchical Inheritance

```
        Animal
       /      \
     Dog      Cat
```

Multiple child classes inherit from one parent.

---

## 4. Multiple Inheritance

```
   A      B
     \   /
       C
```

Java **does not support** multiple inheritance using classes to avoid ambiguity.

Instead, Java uses **interfaces**.

---

# The `super` Keyword

`super` refers to the immediate parent class.

It is used to:

- Access parent variables
- Call parent methods
- Invoke parent constructors

---

# Calling Parent Method

```java
class Animal {

    void sound() {
        System.out.println("Animal Sound");
    }
}

class Dog extends Animal {

    void sound() {

        super.sound();

        System.out.println("Dog Barks");
    }
}
```

### Output

```
Animal Sound
Dog Barks
```

---

# Calling Parent Constructor

```java
class Animal {

    Animal() {

        System.out.println("Animal Constructor");
    }
}

class Dog extends Animal {

    Dog() {

        System.out.println("Dog Constructor");
    }
}
```

### Output

```
Animal Constructor
Dog Constructor
```

The parent constructor executes first.

---

# Method Overriding

A child class can provide its own implementation of a parent method.

```java
class Animal {

    void sound() {

        System.out.println("Animal Sound");
    }
}

class Dog extends Animal {

    @Override
    void sound() {

        System.out.println("Dog Barks");
    }
}
```

---

# IS-A Relationship

Inheritance represents an **IS-A** relationship.

Examples:

- Dog IS-A Animal
- Car IS-A Vehicle
- Manager IS-An Employee

If an IS-A relationship does not exist, inheritance should not be used.

---

# Constructor Execution Order

```
Parent Constructor

        ↓

Child Constructor
```

Parent constructors always execute before child constructors.

---

# Advantages of Inheritance

- Code reusability
- Less duplicate code
- Easier maintenance
- Extensible applications
- Supports polymorphism

---

# Common Mistakes

### Trying Multiple Inheritance

```java
class C extends A, B {

}
```

❌ Not allowed in Java.

---

### Private Members

Private members are inherited but cannot be accessed directly by child classes.

```java
private int age;
```

Use getters/setters instead.

---

### Incorrect Relationship

```
Student extends Book
```

This is not an IS-A relationship.

---

# Best Practices

- Use inheritance only for genuine IS-A relationships.
- Keep the parent class generic.
- Avoid deep inheritance hierarchies.
- Prefer composition when inheritance is not appropriate.
- Override methods only when behaviour changes.

---

# Summary

In this chapter, you learned:

- What inheritance is
- Parent and child classes
- `extends` keyword
- Types of inheritance
- Method overriding
- `super` keyword
- Constructor execution order

---

# Quick Revision

- Inheritance enables code reuse.
- Use the `extends` keyword.
- Java supports single, multilevel, and hierarchical inheritance.
- Java does not support multiple inheritance with classes.
- `super` refers to the parent class.
- Parent constructors execute before child constructors.

---

# Practice Questions

### Basic

1. What is inheritance?
2. Which keyword is used for inheritance?
3. What is a superclass?
4. What is a subclass?
5. What is the purpose of `super`?

### Intermediate

6. Explain the different types of inheritance.
7. Why doesn't Java support multiple inheritance with classes?
8. What is method overriding?

### Interview Questions

1. What is the difference between inheritance and composition?
2. Explain the IS-A relationship with examples.
3. What is the execution order of constructors in inheritance?
4. Can private members be inherited?
5. When should inheritance be avoided?

---

# Hands-on Exercise

Create the following class hierarchy:

**Parent Class: Vehicle**

Variables:

- brand
- model

Methods:

- start()
- stop()

**Child Class: Car**

Additional Variable:

- fuelType

Additional Method:

- displayDetails()

Requirements:

1. Inherit `Car` from `Vehicle`.
2. Use `super` to initialise parent variables.
3. Override the `start()` method.
4. Create a `Car` object and demonstrate inherited and overridden methods.
