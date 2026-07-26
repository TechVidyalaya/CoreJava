# Chapter 09: Polymorphism

## 📖 Overview

**Polymorphism** is one of the four pillars of Object-Oriented Programming (OOP). The word **Polymorphism** means **"many forms."**

It allows the same method or interface to perform different actions depending on the object.

Java supports two types of polymorphism:

- Compile-Time Polymorphism (Method Overloading)
- Run-Time Polymorphism (Method Overriding)

---

# 🎯 Learning Objectives

After completing this chapter, you will be able to:

- Understand polymorphism
- Differentiate compile-time and run-time polymorphism
- Implement method overloading
- Implement method overriding
- Understand dynamic method dispatch

---

# What is Polymorphism?

Polymorphism allows one interface to have multiple implementations.

Example:

```
Payment

   │
   ├── Credit Card Payment
   ├── UPI Payment
   └── Net Banking Payment
```

The same method `pay()` performs different actions depending on the payment type.

---

# Types of Polymorphism

Java supports:

1. Compile-Time Polymorphism
2. Run-Time Polymorphism

---

# 1. Compile-Time Polymorphism

Also called **Method Overloading**.

Methods have:

- Same name
- Different parameter list

The compiler decides which method to call.

---

# Method Overloading Example

```java
class Calculator {

    int add(int a, int b) {
        return a + b;
    }

    int add(int a, int b, int c) {
        return a + b + c;
    }

    double add(double a, double b) {
        return a + b;
    }
}
```

```java
Calculator c = new Calculator();

System.out.println(c.add(5, 10));
System.out.println(c.add(5, 10, 15));
System.out.println(c.add(2.5, 3.5));
```

### Output

```
15
30
6.0
```

---

# Rules for Method Overloading

Methods must differ by:

- Number of parameters
- Type of parameters
- Order of parameters

Changing only the return type is **not allowed**.

---

# Invalid Overloading

```java
int add(int a, int b) {

}

double add(int a, int b) {

}
```

❌ Compilation Error

---

# 2. Run-Time Polymorphism

Also called **Method Overriding**.

The child class provides its own implementation of a parent method.

The JVM decides which method to execute at runtime.

---

# Method Overriding Example

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

```java
Animal a = new Dog();

a.sound();
```

### Output

```
Dog Barks
```

---

# Dynamic Method Dispatch

```java
Animal a = new Dog();
```

Reference Type:

```
Animal
```

Actual Object:

```
Dog
```

At runtime, Java executes:

```
Dog.sound()
```

This is called **Dynamic Method Dispatch**.

---

# Another Example

```java
class Shape {

    void draw() {
        System.out.println("Drawing Shape");
    }
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

```java
Shape s1 = new Circle();
Shape s2 = new Rectangle();

s1.draw();
s2.draw();
```

### Output

```
Drawing Circle
Drawing Rectangle
```

---

# Compile-Time vs Run-Time Polymorphism

| Compile-Time | Run-Time |
|--------------|----------|
| Method Overloading | Method Overriding |
| Compiler decides | JVM decides |
| Faster | Slightly slower |
| Same class | Parent and child classes |
| Based on parameters | Based on object type |

---

# Benefits of Polymorphism

- Flexible code
- Easy maintenance
- Better scalability
- Loose coupling
- Supports extensibility

---

# Real-World Example

```
Notification

     │
 ┌───┼────┐
 │   │    │
Email SMS Push
```

Each notification implements its own version of:

```java
send()
```

The application simply calls:

```java
notification.send();
```

Without worrying about the notification type.

---

# Common Mistakes

### Incorrect Overloading

```java
void display(int x) {

}

void display(int y) {

}
```

❌ Same parameter list.

---

### Incorrect Overriding

```java
class Parent {

    void show() {

    }
}

class Child extends Parent {

    int show() {

    }
}
```

❌ Return type mismatch.

---

### Missing `@Override`

Always use:

```java
@Override
```

It helps the compiler detect mistakes.

---

# Best Practices

- Use method overloading for similar operations.
- Use method overriding to customise inherited behaviour.
- Always use the `@Override` annotation.
- Program to interfaces or parent classes.
- Prefer polymorphism over long `if-else` or `switch` statements.

---

# Summary

In this chapter, you learned:

- What polymorphism is
- Compile-time polymorphism
- Run-time polymorphism
- Method overloading
- Method overriding
- Dynamic method dispatch
- Real-world applications

---

# Quick Revision

- Polymorphism means "many forms."
- Method overloading → Compile-time polymorphism.
- Method overriding → Run-time polymorphism.
- The compiler resolves overloaded methods.
- The JVM resolves overridden methods.
- Dynamic method dispatch occurs at runtime.

---

# Practice Questions

### Basic

1. What is polymorphism?
2. What are the two types of polymorphism?
3. What is method overloading?
4. What is method overriding?
5. What is dynamic method dispatch?

### Intermediate

6. Explain compile-time polymorphism with an example.
7. Explain run-time polymorphism with an example.
8. Differentiate method overloading and method overriding.

### Interview Questions

1. Can static methods be overridden?
2. Can constructors be overloaded?
3. Why can't methods be overloaded by changing only the return type?
4. What is dynamic binding?
5. Why is polymorphism important in enterprise applications?

---

# Hands-on Exercise

Create the following classes:

**Parent Class**

```text
Employee
```

Method:

```java
calculateSalary()
```

Create three child classes:

- Developer
- Tester
- Manager

Requirements:

1. Override the `calculateSalary()` method in each child class.
2. Create an array of `Employee` references.
3. Store different employee objects in the array.
4. Call `calculateSalary()` for each object using a loop.
5. Observe how Java executes the correct overridden method at runtime.
