# Chapter 10: Abstraction

## 📖 Overview

**Abstraction** is one of the four pillars of Object-Oriented Programming (OOP). It focuses on **hiding implementation details** and showing only the essential features of an object.

In Java, abstraction is achieved using:

- Abstract Classes
- Interfaces

Abstraction makes applications easier to maintain, extend, and understand.

---

# 🎯 Learning Objectives

After completing this chapter, you will be able to:

- Understand abstraction
- Create abstract classes
- Create abstract methods
- Implement abstract classes
- Understand when to use abstraction

---

# What is Abstraction?

Abstraction means exposing **what an object does** while hiding **how it does it**.

### Real-World Example

A user drives a car using:

- Steering wheel
- Accelerator
- Brake

The driver doesn't need to know how the engine works internally.

This is abstraction.

---

# Why Do We Need Abstraction?

Without abstraction:

- Every class exposes internal implementation.
- Code becomes tightly coupled.
- Maintenance becomes difficult.

With abstraction:

- Only necessary functionality is visible.
- Implementation can change without affecting users.

---

# Abstract Class

An abstract class is declared using the `abstract` keyword.

An abstract class:

- Cannot be instantiated.
- Can contain abstract methods.
- Can also contain normal methods and variables.

### Syntax

```java
abstract class Animal {

}
```

---

# Abstract Method

An abstract method has **no implementation**.

```java
abstract class Animal {

    abstract void sound();
}
```

Child classes must provide the implementation.

---

# Example

```java
abstract class Animal {

    abstract void sound();
}

class Dog extends Animal {

    @Override
    void sound() {
        System.out.println("Dog Barks");
    }
}
```

```java
public class Main {

    public static void main(String[] args) {

        Dog dog = new Dog();

        dog.sound();
    }
}
```

### Output

```
Dog Barks
```

---

# Abstract Class with Normal Methods

Abstract classes can have both abstract and concrete methods.

```java
abstract class Animal {

    abstract void sound();

    void sleep() {
        System.out.println("Sleeping");
    }
}
```

```java
Dog dog = new Dog();

dog.sound();
dog.sleep();
```

### Output

```
Dog Barks
Sleeping
```

---

# Multiple Child Classes

```java
abstract class Shape {

    abstract void draw();
}

class Circle extends Shape {

    @Override
    void draw() {
        System.out.println("Drawing Circle");
    }
}

class Rectangle extends Shape {

    @Override
    void draw() {
        System.out.println("Drawing Rectangle");
    }
}
```

---

# Rules of Abstract Classes

- Cannot create objects directly.
- Can have constructors.
- Can have variables.
- Can have static methods.
- Can have final methods.
- Child classes must implement all abstract methods unless they are also abstract.

---

# Constructor in Abstract Class

```java
abstract class Animal {

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

---

# Abstract Class vs Normal Class

| Abstract Class | Normal Class |
|----------------|--------------|
| Cannot create objects | Objects can be created |
| Can contain abstract methods | Cannot contain abstract methods |
| Used as a blueprint | Used to create objects |

---

# Real-World Example

```
        Payment

           │
     ┌─────┼─────┐
     │     │     │
   UPI   Card   NetBanking
```

Every payment type implements:

```java
pay()
```

The application simply calls:

```java
payment.pay();
```

without worrying about the implementation.

---

# Common Mistakes

### Creating Object of Abstract Class

```java
Animal a = new Animal();
```

❌ Compilation Error

---

### Missing Implementation

```java
class Dog extends Animal {

}
```

❌ Compilation Error

The child class must implement all abstract methods.

---

### Forgetting `@Override`

Always use:

```java
@Override
```

for overridden methods.

---

# Best Practices

- Use abstract classes when child classes share common code.
- Keep abstract classes focused on common behaviour.
- Use meaningful abstract method names.
- Don't make every class abstract.
- Prefer abstraction to reduce code duplication.

---

# Summary

In this chapter, you learned:

- What abstraction is
- Abstract classes
- Abstract methods
- Rules of abstract classes
- Constructors in abstract classes
- Real-world use cases

---

# Quick Revision

- Abstraction hides implementation details.
- Use the `abstract` keyword.
- Abstract classes cannot be instantiated.
- Abstract methods have no body.
- Child classes must implement abstract methods.
- Abstract classes can contain both abstract and concrete methods.

---

# Practice Questions

### Basic

1. What is abstraction?
2. What is an abstract class?
3. Can an abstract class have constructors?
4. Can we create an object of an abstract class?
5. What is an abstract method?

### Intermediate

6. Why do we use abstraction?
7. Explain the difference between an abstract class and a normal class.
8. Can an abstract class have implemented methods?

### Interview Questions

1. What is the difference between abstraction and encapsulation?
2. Can an abstract class have static methods?
3. Can an abstract class have final methods?
4. Can an abstract class have constructors?
5. When should you use an abstract class instead of an interface?

---

# Hands-on Exercise

Create an abstract class named **Employee**.

**Abstract Method**

```java
calculateSalary()
```

**Concrete Method**

```java
displayCompany()
```

Create two child classes:

- Developer
- Manager

Requirements:

1. Implement `calculateSalary()` in both classes.
2. Call both the abstract and concrete methods.
3. Observe how common functionality is inherited while specific behaviour is implemented by child classes.
