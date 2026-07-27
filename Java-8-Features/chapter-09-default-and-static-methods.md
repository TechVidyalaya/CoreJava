# Chapter 09: Default and Static Methods

## 📖 Overview

Before **Java 8**, interfaces could contain only abstract methods. Java 8 introduced **Default Methods** and **Static Methods** in interfaces, allowing developers to add new functionality without breaking existing implementations.

These features greatly improved interface evolution and backward compatibility.

---

# 🎯 Learning Objectives

After completing this chapter, you will be able to:

- Understand Default Methods
- Understand Static Methods in Interfaces
- Implement Default Methods
- Resolve Default Method conflicts
- Learn best practices

---

# Why Default Methods?

Suppose an interface is already implemented by many classes.

Before Java 8:

```java
interface Vehicle {

    void start();
}
```

If we add a new method:

```java
void stop();
```

All existing classes must implement it, causing compilation errors.

Default methods solve this problem.

---

# Default Method

A default method provides an implementation inside an interface.

```java
interface Vehicle {

    void start();

    default void stop() {

        System.out.println("Vehicle Stopped");
    }
}
```

---

# Implementing Default Methods

```java
class Car implements Vehicle {

    @Override
    public void start() {

        System.out.println("Car Started");
    }
}
```

Usage:

```java
Car car = new Car();

car.start();

car.stop();
```

Output

```
Car Started
Vehicle Stopped
```

---

# Overriding Default Methods

A class can override a default method.

```java
class Bike implements Vehicle {

    @Override
    public void start() {

        System.out.println("Bike Started");
    }

    @Override
    public void stop() {

        System.out.println("Bike Stopped");
    }
}
```

Output

```
Bike Started
Bike Stopped
```

---

# Multiple Interface Conflict

If two interfaces contain the same default method, the implementing class must override it.

```java
interface A {

    default void display() {

        System.out.println("A");
    }
}

interface B {

    default void display() {

        System.out.println("B");
    }
}

class Demo implements A, B {

    @Override
    public void display() {

        System.out.println("Demo");
    }
}
```

Output

```
Demo
```

---

# Calling a Specific Default Method

You can invoke a specific interface's default method using `InterfaceName.super`.

```java
class Demo implements A, B {

    @Override
    public void display() {

        A.super.display();

        B.super.display();
    }
}
```

Output

```
A
B
```

---

# Static Methods in Interfaces

Java 8 also allows static methods inside interfaces.

```java
interface Calculator {

    static int square(int n) {

        return n * n;
    }
}
```

Usage:

```java
System.out.println(
    Calculator.square(5)
);
```

Output

```
25
```

---

# Accessing Static Methods

Static methods belong to the interface itself.

Correct:

```java
Calculator.square(10);
```

Incorrect:

```java
Calculator calculator = null;

// calculator.square(); ❌
```

Static interface methods cannot be accessed through objects.

---

# Default vs Static Methods

| Default Method | Static Method |
|---------------|---------------|
| Inherited by implementing classes | Belongs to interface |
| Can be overridden | Cannot be overridden |
| Called using object | Called using interface name |

---

# Interface Example

```java
interface Shape {

    default void draw() {

        System.out.println("Drawing Shape");
    }

    static void info() {

        System.out.println("Shape Interface");
    }
}
```

Usage:

```java
class Circle implements Shape {

}

Circle circle = new Circle();

circle.draw();

Shape.info();
```

---

# Advantages

- Backward compatibility
- Reduce utility classes
- Better code reuse
- Cleaner API evolution
- Easier framework upgrades

---

# Real-World Applications

Default and Static methods are widely used in:

- Java Collections Framework
- Stream API
- Spring Framework
- Hibernate
- Third-party libraries
- Enterprise APIs

---

# Common Mistakes

### Calling Static Method Through Object

Incorrect:

```java
Shape shape = new Circle();

shape.info();
```

Correct:

```java
Shape.info();
```

---

### Forgetting Conflict Resolution

```java
class Demo implements A, B {

}
```

Compile-time Error

Both interfaces define the same default method.

Override the method in the implementing class.

---

### Assuming Default Methods Are Mandatory

A class inherits a default method automatically unless it chooses to override it.

---

# Best Practices

- Use Default Methods only for common behaviour.
- Keep Default Methods simple.
- Use Static Methods for utility operations.
- Avoid placing complex business logic inside interfaces.
- Override Default Methods only when customization is needed.

---

# Summary

In this chapter, you learned:

- Default Methods
- Static Methods
- Interface evolution
- Conflict resolution
- Interface utility methods
- Best practices

---

# Quick Revision

- Java 8 introduced Default and Static Methods in interfaces.
- Default Methods provide method implementations.
- Static Methods belong to the interface.
- Default Methods can be overridden.
- Static Methods cannot be overridden.
- Use `InterfaceName.super` to call a specific default method.

---

# Practice Questions

### Basic

1. Why were Default Methods introduced?
2. What is a Default Method?
3. What is a Static Method in an interface?
4. Can Default Methods be overridden?
5. How do you call a Static Method in an interface?

### Intermediate

6. Explain the difference between Default and Static Methods.
7. How are conflicts between multiple Default Methods resolved?
8. What is the purpose of `InterfaceName.super`?

### Interview Questions

1. What problem do Default Methods solve?
2. Can an interface contain method implementations?
3. Explain conflict resolution for multiple Default Methods.
4. Can Static Methods in interfaces be overridden? Why?
5. Where are Default Methods commonly used in enterprise applications?

---

# Hands-on Exercise

Create a **Payment System** that:

1. Create an interface `Payment` with:
   - An abstract method `pay()`
   - A default method `printReceipt()`
   - A static method `paymentInfo()`
2. Create classes:
   - `CreditCardPayment`
   - `UPIPayment`
3. Override `pay()` in both classes.
4. Override `printReceipt()` in one class.
5. Call the default method using objects.
6. Call the static method using the interface name.
7. Create two interfaces with the same default method and resolve the conflict using `InterfaceName.super`.
