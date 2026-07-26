# Chapter 01: Introduction to Object-Oriented Programming (OOP)

## 📖 Overview

Object-Oriented Programming (OOP) is a programming paradigm that organises software around **objects** instead of functions. An object represents a real-world entity with its own **data (attributes)** and **behaviour (methods)**.

Java is a **pure object-oriented language** (except primitive data types) and uses OOP concepts to create scalable, reusable, and maintainable applications.

---

## 🎯 Learning Objectives

After completing this chapter, you will be able to:

- Understand Object-Oriented Programming
- Compare Procedural Programming and OOP
- Explain the advantages of OOP
- Identify the four pillars of OOP
- Understand real-world examples of objects

---

# What is Object-Oriented Programming?

Object-Oriented Programming (OOP) is a programming style where software is built using **objects**.

An object contains:

- State (Data)
- Behaviour (Methods)

Instead of writing everything inside one program, we divide it into multiple objects that work together.

---

## Real-World Example

### Car

State

- Brand
- Model
- Colour
- Speed

Behaviour

- Start()
- Stop()
- Accelerate()
- Brake()

Here, **Car** is an object having both data and behaviour.

---

## Another Example

### Student

State

- Name
- Roll Number
- Branch
- Marks

Behaviour

- Study()
- AttendClass()
- WriteExam()
- ViewResult()

---

# Procedural Programming vs OOP

| Procedural Programming | Object-Oriented Programming |
|-------------------------|-----------------------------|
| Focuses on functions | Focuses on objects |
| Data is shared | Data is protected inside objects |
| Difficult to maintain | Easy to maintain |
| Low code reusability | High code reusability |
| Not suitable for large projects | Ideal for enterprise applications |

---

# Why OOP?

As applications grow larger, procedural programming becomes difficult to manage.

OOP helps developers by providing:

- Better code organisation
- Code reuse
- Easier maintenance
- Better security
- Scalability
- Real-world modelling

---

# Advantages of OOP

## Code Reusability

Classes can be reused in multiple applications.

Example:

A `Student` class can be used across different education systems.

---

## Easy Maintenance

Each class manages its own responsibility.

Changes in one class usually do not affect others.

---

## Better Security

Data can be hidden using **Encapsulation**.

Users cannot directly modify important variables.

---

## Modular Design

Large applications are divided into small independent classes.

Example:

- User Module
- Payment Module
- Product Module
- Order Module

---

## Scalability

New features can be added without changing existing code significantly.

---

# The Four Pillars of OOP

## 1. Encapsulation

Wrapping data and methods together inside a class.

Example:

A bank account hides its balance and allows access only through methods.

---

## 2. Inheritance

One class acquires properties of another class.

Example:

Vehicle

↓

Car

↓

ElectricCar

---

## 3. Polymorphism

One interface, multiple implementations.

Example:

`draw()` behaves differently for:

- Circle
- Rectangle
- Triangle

---

## 4. Abstraction

Showing only essential information while hiding implementation details.

Example:

You drive a car without knowing how the engine works internally.

---

# OOP in Java

Everything revolves around classes and objects.

```java
class Student {

    String name;

    void study() {
        System.out.println("Studying...");
    }
}
```

Object Creation

```java
Student s = new Student();

s.name = "Rahul";
s.study();
```

---

# Real-Life OOP Examples

| Object | Attributes | Methods |
|----------|------------|----------|
| Mobile | Brand, RAM | Call(), Message() |
| Employee | Name, Salary | Work(), AttendMeeting() |
| Laptop | Processor, RAM | Boot(), Shutdown() |
| ATM | Balance | Withdraw(), Deposit() |
| Bank Account | Account Number, Balance | Deposit(), Withdraw() |

---

# Where is OOP Used?

- Banking Systems
- E-Commerce Applications
- Hospital Management
- Airline Reservation
- Mobile Apps
- Gaming
- Enterprise Applications
- Spring Boot Projects

---

# Best Practices

- Keep one responsibility per class.
- Use meaningful class names.
- Avoid duplicate code.
- Prefer composition when appropriate.
- Follow OOP principles consistently.

---

# Summary

In this chapter, you learned:

- What Object-Oriented Programming is
- Procedural vs OOP
- Advantages of OOP
- Four pillars of OOP
- Real-world examples
- Importance of OOP in Java

---

# Quick Revision

- OOP organises software using objects.
- Objects contain data and behaviour.
- Java is primarily object-oriented.
- Four pillars:
  - Encapsulation
  - Inheritance
  - Polymorphism
  - Abstraction
- OOP improves reusability, security, scalability, and maintainability.

---

# Practice Questions

### Basic

1. What is Object-Oriented Programming?
2. What is an object?
3. What is a class?
4. Why is OOP used?
5. Give three real-world examples of objects.

### Intermediate

6. Differentiate Procedural Programming and OOP.
7. Explain the advantages of OOP.
8. Describe the four pillars of OOP with examples.

### Interview Questions

1. Why is Java called an object-oriented language?
2. Is Java 100% object-oriented? Explain.
3. What problems does OOP solve?
4. Which OOP pillar improves code reuse?
5. Which OOP pillar provides data security?

---

# Hands-on Exercise

Design the following classes by identifying their **attributes** and **methods** (no coding required):

1. Car
2. Bank Account
3. Employee
4. Book
5. Mobile Phone

Discuss how OOP helps organise these real-world entities into software.
