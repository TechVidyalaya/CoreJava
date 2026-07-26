# Chapter 06: The `final` Keyword

## 📖 Overview

The `final` keyword is used to restrict modification in Java. It can be applied to **variables**, **methods**, and **classes**.

Using `final` helps write secure, reliable, and immutable code.

---

# 🎯 Learning Objectives

After completing this chapter, you will be able to:

- Understand the `final` keyword
- Create final variables
- Create final methods
- Create final classes
- Differentiate `final`, `finally`, and `finalize()`

---

# What is `final`?

The `final` keyword is used to prevent modification.

It can be applied to:

- Variables
- Methods
- Classes

---

# Final Variable

A final variable can be assigned **only once**.

```java
final int MAX_USERS = 100;
```

Trying to change it:

```java
MAX_USERS = 200;
```

❌ Compilation Error

---

# Example

```java
public class Main {

    public static void main(String[] args) {

        final double PI = 3.14159;

        System.out.println(PI);
    }
}
```

### Output

```
3.14159
```

---

# Blank Final Variable

A blank final variable can be assigned later, but only once.

```java
class Student {

    final int id;

    Student(int id) {

        this.id = id;
    }
}
```

Each object can have a different value, but once assigned, it cannot be changed.

---

# Final Reference Variable

A final object reference cannot point to another object.

```java
final Student s = new Student();
```

Valid:

```java
s.name = "Rahul";
```

Invalid:

```java
s = new Student();
```

The reference cannot change, but the object's data can.

---

# Final Method

A final method cannot be overridden by subclasses.

```java
class Animal {

    final void sound() {

        System.out.println("Animal Sound");
    }
}
```

```java
class Dog extends Animal {

    // void sound() { } ❌
}
```

---

# Final Class

A final class cannot be inherited.

```java
final class Bank {

}
```

```java
class SBI extends Bank {

}
```

❌ Compilation Error

---

# Real-World Example

The `String` class is final.

```java
String name = "Java";
```

No class can extend `String`.

This improves security and immutability.

---

# Final Keyword Summary

| Applied To | Effect |
|------------|--------|
| Variable | Value cannot change |
| Method | Cannot be overridden |
| Class | Cannot be inherited |

---

# Final vs Finally vs Finalize()

| Keyword | Purpose |
|----------|---------|
| final | Restricts modification |
| finally | Executes after try-catch |
| finalize() | Garbage collection method (deprecated) |

---

# Example of `finally`

```java
try {

    System.out.println("Inside Try");

} finally {

    System.out.println("Finally Block");
}
```

### Output

```
Inside Try
Finally Block
```

---

# Common Uses of `final`

- Constants
- Immutable objects
- Prevent method overriding
- Prevent inheritance
- Secure APIs

---

# Common Mistakes

### Changing a Final Variable

```java
final int x = 10;

x = 20;
```

❌ Compilation Error

---

### Overriding Final Method

```java
class A {

    final void show() {

    }
}

class B extends A {

    void show() {

    }
}
```

❌ Compilation Error

---

### Extending Final Class

```java
final class A {

}

class B extends A {

}
```

❌ Compilation Error

---

# Best Practices

- Use `final` for constants.
- Declare immutable fields as final.
- Use `static final` for application-wide constants.
- Mark utility classes as final when inheritance is unnecessary.
- Avoid excessive use of final unless it improves readability or design.

---

# Summary

In this chapter, you learned:

- Final variables
- Blank final variables
- Final reference variables
- Final methods
- Final classes
- Difference between `final`, `finally`, and `finalize()`

---

# Quick Revision

- Final variable → cannot be reassigned.
- Final method → cannot be overridden.
- Final class → cannot be inherited.
- `finally` is used with exception handling.
- `finalize()` is deprecated.

---

# Practice Questions

### Basic

1. What is the `final` keyword?
2. Can a final variable be modified?
3. Can a final class be inherited?
4. Can a final method be overridden?
5. What is a blank final variable?

### Intermediate

6. Explain final reference variables.
7. Differentiate final variables and constants.
8. Why is the `String` class final?

### Interview Questions

1. What is the difference between `final`, `finally`, and `finalize()`?
2. Can constructors be final?
3. Why are immutable classes often declared final?
4. Can local variables be final?
5. When should you use `static final`?

---

# Hands-on Exercise

Create a class named **BankAccount** with:

**Variables**

- `final String accountNumber`
- `String holderName`
- `double balance`

Requirements:

1. Initialise `accountNumber` using the constructor.
2. Create a `display()` method.
3. Attempt to modify `accountNumber` and observe the compilation error.
4. Create two BankAccount objects and display their details.
