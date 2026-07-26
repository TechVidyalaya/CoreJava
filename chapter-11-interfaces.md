# Chapter 11: Interfaces

## 📖 Overview

An **Interface** is a blueprint of a class that defines a set of behaviours without providing their implementation (except `default` and `static` methods).

Interfaces are used to achieve:

- Abstraction
- Multiple inheritance
- Loose coupling
- Standardised design

In modern Java, interfaces are one of the most important features used in frameworks like **Spring Boot**, **Hibernate**, and **Java Collections**.

---

# 🎯 Learning Objectives

After completing this chapter, you will be able to:

- Understand interfaces
- Create and implement interfaces
- Understand default and static methods
- Implement multiple interfaces
- Differentiate interfaces and abstract classes

---

# What is an Interface?

An interface defines **what a class should do**, but not **how it should do it**.

It acts as a contract.

### Syntax

```java
interface Animal {

    void sound();
}
```

---

# Implementing an Interface

A class implements an interface using the `implements` keyword.

```java
interface Animal {

    void sound();
}

class Dog implements Animal {

    @Override
    public void sound() {
        System.out.println("Dog Barks");
    }
}
```

---

# Creating an Object

```java
public class Main {

    public static void main(String[] args) {

        Animal animal = new Dog();

        animal.sound();
    }
}
```

### Output

```
Dog Barks
```

---

# Interface Rules

- Cannot create objects directly.
- Methods are `public abstract` by default.
- Variables are `public static final`.
- A class can implement multiple interfaces.
- An interface can extend another interface.

---

# Interface Variables

```java
interface AppConfig {

    int MAX_USERS = 100;
}
```

Equivalent to:

```java
public static final int MAX_USERS = 100;
```

Constants cannot be modified.

---

# Multiple Interfaces

One class can implement multiple interfaces.

```java
interface Printable {

    void print();
}

interface Scannable {

    void scan();
}

class Printer implements Printable, Scannable {

    @Override
    public void print() {
        System.out.println("Printing...");
    }

    @Override
    public void scan() {
        System.out.println("Scanning...");
    }
}
```

---

# Why Multiple Interfaces?

Java does not support multiple inheritance using classes.

Instead, it allows multiple inheritance through interfaces.

```
        Printable

             ▲

             │

Printer ─────┼──────► Scannable
```

---

# Default Methods

Since Java 8, interfaces can have implemented methods using `default`.

```java
interface Vehicle {

    default void start() {
        System.out.println("Vehicle Started");
    }
}
```

```java
class Car implements Vehicle {

}
```

```java
Car car = new Car();

car.start();
```

### Output

```
Vehicle Started
```

---

# Static Methods

Interfaces can also contain static methods.

```java
interface MathUtility {

    static void info() {
        System.out.println("Utility Interface");
    }
}
```

Calling:

```java
MathUtility.info();
```

---

# Functional Interface

An interface containing exactly **one abstract method**.

```java
@FunctionalInterface
interface Calculator {

    int add(int a, int b);
}
```

Functional interfaces are used with:

- Lambda Expressions
- Stream API

---

# Interface vs Abstract Class

| Interface | Abstract Class |
|------------|----------------|
| Uses `implements` | Uses `extends` |
| Supports multiple inheritance | Single inheritance |
| Variables are constants | Can have instance variables |
| Methods are abstract by default | Can have abstract and concrete methods |
| No object creation | No object creation |

---

# Real-World Example

```
Payment

      ▲

      │

-------------------------
| pay()                |
-------------------------

     ▲      ▲      ▲

   UPI    Card   Wallet
```

Every payment system follows the same interface but implements it differently.

---

# Common Mistakes

### Creating Interface Object

```java
Animal a = new Animal();
```

❌ Compilation Error

---

### Forgetting `public`

```java
class Dog implements Animal {

    void sound() {

    }
}
```

❌ Compilation Error

Implemented methods must be `public`.

---

### Modifying Interface Variable

```java
AppConfig.MAX_USERS = 200;
```

❌ Compilation Error

Interface variables are constants.

---

# Best Practices

- Use interfaces for contracts.
- Prefer interfaces over abstract classes when only behaviour is required.
- Keep interfaces focused on a single responsibility.
- Use functional interfaces for lambda expressions.
- Program to interfaces, not implementations.

---

# Summary

In this chapter, you learned:

- What an interface is
- Implementing interfaces
- Multiple inheritance using interfaces
- Default methods
- Static methods
- Functional interfaces
- Interface vs abstract class

---

# Quick Revision

- Interfaces define contracts.
- Use the `implements` keyword.
- Interfaces support multiple inheritance.
- Interface methods are `public abstract` by default.
- Interface variables are `public static final`.
- Default and static methods were introduced in Java 8.

---

# Practice Questions

### Basic

1. What is an interface?
2. Which keyword is used to implement an interface?
3. Can we create an object of an interface?
4. What is a default method?
5. What is a functional interface?

### Intermediate

6. Why does Java support multiple interfaces but not multiple class inheritance?
7. Explain default methods with an example.
8. Differentiate interface variables and class variables.

### Interview Questions

1. What is the difference between an interface and an abstract class?
2. Can an interface have constructors?
3. Why are interface methods public by default?
4. What is the purpose of the `@FunctionalInterface` annotation?
5. Why do Spring Boot projects use interfaces extensively?

---

# Hands-on Exercise

Create two interfaces:

**Printable**

```java
print()
```

**Scannable**

```java
scan()
```

Create a class named **MultiFunctionPrinter** that implements both interfaces.

Requirements:

1. Implement both methods.
2. Create an object using the interface reference.
3. Call both methods.
4. Add a default method to one interface and invoke it from the object.
